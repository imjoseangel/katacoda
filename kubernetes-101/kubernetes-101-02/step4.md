# Namespace limits (CPU and Memory)

In this step, we will learn how to set limits to the Pods that are allocated to a namespace. First, we create a new namespace:

`kubectl create namespace test`{{execute}}

`kubectl get namespaces`{{execute}}

Let's create a YAML file with the limits definition:

<pre class="file" data-target="clipboard">
---
apiVersion: v1
kind: LimitRange
metadata:
  name: resources
  namespace: test
spec:
  limits:
  - default:
      memory: 512Mi
      cpu: 1
    defaultRequest:
      memory: 256Mi
      cpu: 0.5
    max:
      memory: 1Gi
      cpu: 4
    min:
      memory: 128Mi
      cpu: 0.5
    type: Container
</pre>

We can apply the YAML file with the `--filename` or `-f` flag:

`kubectl apply -f kubernetes/labs/02-namespaces/lab3/limits.yaml`{{execute}}

Let's check the applied limits:

`kubectl describe namespace test`{{execute}}

```sh
Resource Limits
 Type       Resource  Min    Max  Default Request  Default Limit  Max Limit/Request Ratio
 ----       --------  ---    ---  ---------------  -------------  -----------------------
 Container  cpu       500m   4    500m             1              -
 Container  memory    128Mi  1Gi  256Mi            512Mi          -
```

To confirm that the Pods are created with the limits, we can run an NGINX pod in the namespace using the imperative command:

`kubectl run nginx --image=nginx -n test`{{execute}}

`kubectl get pods -n test`{{execute}}

We can check the CPU and memory usage of the pod:

`kubectl describe pod nginx -n test`{{execute}}

```yaml
    Limits:
      cpu:     1
      memory:  512Mi
    Requests:
      cpu:        500m
      memory:     256Mi
```
