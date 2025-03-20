# Kubernetes Architecture

**Kubernetes** follows a **client-server** architecture. It’s possible to have a multi-master setup (for high availability), but by default there is a single master server which acts as a controlling node.
A master and its controlled nodes(worker nodes) constitute a **“Kubernetes cluster”**.


![loading...](../../images/kubernetes_img/kubernetes-cluster-architecture.svg)


## Master Node (Control Plane) Components

### API Server

**The API server** is the entry point for all the REST commands used to control the cluster. All the administrative tasks are done by the API server within the master node.API server validates and configures the API objects such as ports, services, replication, controllers, and deployments and it is responsible for exposing APIs for every operation. We can interact with these APIs using a tool called **kubectl**.It is a command-line interface for running commands against Kubernetes clusters.

### Etcd

It is a distributed key-value lightweight database. In Kubernetes, it is a central database for storing the current cluster state at any point in time and is also used to store the configuration details such as subnets, config maps, etc. It is written in the **Go** programming language.


### Scheduler

It is responsible for tracking the utilization of the working load of each worker node and then placing the workload on which resources are available and can accept the workload.The scheduler is responsible for workload utilization and allocating the pod to the new node.

### Controller Manager

Also known as controllers. It is a daemon that runs in a non terminating loop and is responsible for collecting and sending information to the API server.Basically, the controller watches the desired state of the cluster if the current state of the cluster does not meet the desired state then the control loop takes the corrective steps to make sure that the current state is the same as that of the desired state.So in this way controllers are responsible for the overall health of the entire cluster by ensuring that nodes are up and running all the time and correct pods are running as mentioned in the specs file. 

### Cloud Controller Manager

The Cloud Controller Manager (CCM) is a Kubernetes component that helps Kubernetes work with cloud providers like AWS, Azure, or Google Cloud.

It acts as a bridge between Kubernetes and the cloud provider, managing cloud-specific tasks such as:<br>
✅ Creating Load Balancers for Services<br>
✅ Attaching Cloud Storage (Persistent Volumes)<br>
✅ Managing Cloud-based Nodes (Adding or removing virtual machines)<br>
✅ Ensuring Networking Works with the Cloud Provider

---

## Worker Node Components

### kubelet

This is the "manager" for each worker node. It ensures all containers on the node are healthy and running as they should be.If kubelet notices any issues with the pods running on the worker nodes then it tries to restart the pod on the same node. If the issue is with the worker node itself then the Kubernetes master node detects the node failure and decides to recreate the pods on the other healthy node.

### kube-proxy

It is responsible for maintaining the entire network configuration. Kube-Proxy maintains the distributed network across all the nodes, pods, and containers and exposes the services across the outside world.It acts as a network proxy and load balancer for a service on a single worker node and manages the network routing for TCP and UDP packets.

### Pod

The smallest unit in Kubernetes, a Pod is a group of one or more containers.With the help of pods, we can deploy multiple dependent containers together so it acts as a wrapper around these containers so we can interact and manage these containers primarily through pods. 

### Container Runtime Interface

**The Container Runtime Interface (CRI)** is an API specification that allows Kubernetes to communicate with container runtimes (like containerd or CRI-O). It acts as a middle layer between Kubernetes and the software responsible for running containers.

---

## Other Components 😮

### Namespace

A **namespace** in Kubernetes is like a **separate workspace** inside a cluster. It helps organize and manage multiple applications by keeping their resources isolated from each other.<br>

✅ Organizes Resources – Helps group related Pods, Services, and other Kubernetes objects.<br>
✅ Avoids Conflicts – Prevents different teams or projects from interfering with each other.<br>
✅ Controls Access – Allows setting different permissions for different namespaces.<br>
✅ Better Resource Management – Limits CPU & memory usage per namespace.

### Deployment

A Deployment in Kubernetes is like a controller that manages and updates your application automatically. It ensures your application runs as expected, even if something goes wrong.<br>

✅ Ensures High Availability – Keeps the correct number of app instances running.<br>
✅ Easy Updates – Supports rolling updates without downtime.<br>
✅ Self-Healing – Automatically restarts failed Pods.<br>
✅ Scalability – Allows you to scale up/down easily.

### Service

A Service in Kubernetes is like a stable network address for your Pods. It allows communication between different parts of your application, even if individual Pods are replaced or restarted.<br>

✅ Pods are temporary – If a Pod crashes, Kubernetes replaces it with a new one that has a different IP.<br>
✅ A Service provides a fixed IP and DNS name – So other components can always reach it.<br>
✅ Load Balancing – Distributes traffic among multiple Pods.<br>
✅ Enables External Access – Services can expose your app to the internet.



### Ingress

Ingress is like a smart entry gate for your Kubernetes cluster. It routes external HTTP/HTTPS traffic to the correct Service inside the cluster.<br>

✅ Single Entry Point – Instead of exposing multiple Services, use one entry point.<br>
✅ Domain-Based Routing – Send traffic to different apps based on URL (e.g., app.com/api vs. app.com/web).<br>
✅ Path-Based Routing – Route traffic to different services (e.g., /shop → Shop Service, /blog → Blog Service).<br>
✅ TLS/SSL Support – Secure traffic using HTTPS.<br>
✅ Load Balancing – Distribute traffic efficiently across multiple Pods.

