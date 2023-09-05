---
title: "#Day 31 : Installation of minikube on local &  Kubernetes Cluster with Nginx running"
datePublished: Tue Sep 05 2023 02:46:36 GMT+0000 (Coordinated Universal Time)
cuid: clm5pltqb000009mkc7dbciwu
slug: day-31-installation-of-minikube-on-local-kubernetes-cluster-with-nginx-running
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693832125628/f239e5da-362c-487d-86d8-50cc9821541a.png
tags: nginx, kubernetes, k8s

---

### **What is minikube?**

Minikube is a tool which quickly sets up a local Kubernetes cluster on macOS, Linux, and Windows. It can deploy as a VM, a container, or on bare-metal.

Minikube is a pared-down version of Kubernetes that gives you all the benefits of Kubernetes with a lot less effort.

This makes it an interesting option for users who are new to containers, and also for projects in the world of edge computing and the Internet of Things.

### **Features of minikube -**

(a) Supports the latest Kubernetes release (+6 previous minor versions)

(b) Cross-platform (Linux, macOS, Windows)

(c) Deploy as a VM, a container, or on bare-metal

(d) Multiple container runtimes (CRI-O, containerd, docker)

(e) Direct API endpoint for blazing fast image load and build

(f) Advanced features such as LoadBalancer, filesystem mounts, FeatureGates, and network policy

(g) Addons for easily installed Kubernetes applications

(h) Supports common CI environments

## Task-01: Install minikube on your local

# Minikube Installation Guide for Ubuntu

This guide provides step-by-step instructions for installing Minikube on Ubuntu. Minikube allows you to run a single-node Kubernetes cluster locally for development and testing purposes.

## Pre-requisites

* Ubuntu OS
    
* sudo privileges
    
* Internet access
    
* Virtualization support enabled (Check with `egrep -c '(vmx|svm)' /proc/cpuinfo`, 0=disabled 1=enabled)
    

---

## Step 1: Update System Packages

Update your package lists to make sure you are getting the latest version and dependencies.

```plaintext
sudo apt update
```

