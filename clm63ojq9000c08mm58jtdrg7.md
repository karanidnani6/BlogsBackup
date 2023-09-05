---
title: "#Day32:Launching your Kubernetes Cluster with Deployment"
datePublished: Tue Sep 05 2023 09:20:38 GMT+0000 (Coordinated Universal Time)
cuid: clm63ojq9000c08mm58jtdrg7
slug: day32launching-your-kubernetes-cluster-with-deployment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693882724910/1f25f587-0d57-4b2d-b582-299a70af113d.jpeg
tags: deployment, kubernetes, pods

---

In Kubernetes (often abbreviated as K8s), a **Deployment** is a resource object used to manage and describe the desired state of a set of replica Pods. Deployments are a higher-level abstraction that simplifies the process of scaling and updating applications within a Kubernetes cluster.

Here are some key aspects and features of Deployments in Kubernetes:

1. **Replica Sets**: Behind the scenes, a Deployment creates and manages Replica Sets. A Replica Set ensures that a specified number of replica Pods are running at any given time.
    
2. **Desired State**: A Deployment allows you to declare the desired state for your application, including the number of replicas (Pods) you want to run. Kubernetes will automatically work to maintain this desired state.
    
3. **Rolling Updates**: One of the essential features of Deployments is support for rolling updates. You can easily update your application by changing the Docker image, environment variables, or other attributes of your Pods. The Deployment will gradually update Pods without disrupting the service.
    
4. **Rollback**: If an update doesn't go as planned or introduces issues, you can roll back to a previous version of your application with ease. Kubernetes tracks revision history, allowing for easy rollbacks.
    
5. **Scalability**: You can scale your application up or down by simply adjusting the desired number of replicas in the Deployment configuration. Kubernetes will automatically create or terminate Pods to meet the desired count.
    
6. **Self-healing**: Deployments also provide self-healing capabilities. If a Pod fails for any reason, the Deployment controller will detect the failure and create a new Pod to replace it, ensuring that the desired number of replicas is maintained.
    
7. **Pod Template**: In a Deployment configuration, you specify a Pod template that defines the characteristics of the Pods that should be created. This includes the container image, resource requirements, environment variables, and more.
    

## Task-1:

**Create one Deployment file to deploy a sample todo-app on K8s using "Auto-healing" and "Auto-Scaling" feature**

In this task, we will walk through the process of creating a **Kubernetes Deployment for todo-app**, leveraging the **auto-healing** and **auto-scaling** features.

**Prerequisites:**

* Docker Hub account
    
* Docker image of the todo-app built and tagged
    

**Step 1: Push the Docker Image to Docker Hub**

Before deploying the Kubernetes Deployment, ensure that you have built the Docker image of the todo-app and pushed it to Docker Hub. This ensures that the Kubernetes cluster can access the image when creating the pods.

```plaintext
docker login   # Log in to your Docker Hub account
docker push karanidnani6/django-todo
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693901857937/2b236480-acd6-4fdf-98a1-69f7ce85c944.png align="center")

**Step 2: Create a Deployment YAML File**

Create a new YAML file named `deployment.yml` and add the following content to it. This YAML file defines the Deployment with auto-healing and auto-scaling features.

```plaintext
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-app
spec:
  replicas: 3  # Initial number of replicas
  selector:
    matchLabels:
      app: todo-app
  template:
    metadata:
      labels:
        app: todo-app
    spec:
      containers:
        - name: todo-app
          image: karanidnani6/django-todo
          ports:
            - containerPort: 8000.
```

**Explanation of deployment.yml**

* `apiVersion`: Specifies the Kubernetes API version to use.
    
* `kind`: Defines the resource type as a Deployment.
    
* `metadata`: Contains metadata about the Deployment, including its name.
    
* `spec.replicas`: Specifies the desired number of replicas (pods) to maintain. This is the basis for **auto-scaling**.
    
* `spec.Selector`: Defines how the Deployment selects which pods to manage based on labels.
    
* `spec.template`: Specifies the pod template to be used for creating new pods.
    
* `spec.template.metadata.labels`: Labels to be applied to the pods.
    
* `spec.template.spec.containers`: Defines the containers within the pod, including the image and ports.
    

**Step 3: Apply the Deployment to Kubernetes**

Save the `deployment.yml` file and apply the Deployment to your Kubernetes cluster using the following command:

```plaintext
kubectl apply -f deployment.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693905067983/1a96780d-5bb1-4ad4-9278-5380be7219ab.png align="center")

  
**Step 4: Testing Auto-Healing**

To validate the functionality of the auto-healing feature, deliberately remove one of the pods.

Kubernetes will autonomously generate a new pod to substitute the removed instance

```plaintext
kubectl delete pod <pod_name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693905202713/4176d170-f1d6-4045-bc32-8bd5eb7f985b.png align="center")

**Step 5: Set Up Auto-Scaling**

To enable auto-scaling, you need to create a Horizontal Pod Autoscaler (HPA). For example, you can autoscale the todo app based on CPU utilization:

```plaintext
 hpa.yaml
apiVersion: autoscaling/v2beta2
kind: HorizontalPodAutoscaler
metadata:
  name: todo-app-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: todo-app
  minReplicas: 2
  maxReplicas: 5
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 80
```

Apply this HPA using `kubectl`:

```plaintext
kubectl apply -f hpa.yaml
```

This HPA will scale the todo app deployment up or down based on CPU utilization, targeting an average of 80% CPU usage per pod.

**Step 7: Delete the Deployment**

If you need to remove the entire Deployment and its associated pods, use the following command:

```plaintext
kubectl delete -f deployment.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693905559214/a799e8af-234e-489c-a50a-80c830ad55e2.png align="center")

🚀 In completing these steps, you've successfully orchestrated a Kubernetes Deployment for a sample todo-app, complete with robust auto-healing and auto-scaling capabilities. With the Docker image thoughtfully hosted on Docker Hub, Kubernetes efficiently retrieved it during the deployment phase.

✨ In Conclusion This discussion has taken you on a comprehensive journey through Kubernetes Deployments. It encompassed aspects of application administration, declarative evolution, updates, scalability, and disaster recovery. Your hands-on experience in deploying a prototype todo-app with automated healing and scaling has strengthened your command of Kubernetes.

Keep in mind that hands-on practice and exploration are the cornerstones of mastering Kubernetes. Continue to delve into diverse scenarios to deepen your understanding of this dynamic ecosystem. Armed with this knowledge, you can expertly manage applications and fortify resilience within the Kubernetes realm.

Wishing you the best of luck in your ongoing deployment endeavors! 👍🌟✌️