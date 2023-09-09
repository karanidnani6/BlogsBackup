---
title: "#Day34:Working with Services in Kubernetes"
datePublished: Fri Sep 08 2023 07:18:18 GMT+0000 (Coordinated Universal Time)
cuid: clma9mrww000208mt9j1g1we5
slug: day34working-with-services-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694155718630/4b4bc109-402b-423f-8b8e-387e27f3bee1.webp
tags: services, k8s, 90daysofdevops

---

In Kubernetes (often abbreviated as K8s), "Services" refer to an abstraction that defines a set of Pods and a policy by which to access them. Services allow you to expose your application to network traffic, both within and outside the Kubernetes cluster, while abstracting the underlying network details.

There are several types of services in Kubernetes:

1. **ClusterIP**: This is the default service type. It exposes the service on a cluster-internal IP address. It makes the service accessible only within the cluster. It's commonly used for communication between microservices inside the cluster.
    
2. **NodePort**: This service type exposes the service on a static port on each Node's IP. This means you can access the service using the Node's IP address and the NodePort. NodePort services are often used when you need to expose a service to the outside world, such as for debugging purposes or when working with legacy applications.
    
3. **LoadBalancer**: This service type provisions a cloud load balancer (if the cloud provider supports it) and assigns a stable external IP address to the service. It's typically used when you want to expose your service to the internet or need an external IP for your service.
    
4. **ExternalName**: This service type maps the service to an external DNS name. It's used for scenarios where you want to make a service in your cluster appear as if it's part of an external DNS namespace.
    
5. **Headless**: A headless service is used when you don't need load balancing or a stable cluster IP. It's often used for StatefulSets to provide DNS names for Pods without actually load balancing traffic to them.
    
6. **Ingress**: While not a service itself, Ingress resources are used to manage external access to services within the cluster. An Ingress controller handles incoming traffic and routes it to the appropriate service based on rules defined in the Ingress resource.
    

Services play a crucial role in enabling communication between microservices and managing the network exposure of applications running in a Kubernetes cluster. They abstract the complexity of networking and allow you to define how your applications should be accessed, whether it's within the cluster, from external clients, or both.

## Task-1:Create a Service for your todo-app Deployment

Step 1: Create a Service definition in a YAML file (e.g., `service.yml`): Create a YAML file, e.g., `service.yml`, and define the Service for your `todo-app` Deployment. Here's an example YAML file for a ClusterIP Service:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: todo-app-service
  namespace : todo-app
spec:
  selector:
    app: todo-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8001
```

In this example:

* [`metadata.name`](http://metadata.name) specifies the name of the Service.
    
* `spec.selector` specifies the labels used to select the Pods associated with the Service. Make sure the `app` label matches the label on your `todo-app` Pods.
    
* `spec.ports` specifies the ports for the Service, including the protocol, port number exposed by the Service, and the targetPort, which should match the port your `todo-app` Pods are listening on (in this case, 8001).
    

Step 2: Apply the Service definition to your Minikube cluster: Use the `kubectl apply` command to apply the Service definition to your Minikube cluster. Replace `<namespace-name>` with the appropriate namespace or omit it to use the default namespace.

```bash
kubectl apply -f service.yml -n <namespace-name>
```

Step 3: Verify that the Service is working: You can check the status of your Service and retrieve its ClusterIP by running:

```bash
kubectl get svc todo-app-service -n <namespace-name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694229322170/a046bee8-68fc-4810-83af-69db6a1a5b60.png align="center")

To access your `todo-app` using the Service's IP and Port within your namespace, you can either use `kubectl port-forward` or create an external Ingress resource. Here's how you can use `kubectl port-forward`:

```bash
kubectl port-forward svc/todo-app-service 8001:80 -n <namespace-name>
```

