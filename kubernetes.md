# Kubernetes

## What is Kubernetes
Kubernetes originages from Google, who has a need to orchestrate billions of containers for all their microservices.  
  * Borg and Omega are related to Kubernetes, kind of like "sharing DNA and family history"
  * Google released Kubernetes as open source software to the CNCF

## Kubernetes Architecture

### Declaritive Model and Desired State
* We give the K8s cluster a declaritive manifest file which describes its desired state
  * Description of what things *should* look like
  * Posted to API server, K8s does whatever necessary to get us to that desired state
  * If something changes or goes wrong, and the observed state drifts from desired state (e.g. a node fails), K8s will attempt to reconcile the cluster to return to desired state



### Masters
AKA control plane or head nodes, the intelligence of the cluster
* Since the masters are effectively in charge of running the cluster, having multiple masters running helps to ensure high availability
  * Stick redundant masters in **separate** failure domains/networks
  * 3 masters is the 'magic number' - generally more than 5 makes things too complicated
* Generally a best practice not to run business applications on the masters
* `kube-apiserver` is the front-end to the control plane
  * API is exposed via REST
  * Consumes YAML/JSON
* `Cluster Store` persists the cluster state and configuration
  * Based on `etcd` distributed noSQL database
  * Performance is critical; usually first thing to come under pressure
  * Have backup/recovery plans in place
* `Kube-controller-manager` is a 'controller of controllers'
* `Kube-scheduler` watches API server for new work tasks and assigns work to cluster nodes

### Nodes
3 main components: `kubelet` `container runtime` `kube proxy`
* Kubelet
  * Main kubernetes agent that runs on every node/container and registers the node with the cluster
  * Watches API server for pod work tasks, executes pods, and reports back to master
* Container Runtime
  * Usually Docker, but pluggable with other container runtime interfaces (like containerd)
  * Responsible for low-level container intelligence
* Kube-proxy
  * Network brains of the node
  * Ensures every pod gets own unique IP
  * Lightweight load balancing across all of the pods behind a service


### Pods
Pods are the most fundamental unit of work in Kubernetes
* Pods *wrap containers*; Kubernetes can only manage **pods**, not containers
* Pods are *shared execution environments* - e.g. can have multiple containers inside a single pod, but they all share a single IP. Thus, to access the *containers* need to specify the relevant *port*
  * Containers within the *same pod* may communicate via localhost
* All containers in the same pod share the same resources
  * Generally, multi-container pods **are not recommended** and reserved for special use cases
* **Service mesh** typically inject an additional container into each pod
  * This service mesh container sits inbetween the main app container and the network
  * Handles things like encrypt/decrypt traffic between network and app container, expose telemetry, and other network functions


### Services
Since pods are constantly scaling up and down, and each pod has its own unique IP address, it would be complex to manage the communication to/from individual pods in a cluster
* This is where services come in to play.  We place a `service` in front of pods, and the services provides a stable name and IP to interface and load balance with the pods behind it
  * Load balancing mechanism is handled by the label selector


### Deployments
Pods by themselves lack the ability to scale/self-heal/etc.  These features are provided by wrapping the pods with higher-level deployment objects
* Deployment controller/reconciliation loop watches API server for new deployments and implements them when requested. This is facilitated by constantly comparing the *observed state* with the *desired state*
* Replicaset controller manages the number of replicates, or duplicated pods


## Pods in Detail
* General process is take app source code -> convert to image -> store image in repository -> define in K8s manifest -> post manifest to K8s API
* Pods are part of the *core API* - referenced in .yml manifest with `version: v1`
* Post a pod manifest with command: `kubectl pply -f pod.yml`
  * Get state of pod with `kubectl get pods --watch`
  * For detailed info: `kubectl describe pods <pod_name>`
* An example of multi-container pod:
  * 'Main' app container nginx on port 80
  * 'Helper' container on port 9113, exposing the nginx logs to a prometheus helper; "in a format that prometheus likes"
* **Delete** pods with: `kubectl delete -f <pod_manifest.yml>`


## Services in Detail
* The way to expose kubernetes pods to the local network and to the outside world
* Recall that pods each have their own IP, but **this IP address is internal to the cluster**
  * This is where services come in to play
  * Service "front end" has an IP and a port that can be accessed from the internet
  * Service "back end" is a load balancer that proxies requests to the cluster nodes
* Service IP is automatically assigned by K8s and called the **clusterIP**
  * Only for use inside the cluster
