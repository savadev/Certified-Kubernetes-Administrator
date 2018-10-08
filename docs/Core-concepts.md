# Core Concepts

## Cluster Architecture

At a very high level, Kubernetes has the following main components:
* One or more master nodes (API Server, Scheduler, Controller Manager)
* One or more worker nodes (Container runtime, kubelet, kube-proxy)
* Distributed key-value store, like etcd.

## API Primitives

* Pod
* Label
* Label Selector
* ReplicationController
* ReplicaSet (I/II/III)
* Deployment (I/II/III)
* Name
* Namespace
* Service
* ServiceType

## Network Primitives

The following rules must apply:
* A unique IP is assigned to each Pod
* Containers in a Pod can communicate to each other
* The Pod is able to communicate with other Pods in the cluster
* If configured, the application deployed inside a Pod is accessible from the external world.
