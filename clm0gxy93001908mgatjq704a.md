---
title: "#Day30: Kubernetes Overview & Architecture"
datePublished: Fri Sep 01 2023 10:45:15 GMT+0000 (Coordinated Universal Time)
cuid: clm0gxy93001908mgatjq704a
slug: day30-kubernetes-overview-architecture
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693564448705/8862cd5c-3ca6-4ae3-8536-6e97578611c0.jpeg
tags: kubernetes, k8s, 90daysofdevops

---

## Kubernetes Overview

With the widespread adoption of [containers](https://cloud.google.com/containers) among organizations, Kubernetes, the container-centric management software, has become a standard to deploy and operate containerized applications and is one of the most important parts of DevOps.

Originally developed at Google and released as open-source in 2014. Kubernetes builds on 15 years of running Google's containerized workloads and the valuable contributions from the open-source community.

1. What is Kubernetes? Write in your own words and why do we call it k8s?
    

Hey there, tech enthusiasts! 🌟 Have you ever heard of Kubernetes? It might sound like a tongue-twister, but fear not! In this blog, we're going to break it down in simple terms and throw in some emojis to make it fun! 😄

### **What is Kubernetes? 🤔**

Imagine you're a chef, and you have a bunch of dishes to prepare. You've got ingredients, recipes, and a kitchen full of helpers. But how do you manage all this chaos smoothly? 🍳

That's where Kubernetes, or "K8s" for short, comes into play. 🎩 It's like the magical kitchen manager that helps you run your restaurant (or data center) efficiently.

Kubernetes is all about managing and orchestrating containers. 🐳 Containers are like little boxes that hold your software and all its ingredients (code, libraries, settings) in one neat package.

### **Why "K8s"? 🤷‍♂️**

Now, you might be wondering why we call it "K8s." Well, it's just a shortcut! The letter "K" is followed by 8 letters ("ubernete") and then an "s" to make it easier to say and write. Imagine typing "kubernetes" all the time! 😅

1. What are the benefits of using k8s?
    

### **Benefits of Using K8s 🌟**

So, why should you care about K8s?

* **Scaling**: K8s can automatically handle more work when things get busy, like adding more chefs when the restaurant gets crowded.
    
* **Rolling Updates**: It can update your software without shutting everything down, like changing the menu while the restaurant is open.
    
* **High Availability**: K8s ensures that your dishes (or applications) are always available, even if a chef (or server) goes on vacation.
    
* **Resource Efficiency**: It uses your kitchen resources (servers) effectively, so nothing goes to waste.
    

1. Explain the architecture of Kubernetes
    

### **Kubernetes Architecture 🏛️**

Now, let's dive into how K8s works inside!

* **Control Plane**: Think of this as the restaurant manager's office. It makes decisions about how to run your dishes (containers) and keeps everything in check.
    
* **Worker Nodes**: These are your chefs (or servers). They do the actual cooking (running containers) based on what the Control Plane tells them.
    
* **Pods**: Pods are like plates. They can hold one or more dishes (containers) and ensure they work together.
    

1. What is Control Plane?
    

### **What's the Control Plane? 🧐**

The Control Plane is the brains behind K8s. It has some key components:

* **API Server**: This is like the restaurant's main entrance. It receives your requests (orders) and helps you communicate with K8s.
    
* **Etcd**: Think of this as the secret recipe book. It stores all the important data about your restaurant (configuration data).
    
* **Scheduler**: The scheduler is like the manager who decides which chef (node) should prepare your dish (container).
    

1. Write the difference between kubectl and kubelets.
    

### **Kubectl vs. Kubelet 🤔**

* **Kubectl**: This is like the menu for the restaurant manager (you). You use it to give orders to K8s. It's for managing the whole system.
    
* **Kubelet**: Kubelet is the chef's assistant. It runs on each worker node and makes sure the dishes (containers) are cooking as they should.
    

1. Explain the role of the API server.
    

### **API Server's Role 📡**

The API Server is the heart of K8s. 🫀 It does three main things:

1. **Validation**: It checks if your orders (requests) are correct and sensible.
    
2. **Authorization**: It decides if you have the authority to make those orders.
    
3. **Configuration**: It stores the secret recipes (configurations) and shares them when needed.
    

In a nutshell, Kubernetes, or "K8s," is like your kitchen manager for containers. It keeps your software dishes running smoothly, even when the restaurant (or data center) is bustling. So, next time you hear about Kubernetes, you'll know it's all about making tech kitchens more efficient and delicious! 🍽️👨‍🍳🚀