* `Name` is the name of the service and gets registered with DNS
  * Every cluster gets an internal DNS service provided by CoreDNS technology
  * Every container in every pod gets the internal DNS details
* 'Back end' load balancing is facilitated by the `labels` described in manifest
* Accessing from outside the cluster facilitated by **NodePort**
  * Range of 30000-32767
  * NodePort mapped on every cluster node to point back to the service cluster IP
  * We can sit outside the cluster, and send a request to one of the nodes at the *NodePort*, and have the request routed to one of the pods behind that service
* In manifest, `type: LoadBalancer` 
  * `Port:` specifies **external** port to listen on
  * `TargetPort:` specifies **internal** port to route to cluster
  * Matches service to pods via `Selector: <label>`
* Manifest ports explained:
  * `Port: 80` - the port that the service listens on *inside the cluster*; tied to the *cluster IP*
  *  `TargetPort: 8080` - the port that the app inside the container is listening on
  * `NodePort: 31111` - the external port mapped on every cluster **node**
* `Selector:` field has to match the `Label:` field **of the pod**


## Deployments in Detail
* Where the scaling, self-healing, rolling update magic happens
* Create a deployment .yml with the desired state -> post to API -> athN and athZ -> config stored in the cluster store -> pods get scheduled to nodes in the cluster
  * In the background, `replicaset` controller watches to make sure there is always n-replicas of the right spec running
* `Replicas:` in deployment manifest controls how many pods are created/managed
* Just like pod and services: `kubectl apply -f deployment.yml`


## Storage in Kubernetes

#### Decoupling Application & Data Lifecycles
* Normally, data only persists in containers between starts and stops
  * When container fails, or is deleted, the data is destroyed as well
* For stateful apps, like a customer order system, need to keep this data alive
  * This is accomplished by decoupling the data from the app
  * Like pods, `volumes` are created as their own objects. Volumes can get mounted to containers and remain independent of container lifecycle

#### `Persistent Volume` Subsystem
* We have some external storage that *is not* part of K8s cluster; we need some way to make this storage accessible by our pods/cluster
* Map this external volume to the kubernetes `persistent volume` (pv) object
  * Once we've done this mapping, it is available to kubernetes
  * "Claimed" with `persistent volume claim` (pvc) k8s API object
  * Pods need to reference this pvc in its manifest .yml
  * Once a pod makes a claim and the pv is bound, **no other pod can claim it** 
    * But *all* containers within the pod may access the persistent volume

#### Static Provisioning
* Drawback - does not scale well
* Example: suppose you have a 50G volume storage in AWS/Google/Azure/On-prem/etc. The `PersistentVolume` manifest .yml would look like this:
```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-pv
spec:
  accessModes:
  - ReadWriteOnce
  storageClassName: my-fast
  capacity:
    storage: 50Gi
  persistentVolumeReclaimPolicy: Retain
  gcePersistentDisk:
    pdName: my-vol
```

#### Dynamic Provisioning
* About making volume creation dynamic, and making different classes/tiers of volumes
* Of kind `StorageClass` : 
```
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: ps-gcp-fast
  annotations:
    storageclass.kubernetes.io/id-default-class: "true"
provisioner: kubernetes.io/gce-pd
volumeBindingMode: WaitForFirstConsumer
parameters:
  type: pd-ssd
  replication-type: none
```

## Multi-Container Pods
### Pod theory
* Pods are smallest unit of execution
* Pods wrap a container, adding augmented features like probes, affinities, restart policies, termination control....
* Two containers within the same pod share the same resources, like memory, storage, network interface..
  * Allows for communication over localhost, or mechanisms like IPC

#### Init Pattern
* When you need to configure an environment before an application is ready to start
  * Cloning a git repo, waiting for an API to be up and responding, etc
* K8s gaurantees an init container to start *before* the app container, and that it will only run once
* In the `spec:` portion of manifest, use `initContainers:` instead of `containers:`
* If more than one `initContainer`, they will always run sequentially, never in parallel


#### Sidecar Pattern
* Starts alongside app container and runs concurrently
* One use-case is if you want to continuously pull git repo, instead of just during initialization

#### Adapter Pattern
* A type of sidecar container
* Common to use Prometheus as a monitoring tool
  * Create helper container to format application logs in the format Prometheus desires
* Since both containers within the pod share localhost, adapter container can scrape main app endpoint on localhost, transform output to format prometheus needs, and expose those logs on a different endpoint in localhost


#### Ambassador Pattern
