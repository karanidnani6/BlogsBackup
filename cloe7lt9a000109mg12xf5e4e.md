---
title: "#Day43:S3 Programmatic Access with AWS CLI 💻 📁"
datePublished: Tue Oct 31 2023 10:52:03 GMT+0000 (Coordinated Universal Time)
cuid: cloe7lt9a000109mg12xf5e4e
slug: day43s3-programmatic-access-with-aws-cli
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698741380571/0f83662b-6a91-47b4-8362-0543d1c45104.png
tags: 90daysofdevops

---

In the ever-expanding digital universe, managing data efficiently is paramount. Amazon Simple Storage Service, popularly known as Amazon S3, has emerged as a game-changer in the realm of cloud storage. Let's take a dive into the basics of Amazon S3: its features, characteristics, and real-world applications, all explained in simple terms!

### **What is Amazon S3?**

Amazon S3 is like a virtual warehouse for your digital stuff. It's a cloud storage service provided by Amazon Web Services, allowing you to store and retrieve any amount of data, anytime, anywhere via the internet. Think of it as a secure, digital storage space where you can keep your files, images, videos, and more.

### **Features of Amazon S3:**

#### \*\*1. **Unlimited Storage:**

With S3, you can store practically any amount of data—ranging from a few files to massive collections—without worrying about running out of space.

#### **2\. Durability and Reliability:**

S3 stores your data across multiple servers and locations. This redundancy ensures that even if one server fails, your data remains safe and accessible.

#### **3\. Security:**

S3 offers robust security features, allowing you to control who can access your data. You can set up private, password-protected areas and manage permissions with ease.

#### **4\. Scalability:**

Whether you're a small business or a large enterprise, S3 scales with your needs. It effortlessly handles your growing data, adapting to your requirements seamlessly.

#### **5\. Accessibility:**

You can access your stored data from anywhere with an internet connection. This accessibility makes it ideal for businesses and individuals with a global presence.

### **Characteristics of Amazon S3:**

#### **1\. Object-Based Storage:**

S3 stores data as objects, which can include files, images, videos, or even entire applications. Each object contains the data, metadata, and a unique identifier.

#### **2\. Easy-to-Use Interface:**

S3's user-friendly interface simplifies the process of uploading, accessing, and managing your files. You can interact with S3 via the AWS Management Console, AWS CLI, or SDKs.

#### **3\. Pay-as-You-Go Pricing:**

You only pay for the storage you use, making S3 a cost-effective solution for businesses of all sizes. There are no upfront fees, and you can adjust your storage capacity as needed.

### **Applications of Amazon S3:**

#### **1\. Data Backup and Recovery:**

Businesses use S3 to create backups of their critical data. In case of emergencies or data loss, they can quickly restore their information, ensuring continuity.

#### **2\. Web Hosting and Content Delivery:**

S3 serves as an excellent platform for hosting websites and delivering content like images, videos, and scripts. Its high availability and low latency enhance user experience.

#### **3\. Big Data Analytics:**

Data scientists and analysts leverage S3 to store vast datasets for analysis. Its scalability and integration with analytics tools make it a go-to choice for big data applications.

In a nutshell, Amazon S3 is a reliable, secure, and versatile cloud storage service with a wide array of applications. Whether you're safeguarding important documents, hosting a website, or analyzing vast amounts of data, S3 simplifies the way you handle digital information. Embrace the power of S3 and experience seamless, worry-free storage in the cloud! ☁️🔐🌐

### **Task 01: EC2 Instance and S3 Bucket Setup**

#### **Step 1: Launch an EC2 Instance**

1. **AWS Management Console:**
    
    * Go to the AWS Management Console.
        
    * Navigate to EC2 service.
        
    * Click on "Launch Instance" to create a new instance. Choose an Amazon Machine Image (AMI) of your choice, configure instance details, add storage, and configure security groups (make sure to allow SSH traffic on port 22).
        
2. **SSH Connection:**
    
    * Once the instance is running, use SSH to connect to it. Open your terminal or command prompt and use the following command:
        
        ```bash
        ssh -i /path/to/your/key.pem ec2-user@your-instance-public-ip
        ```
        

#### **Step 2: Create an S3 Bucket and Upload a File**

1. **AWS Management Console:**
    
    * Navigate to S3 service.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698745824369/d6cd7f17-4065-4334-a7c8-349d578194a8.png align="center")
        
    * Click on "Create Bucket" and follow the prompts to create a new bucket.
        
    * Inside the bucket, click on "Upload" to upload a file.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698747018286/01d5a582-e6a6-4a63-9db9-9a43f290f5d5.png align="center")
        
        It's time to access the file we uploaded to the S3 bucket from our EC2 instance using AWS CLI:
        
        1. SSH into your EC2 instance.
            
        2. Install the AWS CLI if it's not already installed by running command
            
            ```plaintext
             sudo apt-get update
             sudo apt-get install awscli -y
            ```
            

Use the command to download the file from the S3 bucket to your EC2 instance.

```plaintext
 aws s3 ls
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698747695249/8acaf92f-15fb-4855-9cd1-96c5ace8c354.png align="center")

### **Task 02: EC2 Snapshot and File Verification**

#### **Step 1: Create a Snapshot of the EC2 Instance**

1. **AWS Management Console:**
    
    * Navigate to the EC2 service.
        
    * Select your running instance.
        
    * From the "Actions" menu, choose "Create Image" to create a snapshot of your instance.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698747772537/d5bc00d6-e177-40dd-acb7-40822dd41777.png align="center")
        
2. **Launch a New EC2 Instance from the Snapshot:**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698747953275/8f35aade-2fac-4dd0-86fb-09f625f53179.png align="center")
    
    * After the snapshot is created, go to the AMIs section in the EC2 service.
        
    * Select your snapshot and click on "Launch Instance from Image" to create a new instance.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698749208034/7aae5cec-f71a-40d4-bf23-86fd8cd624db.png align="center")
        

#### **Step 2: Download a File from S3 and Verify**

1. **AWS CLI:**
    
    * On your local machine, use AWS CLI to download the file from the S3 bucket:
        
        ```bash
        aws s3 cp s3://your-bucket-name/your-file-name /path/to/local/destination
        ```
        
2. **Verify File Contents:**
    
    * SSH into both EC2 instances.
        
    * Use a text editor or command-line tools to view the contents of the downloaded file on both instances. You can use `cat`, `less`, or any text editor of your choice.
        

By following these steps, you will have successfully completed the tasks specified.