Now, you can access your `todo-app` at [`http://localhost:80`](http://localhost:8080)`01` from your local machine.

Please replace `<namespace-name>` with the appropriate namespace where your `todo-app` Deployment is located. Additionally, make sure your `todo-app` Deployment is already running before creating the Service.

## Task-2:Create a ClusterIP Service for accessing the todo-app from within the cluster

Step 1: Create a ClusterIP Service definition in a YAML file (e.g., `cluster-ip-service.yml`):

Create a YAML file, e.g., `cluster-ip-service.yml`, and define the ClusterIP Service for your `todo-app` Deployment. Here's an example YAML file:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: todo-app-clusterip-service
spec:
  selector:
    app: todo-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
```

In this example:

* [`metadata.name`](http://metadata.name) specifies the name of the ClusterIP Service.
    
* `spec.selector` specifies the labels used to select the Pods associated with the Service. Make sure the `app` label matches the label on your `todo-app` Pods.
    
* `spec.ports` specifies the ports for the ClusterIP Service, including the protocol, port number exposed by the Service, and the targetPort, which should match the port your `todo-app` Pods are listening on (in this case, 8080).
    

Step 2: Apply the ClusterIP Service definition to your Minikube cluster:

Use the `kubectl apply` command to apply the ClusterIP Service definition to your Minikube cluster. Replace `<namespace-name>` with the appropriate namespace or omit it to use the default namespace.

```bash
kubectl apply -f cluster-ip-service.yml -n <namespace-name>
```

Step 3: Verify that the ClusterIP Service is working by accessing the `todo-app` from another Pod in the cluster in your namespace:

You can create a temporary Pod within the same namespace to test accessing the `todo-app` service using its ClusterIP. Here's an example:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: test-pod
spec:
  containers:
    - name: test-container
      image: busybox
      command: ["/bin/sh"]
      args: ["-c", "wget -qO- http://todo-app-clusterip-service/<path-to-todo-app>"]
```

Replace `<path-to-todo-app>` with the actual path or endpoint you want to access in your `todo-app`. Save this Pod definition to a file (e.g., `test-pod.yml`) and apply it to your namespace:

```bash
kubectl apply -f test-pod.yml -n <namespace-name>
```

This temporary Pod will use `wget` to access your `todo-app` service via the ClusterIP. Make sure the `test-pod` is running, and then check its logs to verify that it can access the `todo-app` service successfully:

```bash
kubectl logs test-pod -n <namespace-name>
```

You should see the output from the `todo-app` service if the ClusterIP Service is working correctly.

Remember to replace `<namespace-name>` with the appropriate namespace where your `todo-app` Deployment and ClusterIP Service are located.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694232273484/82d6774e-9aca-4532-8cb1-42df0e939a29.png align="center")

## Task-3:Create a LoadBalancer Service for accessing the todo-app from outside the cluster

Step 1: Create a LoadBalancer Service definition in a YAML file (e.g., `load-balancer-service.yml`):

Create a YAML file, e.g., `load-balancer-service.yml`, and define the LoadBalancer Service for your `todo-app` Deployment. Here's an example YAML file:

```plaintext
apiVersion: v1
kind: Service
metadata:
  name: todo-app-loadbalancer-service
spec:
  selector:
    app: todo-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
  type: LoadBalancer
```

In this example:

* [`metadata.name`](http://metadata.name) specifies the name of the LoadBalancer Service.
    
* `spec.selector` specifies the labels used to select the Pods associated with the Service. Make sure the `app` label matches the label on your `todo-app` Pods.
    
* `spec.ports` specifies the ports for the LoadBalancer Service, including the protocol, port number exposed by the Service, and the targetPort, which should match the port your `todo-app` Pods are listening on (in this case, 8080).
    
* `type: LoadBalancer` specifies that you want to create a LoadBalancer Service.
    

Step 2: Apply the LoadBalancer Service definition to your Minikube cluster:

Use the `kubectl apply` command to apply the LoadBalancer Service definition to your Minikube cluster. Replace `<namespace-name>` with the appropriate namespace or omit it to use the default namespace.

```plaintext
kubectl apply -f load-balancer-service.yml -n <namespace-name>
```

Step 3: Verify that the LoadBalancer Service is working by accessing the `todo-app` from outside the cluster in your namespace:

Since you are using Minikube, a LoadBalancer Service may not create a real external load balancer. Instead, it will typically create a NodePort that you can access from your Minikube host.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694232726132/63bc6c3e-81e5-44c4-8614-7680bae94a78.png align="center")

You can get the NodePort assigned to the LoadBalancer Service:

```plaintext
kubectl get svc todo-app-loadbalancer-service -n <namespace-name>
```

Look for the `NodePort` value, which is typically in the range of 30000-32767.

Now, you can access your `todo-app` from outside the cluster using the Minikube IP and the NodePort. Obtain the Minikube IP:

```plaintext
minikube ip
```

You can now access your `todo-app` in a web browser or using tools like `curl` by visiting `http://<Minikube-IP>:<NodePort>`.

In conclusion, the tasks outlined above demonstrate fundamental concepts of working with Services in Kubernetes, particularly in a Minikube environment. Services in Kubernetes provide networking abstraction and facilitate communication between different parts of an application.