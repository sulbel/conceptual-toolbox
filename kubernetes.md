# Kubernetes

## What is Kubernetes
Kubernetes originages from Google, who has a need to orchestrate billions of containers for all their microservices.  
  * Borg and Omega are related to Kubernetes, kind of like "sharing DNA and family history"
  * Google released Kubernetes as open source software to the CNCF

## Kubernetes Architecture

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
* All containers in the same pod share the same resources
  * Generally, multi-container pods **are not recommended** and reserved for special use cases


### Services
Since pods are constantly scaling up and down, and each pod has its own unique IP address, it would be complex to manage the communication to/from individual pods in a cluster
* This is where services come in to play.  We place a `service` in front of pods, and the services provides a stable name and IP to interface and load balance with the pods behind it
  * Load balancing mechanism is handled by the label selector


### Deployments
Pods by themselves lack the ability to scale/self-heal/etc.  These features are provided by wrapping the pods with higher-level deployment objects
* Deployment controller/reconciliation loop watches API server for new deployments and implements them when requested. This is facilitated by constantly comparing the *observed state* with the *desired state*
* Replicaset controller manages the number of replicates, or duplicated pods