[![image](https://user-images.githubusercontent.com/40052830/261849355-57f1c5d9-474a-43b8-90b9-fe542e122f3f.png align="left")](https://user-images.githubusercontent.com/40052830/261849355-57f1c5d9-474a-43b8-90b9-fe542e122f3f.png)

## Step 2: Install Required Packages

Install some basic required packages.

```plaintext
sudo apt install -y curl wget apt-transport-https
```

[![image](https://user-images.githubusercontent.com/40052830/261849450-84ad8474-8d4d-4d4b-a04d-def88f76dc9a.png align="left")](https://user-images.githubusercontent.com/40052830/261849450-84ad8474-8d4d-4d4b-a04d-def88f76dc9a.png)

---

## Step 3: Install Docker

Minikube can run a Kubernetes cluster either in a VM or locally via Docker. This guide demonstrates the Docker method.

```plaintext
sudo apt install -y docker.io
```

[![image](https://user-images.githubusercontent.com/40052830/261849550-d261f75b-a22f-4510-b3a3-14e1cecaf3e1.png align="left")](https://user-images.githubusercontent.com/40052830/261849550-d261f75b-a22f-4510-b3a3-14e1cecaf3e1.png)

Start and enable Docker.

```plaintext
sudo systemctl enable --now docker
```

Add current user to docker group (To use docker without root)

```plaintext
sudo usermod -aG docker $USER && newgrp docker
```

Now, logout (use `exit` command) and connect again.

---

## Step 4: Install Minikube

First, download the Minikube binary using `curl`:

```plaintext
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```

Make it executable and move it into your path:

```plaintext
chmod +x minikube
sudo mv minikube /usr/local/bin/
```

[![image](https://user-images.githubusercontent.com/40052830/261849695-80e8a137-286a-4334-886b-ea4821f596b2.png align="left")](https://user-images.githubusercontent.com/40052830/261849695-80e8a137-286a-4334-886b-ea4821f596b2.png)

---

## Step 5: Install kubectl

Download kubectl, which is a Kubernetes command-line tool.

```plaintext
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

**Check above image ⬆️** Make it executable and move it into your path:

```plaintext
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

[![image](https://user-images.githubusercontent.com/40052830/261849769-cdda6c84-f6c9-4d05-87e0-ed8627e46a3a.png align="left")](https://user-images.githubusercontent.com/40052830/261849769-cdda6c84-f6c9-4d05-87e0-ed8627e46a3a.png)

---

## Step 6: Start Minikube

Now, you can start Minikube with the following command:

```plaintext
minikube start --driver=docker
```

This command will start a single-node Kubernetes cluster inside a Docker container.

---

## Step 7: Check Cluster Status

Check the cluster status with:

```plaintext
minikube status
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693880395323/c4866523-efe1-416a-b498-57976575b125.png align="center")

You can also use `kubectl` to interact with your cluster:

```plaintext
kubectl get nodes
```

---

## Step 8: Stop Minikube

When you are done, you can stop the Minikube cluster with:

```plaintext
minikube stop
```

---

## Optional: Delete Minikube Cluster

If you wish to delete the Minikube cluster entirely, you can do so with:

```plaintext
minikube delete
```

---

That's it! You've successfully installed Minikube on Ubuntu, and you can now start deploying Kubernetes applications for development and testing.

## Task-02:

## Create your first pod on Kubernetes through minikube.

### Let's understand the concept **pod**

Pods are the smallest deployable units of computing that you can create and manage in Kubernetes.

A Pod (as in a pod of whales or pea pod) is a group of one or more containers, with shared storage and network resources, and a specification for how to run the containers. A Pod's contents are always co-located and co-scheduled, and run in a shared context. A Pod models an application-specific "logical host": it contains one or more application containers which are relatively tightly coupled.

To create your first pod on Kubernetes using Minikube, follow these steps:

1. **Install Minikube**: If you haven't already, you'll need to install Minikube on your system. You can find installation instructions for your specific platform here: [Minikube Installation Guide](https://minikube.sigs.k8s.io/docs/start/).
    
2. **Start Minikube**: Open a terminal and start Minikube by running the following command:
    
    ```bash
    minikube start
    ```
    
    This command will create a new Minikube cluster. It may take a few minutes to complete.
    
3. **Verify Cluster**: You can verify that Minikube is running correctly by using the following command:
    
    ```bash
    minikube status
    ```
    
    It should show that Minikube is running and the kubectl context is set to the Minikube cluster.
    
4. **Create a Pod**: Now, you can create a simple Pod using a YAML configuration file. Here's an example YAML file named `my-pod.yaml` for a basic NGINX web server Pod:
    
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
      name: nginx
    spec:
      containers:
        - name: nginx-container
          image: nginx:latest
    ```
    
    Save this YAML file on your system.
    
5. **Apply the Pod Configuration**: Apply the Pod configuration to your Minikube cluster using `kubectl`:
    
    ```bash
    kubectl apply -f my-pod.yaml
    ```
    
    This will create the Pod in your Minikube cluster.
    
6. **Check Pod Status**: You can check the status of your Pod using the following command:
    
    ```bash
    kubectl get pods
    ```
    
    It should show the status of your `my-nginx-pod` Pod as "Running" after a brief moment.
    
7. **Access the Pod**: To access the NGINX web server running in your Pod, you need to expose it as a service. You can use the following command to create a NodePort service:
    
    ```bash
    kubectl expose pod nginx --type=NodePort --port=80
    ```
    
8. **Find the Port**: Find the NodePort assigned to your service:
    
    ```bash
    kubectl get svc
    ```
    
    Look for the "PORT(S)" column, and you'll find a port number (e.g., 30080) that maps to port 80 on your Pod.
    
9. **Access the NGINX Web Server**: You can access the NGINX web server in your Pod by opening a web browser and navigating to `http://<minikube-ip>:<NodePort>`. To get the Minikube IP, use:
    
    ```bash
    minikube ip
    ```
    
    Replace `<minikube-ip>` with the IP address and `<NodePort>` with the NodePort number you found in step 8.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693881880870/9384a8e9-93fe-4996-afe7-30d9f8ec92ae.png align="center")
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693881938086/7fce1990-143a-4479-8fa0-bc94a4c79e24.png align="center")

That's it! You've created your first Pod on Minikube and accessed a simple NGINX web server running inside the Pod. You can further customize and manage your Kubernetes resources as needed for your applications.