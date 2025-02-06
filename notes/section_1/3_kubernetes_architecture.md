# Kubernetes Architecture (Control Plane and Worker Nodes)

## Node Processes

### Worker Machine in K8s Cluster

- Each Node has multiple Pods on it
- 3 processes must be installed on every Node
- Worker Nodes to the actual work

3 Node processes

- Kubelet
- Kube Proxy
- Container Runtime (containerd, docker, Crio)

### Control Plane Processes

- **4 processes** run on every control plane node

1) **kube-apiserver (API Server)**

- Acts as the front door to the Kubernetes cluster.
- Exposes the Kubernetes API, allowing communication between users, cluster components, and external systems.
- Validates and processes API requests before updating the cluster’s state in etcd.
Acts as a gatekeeper for authentication

2)**kube-scheduler (Scheduler)**:

- Responsible for assigning pods to worker nodes based on resource availability, policies, and constraints.
- Evaluates CPU, memory, affinity/anti-affinity rules, and node taints/tolerations to make optimal scheduling decisions.
- Ensures workload distribution is efficient and balanced across nodes.

3)**kube-controller-manager (Controller Manager)**

- Runs various controller loops that monitor the cluster and enforce the desired state.

- Includes controllers for nodes, endpoints, replication, deployments, and more.

- Ensures failed nodes or pods are replaced, maintaining cluster stability.

4)**etcd (Key-Value Store)**

- Serves as Kubernetes' database, storing all cluster data, including configuration and state information.

- Provides a distributed and highly available data store to maintain consistency across the cluster.
- Any cluster changes, such as deployments or scaling, are recorded in etcd.
