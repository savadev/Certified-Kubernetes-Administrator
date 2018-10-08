# Core Concepts

## Cluster Architecture

At a very high level, Kubernetes has the following main components:
* One or more master nodes (API Server, Scheduler, Controller Manager)
* One or more worker nodes (Container runtime, kubelet, kube-proxy)
* Distributed key-value store, like etcd.

## API Primitives
Kubernetes is built through the definition of a set of components (building blocks or "primitives") which, when used collectively, provide a method for the deployment, maintenance, and scalability of container-based application clusters.

These "primitives" are designed to be ''loosely coupled'' (i.e., where little to no knowledge of the other component definitions is needed to use) as well as easily extensible through an API. Both the internal components of Kubernetes as well as the extensions and containers make use of this API.

The building blocks of Kubernetes are the following (note that these are also referred to as Kubernetes "Objects" or "API Primitives"):

* Cluster : A cluster is a set of machines (physical or virtual) on which your applications are managed and run. All machines are managed as a cluster (or set of clusters, depending on the topology used).

* Nodes (minions) : You can think of these as "container clients". These are the individual hosts (physical or virtual) that Docker is installed on and hosts the various containers within your managed cluster.Each node will run etcd (a key-pair management and communication service, used by Kubernetes for exchanging messages and reporting on cluster status) as well as the Kubernetes Proxy.

* Pods : A pod consists of one or more containers. Those containers are guaranteed (by the cluster controller) to be located on the same host machine (aka "co-located") in order to facilitate sharing of resources. For an example, it makes sense to have database processes and data containers as close as possible. In fact, they really should be in the same pod.
Pods "work together", as in a multi-tiered application configuration. Each set of pods that define and implement a service (e.g., MySQL or Apache) are defined by the label selector (see below).
Pods are assigned unique IPs within each cluster. These allow an application to use ports without having to worry about conflicting port utilization.
Pods can contain definitions of disk volumes or shares, and then provide access from those to all the members (containers) within the pod.
Finally, pod management is done through the API or delegated to a controller.

* Labels : Clients can attach key-value pairs to any object in the system (e.g., Pods or Nodes). These become the labels that identify them in the configuration and management of them. The key-value pairs can be used to filter, organize, and perform mass operations on a set of resources.

* Selectors : Label Selectors represent queries that are made against those labels. They resolve to the corresponding matching objects. A Selector expression matches labels to filter certain resources. For example, you may want to search for all pods that belong to a certain service, or find all containers that have a specific tier Label value as "database". Labels and Selectors are inherently two sides of the same coin. You can use Labels to classify resources and use Selectors to find them and use them for certain actions. These two items are the primary way that grouping is done in Kubernetes and determine which components that a given operation applies to when indicated.

* Controllers : These are used in the management of your cluster. Controllers are the mechanism by which your desired configuration state is enforced.
** Controllers manage a set of pods and, depending on the desired configuration state, may engage other controllers to handle replication and scaling (Replication Controller) of X number of containers and pods across the cluster. It is also responsible for replacing any container in a pod that fails (based on the desired state of the cluster).
** Replication Controllers (RC) are a subset of Controllers and are an abstraction used to manage pod lifecycles. One of the key uses of RCs is to maintain a certain number of running Pods (e.g., for scaling or ensuring that at least one Pod is running at all times, etc.). It is considered a "best practice" to use RCs to define Pod lifecycles, rather than creating Pods directly.
** Other controllers that can be engaged include a ''DaemonSet Controller'' (enforces a 1-to-1 ratio of pods to Worker Nodes) and a ''Job Controller'' (that runs pods to "completion", such as in batch jobs).
Each set of pods any controller manages, is determined by the label selectors that are part of its definition.

* Replica Sets: These define how many replicas of each Pod will be running. They also monitor and ensure the required number of Pods are running, replacing Pods that die. Replica Sets can act as replacements for Replication Controllers.

* Services : A Service is an abstraction on top of Pods, which provides a single IP address and DNS name by which the Pods can be accessed. This load balancing configuration is much easier to manage and helps scale Pods seamlessly.
Kubernetes can then provide service discovery and handle routing with the static IP for each pod as well as load balancing (round-robin based) connections to that service among the pods that match the label selector indicated.
By default, although a service is only exposed inside a cluster, it can also be exposed outside a cluster, as needed.

* Volumes : A Volume is a directory with data, which is accessible to a container. The volume co-terminates with the Pods that encloses it.

* Name : A name by which a resource is identified.

* Namespace : A Namespace provides additional qualification to a resource name. This is especially helpful when multiple teams/projects are using the same cluster and there is a potential for name collision. You can think of a Namespace as a virtual wall between multiple clusters.

* Annotations : An Annotation is a Label, but with much larger data capacity. Typically, this data is not readable by humans and is not easy to filter through. Annotation is useful only for storing data that may not be searched, but is required by the resource (e.g., storing strong keys, etc.).

* Control Pane

* API

## Network Primitives

The following rules must apply:
* A unique IP is assigned to each Pod
* Containers in a Pod can communicate to each other
* The Pod is able to communicate with other Pods in the cluster
* If configured, the application deployed inside a Pod is accessible from the external world.
