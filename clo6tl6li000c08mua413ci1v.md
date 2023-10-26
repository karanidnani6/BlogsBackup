---
title: "#Day41:Setting up an Application Load Balancer with AWS EC2🚀"
datePublished: Thu Oct 26 2023 06:45:16 GMT+0000 (Coordinated Universal Time)
cuid: clo6tl6li000c08mua413ci1v
slug: day41setting-up-an-application-load-balancer-with-aws-ec2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698214127456/85373353-064f-440b-b28d-60c2b03b6897.avif
tags: ec2, load-balancing, 90daysofdevops

---

**Title: Load Balancing Demystified! 🌐**

In the world of digital connectivity, ensuring smooth and uninterrupted user experiences is paramount. Imagine a scenario where thousands of users are trying to access a website simultaneously - handling this traffic efficiently is where **Load Balancing** comes into play! Let's take a cheerful journey through the basics of Load Balancing and explore the magic of Amazon Web Services' Elastic Load Balancing (ELB) with its three charming avatars: **Application Load Balancer (ALB), Network Load Balancer (NLB), and Classic Load Balancer (CLB).** ✨

### **What is Load Balancing?**

**Load Balancing** is like having a super-friendly traffic manager for your website or application. When numerous users knock on your digital door, a load balancer steps in to evenly distribute the incoming traffic among multiple servers. This smart balancing act ensures no server is overwhelmed, making sure everyone gets served quickly and efficiently! 🎉

### **Elastic Load Balancing: Your Digital Fairy Godmother!**

Amazon Web Services (AWS) offers a magical service called **Elastic Load Balancing (ELB)**. It's like having a fairy godmother for your digital kingdom, ensuring everything runs smoothly. ELB comes in three delightful flavors:

#### **1\. Application Load Balancer (ALB) 🌟**

**ALB** is like a sophisticated maître d' in a high-end restaurant. It operates at the application layer of the OSI model, making intelligent decisions based on content. It's perfect for routing HTTP/HTTPS traffic and is a master at hosting multiple applications on a single domain.

#### **2\. Network Load Balancer (NLB) 💡**

**NLB** is the tech-savvy guru of the ELB family. It operates at the transport layer (Layer 4) and can handle massive traffic loads with ease. If your applications demand high performance and low latency, NLB is your go-to option. It's ideal for TCP/UDP traffic.

#### **3\. Classic Load Balancer (CLB) 🎩**

**CLB** is the vintage charmer, versatile and reliable. It balances the load across multiple Amazon EC2 instances, ensuring your applications run seamlessly. While newer siblings like ALB and NLB have more features, CLB remains a solid choice for various applications.

### Task 1: Launch EC2 Instances with Apache Web Server Installed

1. **Launch EC2 Instances:**
    
    * Go to the AWS Management Console.
        
    * Navigate to EC2 and click on "Launch Instance."
        
    * Choose the Ubuntu AMI and follow the wizard to launch two instances.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698293432518/cd906097-7bb9-423a-84b5-498d242aa1d9.png align="center")
        
    * In the **Configure Instance Details** section, paste the following User Data script:
        

```bash
#!/bin/bash
apt update
apt install -y apache2
echo "Your Name" > /var/www/html/index.html
```

Replace "Your Name" with your actual name for the first instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698300723972/b5614b67-27e3-4d24-833f-a4e3de398a44.png align="center")

For the second instance, use the following User Data script:

```bash
#!/bin/bash
apt update
apt install -y apache2
echo "TrainWithShubham Community is Super Awesome :)" > /var/www/html/index.html
```

* Complete the instance creation process.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698301835715/8c30008c-1afa-42a4-b4c5-864a43003eec.png align="center")
    

1. **Copy Public IP Addresses:**
    
    * Once instances are running, copy their public IP addresses from the AWS Management Console.
        
2. **Access Apache Web Server:**
    
    * Open a web browser and paste the public IP addresses into the address bar for both instances. You should see webpages displaying your name and the specified message.
        

### Task 2: Create Application Load Balancer (ALB) and Add Instances

1. **Create Application Load Balancer:**
    
    * Go to the AWS Management Console.
        
    * Navigate to EC2 and click on "Load Balancers."
        
    * Click on "Create Load Balancer" and choose "Application Load Balancer."
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698302030043/9ccfbc6d-0267-4549-9c0d-2858350d4e0d.png align="center")
        
    * Configure the ALB settings, including listeners and availability zones, as per your requirements.
        
2. **Add Instances to Target Groups:**
    
    * While creating the ALB, create a new target group or use an existing one.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698302005635/6f5dab37-cbd5-453f-9135-43eb7da741ac.png align="center")
        
    * Add the EC2 instances created in Task 1 to the target group.
        
3. **Verify ALB and Test Load Balancing:**
    
    * After ALB is created, go to the "Target Groups" section in the EC2 dashboard.
        
    * Check the health status of instances to ensure they are healthy and registered with the ALB.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698302332984/c3d7d064-3640-48ae-a6fc-f35b880ed793.png align="center")
        
    * Open a web browser and access the ALB's DNS name or public IP address. The requests should be distributed between the instances. Verify that the pages with your name and the specified message are displayed, confirming that the ALB is working correctly.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698302551744/66962d36-aa8d-432a-aae6-5b45165c72e4.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698302565408/04a9a31c-684d-4a1f-aee7-ec7ecbcddf54.png align="center")
        

That's it! You have successfully completed Task 1 and Task 2, creating EC2 instances with Apache Web Server, modifying webpages, and setting up an Application Load Balancer to distribute traffic between the instances.