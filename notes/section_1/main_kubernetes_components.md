# Main Kubernetes Components

## Node and Pod

![Kubernetes Pod](../../imgs/notes/section_1/Pod.png)

- **Node**: virtual or physical machine
- **Pod**: Smallest unit in Kubernetes; Abstraction over containers'
- Usually **1 Application** per Pod
- Each Pod gets its **own IP address**

## Service and Ingress

![Kubernetes Svc](../../imgs/notes/section_1/Svc.png)

- **Permanent IP address**
- Lifecycle of Pod and Service **not connected**
- **Stable Networking**: Provides a stable IP and DNS name to expose a set of pods.
- **Types**: ClusterIP (default, internal), NodePort (accessible via node IP), LoadBalancer (cloud-managed external access), and ExternalName.
- **Selector-Based Routing**: Routes traffic to pods based on labels.

![Kubernetes Ing](../../imgs/notes/section_1/Ing.png)
- **Traffic Routing**: Manages HTTP/S routing to different Services based on host/path rules.
- **TLS Termination**: Can handle SSL/TLS termination for secure connections.
- **Requires Ingress Controller**: Needs a controller (e.g., Nginx) to function.

## ConfigMap and Secret


- <b>External</b> Configuration of your application



- Used to store **secret data**
- The built-in security mechanism is not enabled by default
- Reference Secret in Deployment/Pod
- Use it as environment variables or as a properties file

## Volumes

- Storage on **local** machine
- Or **remote**, outside of the K8s cluster
- Kubernetes doesn't manage data persistence

## Deployments

- Blueprint for Pods
- For StateLESS Apps
- You create **Deployments**
- Abstraction of Pods

## StatefulSet

- For STATEFUL apps or Databases
- Examples: MySQL, Elastic, mongoDB
- Deploying not easy compared to Deployments

## DaemonSet

- Calculates how many Replicas are needed based on existing Nodes
- Deploys just 1 Replica per Node
- When **Nodes are added**, Pods are added to them
- When **Nodes are removed**, those Pods are garbage collected
- No need to define replica count
- Automatically scales up & down