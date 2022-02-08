# Kubernetes cluster Nodes

## Nodes

> A Kubernetes Node is a unique host. It can be a physical machine or a virtual machine. The role of a Node is to run the Kubernetes Pods (the smallest, most basic deployable resources in Kubernetes) and for the communication between them. Every node, runs the **kubelet** and the **kube-proxy** components. The nodes are managed by the Control Plane host.

To see the nodes that are part of the cluster, run the command:

`kubectl get nodes`{{execute}}

This command shows the nodes that are part of the cluster to allocate our applications. Note that we have only one node available in our cluster. The status of the node is *"Ready"*. We can see other information about the node by using the flag *"-o wide"*.:

`kubectl get nodes -o wide`{{execute}}

We can also use the command *"kubectl describe node"* to see specific the information about the node. The command returns specific information about:

- Node basic information. (Operating System, processor)
- Status Information.
- Server Capacity Information.
- Node Software Information.
- Running Pods Information

`kubectl describe nodes node01`{{execute}}
