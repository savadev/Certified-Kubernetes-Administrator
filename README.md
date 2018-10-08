# Certified-Kubernetes-Administrator
Online resources that will help you prepare for taking the Certified Kubernetes Administrator (CKA) Certification exam.


## K8s Features
Major Kubernetes supported features are:

* __Service discovery and Load balancing__: Kubernetes gives containers their own IP addresses, groups sets of containers and refers to them via a Domain Name System (DNS). This DNS is also called a Kubernetes service. Kubernetes can discover these services automatically, and load-balance requests between containers of a given service

* __Storage orchestration__: Kubernetes automatically mount a large variety of storage systems, whether from local storage, a public cloud provider such as GCP or AWS, or a network storage system such as NFS, iSCSI, Gluster, Ceph, Cinder, or Flocker.

* __Automated rollouts and rollbacks__: Kubernetes can roll out and roll back changes of an application or its configuration, without introducing any downtime. 

* __Batch execution__: Besides long running jobs, Kubernetes also manage batch execution and CI workloads, replacing containers that fail, if desired.

* __Automatic binpacking__: Automatically places containers based on their resource requirements and other constraints, while not sacrificing availability. Mix critical and best-effort workloads in order to drive up utilization and save even more resources.

* __Self-healing__: Kubernetes automatically replaces and reschedules containers from failed nodes. It also kills and restarts the containers which do not respond to health checks, based on existing rules/policy

* __Secrets and configuration management__: Kubernetes can manage secrets and configuration details for an application without rebuilding the respective images and without exposing secrets within the stack configuration

* __Horizontal scaling__: Kubernetes can automatically scale applications based on resource usage like CPU and memory. In some cases, it also supports dynamic scaling based on customer metrics

## Tutorials
* [Kubernetes 101](https://kubernetes.io/docs/tutorials/k8s101/)
* [Kubernetes 201](https://kubernetes.io/docs/tutorials/k8s201/)

## Exam Objectives
These are the exam objectives you review and understand in order to pass the test. The objectives are current as of October, 2018.

* [CNCF Exam Curriculum repository ](https://github.com/cncf/curriculum/)


### _Core concepts_: 19%
* Understand the Kubernetes API primitives
* Understand the Kubernetes cluster architecture
* Understand Services and other network primitives

### _Networking_: 11%
* Understand the networking configuration on the cluster nodes
* Understand Pod networking concepts
* Understand service networking
* Deploy and configure network load balancer
* Know how to use Ingress rules
* Know how to configure and use the cluster DNS
* Understand CNI

### _Storage_: 7%
* Understand persistent volumes and know how to create them
* Understand access modes for volumes
* Understand persistent volume claims primitive
* Understand Kubernetes storage objects
* Know how to configure applications with persistent storage

### _Security_: 12%
* Know how to configure authentication and authorization
* Understand Kubernetes security primitives
* Know to configure network policies
* Create and manage TLS certificates for cluster components
* Work with images securely
* Define security contexts
* Secure persistent key value store
* Work with role-based access control

### _Installation, Configuration & Validation_: 12%
* Design a Kubernetes cluster
* Install Kubernetes masters and nodes, including the use of TLS bootstrapping
* Configure secure cluster communications
* Configure a Highly-Available Kubernetes cluster
* Know where to get the Kubernetes release binaries
* Provision underlying infrastructure to deploy a Kubernetes cluster
* Choose a network solution
* Choose your Kubernetes infrastructure configuration
* Run end-to-end tests on your cluster
* Analyse end-to-end tests results
* Run Node end-to-end tests

### _Application Lifecycle Management_: 8%
* Understand Deployments and how to perform rolling updates and rollbacks
* Know various ways to configure applications
* Know how to scale applications
* Understand the primitives necessary to create a self-healing application

### _Scheduling_: 5%
* Use label selectors to schedule Pods
* Understand the role of DaemonSets
* Understand how resource limits can affect Pod scheduling
* Understand how to run multiple schedulers and how to configure Pods to use them
* Manually schedule a pod without a scheduler
* Display scheduler events
* Know how to configure the Kubernetes scheduler

### _Logging/Monitoring_: 5%
* Understand how to monitor all cluster components
* Understand how to monitor applications
* Manage cluster component logs
* Manage application logs


### _Cluster Maintenance_: 11%
* Understand Kubernetes cluster upgrade process
* Facilitate operating system upgrades
* Implement backup and restore methodologies

### _Troubleshooting_: 10%
* Troubleshoot application failure
* Troubleshoot control plane failure
* Troubleshoot worker node failure
* Troubleshoot networking
