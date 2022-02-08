# Create/Delete namespaces

## Creating Namespaces

We can create namespaces in two ways:

- Using the imperative mode (With commands):

`kubectl create namespace development`{{execute}}

`kubectl get namespaces`{{execute}}

- Using the declarative mode (With YAML):

<pre class="file" data-target="clipboard">
---
apiVersion: v1
kind: Namespace
metadata:
  name: develop
spec:
  finalizers:
</pre>

To run the above YAML, we need to use the `--filename` or `-f` flag:

`kubectl apply -f kubernetes/labs/02-namespaces/lab1/develop-ns.yaml`{{execute}}

Check the namespace created by running the command:

`kubectl get namespaces`{{execute}}

## namespace information

To find the different characteristics of a namespace, we can use the command:

`kubectl describe namespace develop`{{execute}}

or

`kubectl describe ns develop`{{execute}}

We can also get the namespace definion in YAML format:

`kubectl get ns develop -o yaml`{{execute}}

## Removing namespaces

To delete a namespace, we can also use the imperative and the declarative commands:

- The imperative way:

`kubectl delete namespace development`{{execute}}

- The declarative way:

`kubectl delete -f kubernetes/labs/02-namespaces/lab1/develop-ns.yaml`{{execute}}

We can check that the namespaces has been successfully deleted by running the command:

`kubectl get namespaces`{{execute}}
