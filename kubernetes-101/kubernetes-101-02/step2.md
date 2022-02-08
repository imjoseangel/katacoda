# Create/Delete namespaces

## Creating Namespaces

We can create namespaces in two ways:

- Using the imperative mode (With commands):

`kubectl create namespace development`{{execute}}

`kubectl get namespaces`{{execute}}

- Using the declarative mode (With YAML):

```yaml
---
apiVersion: v1
kind: Namespace
metadata:
  name: develop
spec:
  finalizers:
  - kubernetes
```

To run the above YAML, we need to use the `--filename` or `-f` flag:

`kubectl apply -f kubernetes/02-namespaces/lab1/development-namespace.yaml`{{execute}}

Check the namespace created by running the command:

`kubectl get namespaces`{{execute}}

## namespace information

To find the different characteristics of a namespace, we can use the command:

`kubectl describe namespace development`{{execute}}

`kubectl describe ns development`{{execute}}

We can also get the namespace definion in YAML format:

`kubectl get ns development -o yaml`{{execute}}
