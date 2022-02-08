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
