# Undestanding Kubernetes Namespaces

## Introduction

> A Namespace is like a virtual cluster inside Kubernetes. Namespaces provides a mechanism for isolating groups of resources within a single cluster. We can have multiple namespaces in a single cluster and each namespace can have its own resources. These virtual spaces can be used to isolate different projects, teams and users in a single cluster.

We can request the different namespaces from the Kubernetes API server using the command:

`kubectl get namespace`{{execute}}

![namespaces](./assets/namespaces.png)

There are three Namespaces that are created when a Kubernetes cluster is deployed. These are _default_, _kube-system_ (for Kubernetes System resources) and _kube-public_ (for Public resources, although this is not commonly utilized).

- **kube-system** This namespace has the system resources needed for Kubernetes to work. We can see the pods running in this namespace by using the command:

`kubectl get pods -n kube-system`{{execute}}

- **kube-public**  This namespace is created also automatically and is readable by all users, including those not authenticated. This namespace is mainly reserved for internal use, in the case that we need to expose a service to the public. The public nature of this namespace is just a convention, not a pre-requisite. The _kube-public_ namespace has a ConfigMap that contains the bootstrap and the configuration certificate for the Cluster.

We can see the configmap in this namespace by using the command:

`kubectl get configmap -n kube-public cluster-info -o yaml`{{execute}}

- **kube-node-lease** This namespace introduces a Lease built-in API that makes it reusable for different purposes. It makes node heartbeats significantly cheaper from both scalability and performance perspective.

- **default** This is the _default_ namespace for all the resources that are created without a namespace specification. It is empty by default.

`kubectl get pods -n default`{{execute}}

These three namespaces cannot be deleted. You can try deleting them with the command:

`kubectl delete namespace kube-system default kube-public`{{execute}}
