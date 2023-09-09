---
title: "#Day35:Mastering ConfigMaps and Secrets in Kubernetes🔒🔑🛡️"
datePublished: Sat Sep 09 2023 06:20:38 GMT+0000 (Coordinated Universal Time)
cuid: clmbn0h0c00090aik6hqiescw
slug: day35mastering-configmaps-and-secrets-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694233857886/cdfd0024-5fe7-4932-a77d-8492189a43a5.png
tags: k8s, secrets, configmap, 90daysofdevops

---

### **Introduction to ConfigMaps and Secrets in Kubernetes**

In the dynamic world of Kubernetes, efficient configuration management and secure handling of sensitive data are paramount. To tackle these challenges, Kubernetes offers two essential resources: **ConfigMaps** and **Secrets**.

**ConfigMaps**

provide a means to store configuration data in a structured key-value format, enabling the decoupling of configuration from application code. They serve as a powerful tool for managing non-sensitive parameters like environment variables, application settings, and properties. ConfigMaps are instrumental in ensuring that your applications remain adaptable and environment-agnostic.

**Secrets**

are the guardians of sensitive information in Kubernetes. These resources are designed to securely store confidential data such as passwords, API tokens, encryption keys, and certificates. Secrets encrypt data at rest and offer a robust solution for safeguarding sensitive credentials, preventing them from being exposed in plaintext within your application pods.

In this exploration of ConfigMaps and Secrets, we'll dive deeper into their purpose, use cases, and practical examples. By the end of this journey, you'll have a solid understanding of how these Kubernetes resources can enhance both the flexibility and security of your containerized applications. Let's embark on this insightful journey into the world of ConfigMaps and Secrets in Kubernetes! 🚀🔒

## Task 1:Create a ConfigMap for your Deployment

**Step 1: Create a ConfigMap**

You can create a ConfigMap either using a YAML file or directly from the command line.

Create a ConfigMap using a YAML file (e.g., `configmap.yaml`).

```plaintext
    apiVersion: v1
    kind: ConfigMap
    metadata:
      name: app-demo
    data:
      name: django-todo-app
      namespace: todo-app
      application: todo-app
      protocol: TCP
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694238549423/34eddb2a-1517-4e92-9665-9a74772b0280.png align="center")

1. **Update the deployment.yml file**
    
    * Modify your deployment.yml file to include the ConfigMap. Specify the ConfigMap in the `spec` section of your Deployment configuration.
        
    

```plaintext
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: todo-app-deployment
      labels: 
        app: todo-app  
      namespace: todo-app
    spec:
      replicas: 1
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
              image: karanidnani6/todo-app
              ports:
              - containerPort: 8000

              env:
                - name: application
                  valueFrom:
                    configMapKeyRef:
                      name: app-demo
                      key: application
```

1. **Apply the updated deployment**
    
    * Deploy the updated configuration using the following command
        

```plaintext
    kubectl apply -f deployment.yml -n <namespace-name>
```

1. **Verify the ConfigMap**
    
    * Ensure that the ConfigMap has been successfully created by checking the status of ConfigMaps within your specified Namespace.
        

```plaintext
    kubectl get configmaps -n <namespace-name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694238922561/f71fa245-c0ac-4f14-a432-2964eb37eb50.png align="center")

* To view detailed information about the Configmap use the following command
    

```plaintext
    kubectl describe configmap <configmap-name> -n <namespace-name>
```

## Task 2:Create a Secret for your Deployment

**Step 1: Create a Secret**

You can create a Secret either using a YAML file or directly from the command line. create a Secret using a YAML file (e.g., `secret.yaml`). Here's an example YAML file:

```plaintext
    apiVersion: v1
    kind: Secret
    metadata:
      name: secret-file
      namespace: todo-app
    type: Opaque
    data:
      password: a2FyYW5pc3JlYWw=
```

1. **Apply the created secret**
    
    ```plaintext
     kubectl apply -f < secret-file-name > -n < namespace-name >
    ```
    
2. **Update the deployment.yml file**
    
    * Modify your deployment.yml file to include the Secret. Specify the Secret in the `spec` section of your Deployment configuration.
        

```plaintext
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: todo-app-deployment
      labels:
        app: todo-app
      namespace: todo-app
    spec:
      replicas: 1
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
              image: karanidnani6/todo-app
              ports:
              - containerPort: 8000

              env:
                - name: secret
                  valueFrom:
                    secretKeyRef:
                      name: secret-file
                      key: password
```

1. **Apply the updated deployment**
    
    * Deploy the updated configuration using the command
        

```plaintext
    kubectl apply -f deployment.yml -n <namespace-name>
```

1. **Verify the Secret**
    
    * Ensure that the Secret has been successfully created by checking the status of Secrets within your specified Namespace
        

```plaintext
    kubectl get secrets -n < namespace-name >
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694240296058/3e859cd8-c10d-48d2-a32f-20e01e82bcd8.png align="center")

In conclusion, configuring ConfigMaps and Secrets in Kubernetes is essential for separating configuration data and sensitive information from your application code, providing better flexibility and security.