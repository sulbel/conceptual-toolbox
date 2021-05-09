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


### Deployments
