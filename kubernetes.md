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


### Pods


### Deployments
