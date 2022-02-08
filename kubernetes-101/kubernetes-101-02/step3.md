# Creating resources in a namespace

First, we need to create a namespace called **development**:

 `kubectl create namespace development`{{execute}}

and check that it has been created:

`kubectl get namespaces`{{execute}}

In our example, we are going to create a pod in the **development** namespace.

<pre class="file" data-target="clipboard">
---
apiVersion: v1
kind: Pod
metadata:
  name: hello-world
  namespace: development
spec:
  containers:
  - name: hello-world
    image: busybox
    command:
    - sleep
    - "3600"
    imagePullPolicy: IfNotPresent
</pre>

`kubectl create -f kubernetes/labs/02-namespaces/lab2/pod.yaml`{{execute}}

We can check how the Pod is running in the namespace by running the command:

`kubectl get pods -n development`{{execute}}

`kubectl describe pods hello-world -n development`{{execute}}
