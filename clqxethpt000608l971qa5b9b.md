---
title: "Day 52: Your CI/CD pipeline on AWS - Part 3 🚀 ☁"
datePublished: Wed Jan 03 2024 06:41:01 GMT+0000 (Coordinated Universal Time)
cuid: clqxethpt000608l971qa5b9b
slug: day-52-your-cicd-pipeline-on-aws-part-3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704251100289/1001989a-74db-4ef1-bb5f-42464b281511.png
tags: 90daysofdevops

---

# Task-01 :

* Read about Appspec.yaml file for CodeDeploy.
    
* Deploy index.html file on EC2 machine using nginx
    
* you have to setup a CodeDeploy agent in order to deploy code on EC2
    
    ### **Step 1: Read about** `Appspec.yaml` **file for CodeDeploy**
    
    Before we jump into deployment, it's essential to understand the `appspec.yaml` file, which plays a crucial role in defining how your application should be deployed.
    
    This file is used by CodeDeploy to determine what actions to take during the deployment process.
    
    It specifies hooks, permissions, and other details required for a successful deployment.
    
    Here's a simple example of an `appspec.yaml` file:
    
    ```plaintext
    version: 0.0
    os: linux
    files:
      - source: /
        destination: /var/www/html
    hooks:
      BeforeInstall:
        - location: scripts/install_dependencies.sh
          timeout: 300
          runas: root
      AfterInstall:
        - location: scripts/install_nginx.sh
          timeout: 300
          runas: root
      ApplicationStart:
        - location: scripts/stop_nginx.sh
          timeout: 300
          runas: root
      ApplicationStop:
        - location: scripts/start_nginx.sh
          timeout: 300
          runas: root
    ```
    
    Let's break down its sections:
    
    1. **Version**: Specifies the version of the deployment specification (e.g., `0.0`).
        
    2. **OS**: Defines the operating system used by the deployment target (e.g., `Linux`).
        
    3. **Resources**: Allows you to manage AWS resources like Auto Scaling groups or EC2 instances.
        
    4. **Hooks**: Defines lifecycle event hooks for different deployment phases (e.g., `BeforeInstall`, `AfterInstall`, `ApplicationStop`, and `ApplicationStart`). Each hook specifies the location of a script file to be executed during that phase.
        
    5. **Files**: Specifies which files should be copied from the source location to the destination location on the deployment target.
        
    
    ### **Step 2: Deploy** `index.html`**file on EC2 using Nginx**
    
    ***Creating a CodeDeploy Application***
    
    1. Go to the AWS Management Console and navigate to **CodeDeploy**.
        
    2. Click on **"Applications"** and then select **"Create application."**
        
    3. Choose the compute platform as **"EC2/on-premises"** and click "Create application.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704253107158/d608cd4e-5026-4387-a002-eaf3855530f6.png align="center")
        
    4. Your application is now successfully created.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704253134974/317e7acf-846e-4e5c-ab43-1d9fdcbf4e90.png align="center")
        
    
    ***Creating a Service Role***
    
    To enable communication between CodeDeploy and other AWS services, you need to create a service role.
    
    1. Go to AWS Identity and Access Management (IAM) and create a role named **'code-deploy-service-role'** with the required permissions.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704253604761/89957fc9-7ae8-40eb-addf-0b35aa68825b.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704253688507/605e7366-2104-4f30-b2e9-7ed3e1aee620.png align="center")
        
    
    ***Setting Up an EC2 Instance***
    
    Before deploying your application, create an EC2 instance where you want to deploy the index.html file.
    
    1. Launch an Ubuntu EC2 instance on AWS.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704253952732/292a4def-7f74-4236-8db5-87675c7e60f4.png align="center")
        
    
    ***Creating a Deployment Group***
    
    Once you've created a CodeDeploy application, it's time to create a deployment group. This group defines the EC2 instances where your application will be deployed.
    
    1. Add instance names to the deployment group.
        
    2. Click on **"Create deployment group."**
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704254128498/98d3805c-56bf-4152-90b3-f82dd28cc320.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704254510694/1bb8d42e-e17e-485d-8e4c-00ecddb686a4.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704254595201/b657ea43-49b8-41b1-9502-d8d88bb79a34.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704255082058/05a931f9-298f-4eb7-9d42-5b1f0205f7c5.png align="center")
        
    
    ***Installing the CodeDeploy Agent***
    
    To deploy code on your EC2 instance, you must install the CodeDeploy agent.
    
    1. Install the CodeDeploy agent on your Ubuntu EC2 instance by running the provided commands & Check whether the Code agent is running.
        
        ```plaintext
         # This installs the CodeDeploy agent and its prerequisites on Ubuntu  
         #!/bin/bash
         sudo apt-get update
         sudo apt-get install ruby
         sudo apt-get install wget
         wget https://aws-codedeploy-ap-south-1.s3.ap-south-1.amazonaws.com/latest/install
         chmod +x ./install
         sudo ./install auto
         sudo service codedeploy-agent status
         sudo service codedeploy-agent start
         sudo service codedeploy-agent status
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704255358293/b9f15aa0-aa8c-47cc-88d5-ea6d63e93091.png align="center")
        
    
    ***Creating an index.html File***
    
    Before moving forward, create the `index.html` file that you want to deploy on your EC2 instance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704255611980/5bac5be3-73ee-4444-a2a5-f1214d3978be.png align="center")
    
    # Task-02 :
    
    Add appspec.yaml file to CodeCommit Repository and complete the deployment process.
    

***Adding an*** `appspec.yaml`***file to CodeCommit Repository***

1. Create an appspec.yaml file that specifies how CodeDeploy should handle your application.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704255878112/fb95fc30-99c6-4681-b758-943c0fe637bf.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704259351170/6e310aaf-6a1b-4bcd-9d09-aff599acd20d.png align="center")
    
2. Push all the files, including the `appspec.yaml` file, to your CodeCommit repository.
    
    **install\_**[**nginx.sh**](http://nginx.sh/)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704257404259/0bd620e5-6cce-417c-bec4-76054bcb42aa.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704259354056/5e378a0c-1ad5-49ff-bfae-73a92f0800c2.png align="center")
    

***Rebuilding the Project and Preparing for Deployment***

1. Edit the artifacts in your CodeBuild project and rebuild it.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704262654801/70103dbc-b3f5-4bfc-a882-33a5d3f651db.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704262700024/d4547d0b-f7aa-4fde-905b-b2eb30a00c64.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704262747632/c47cf5f6-62ed-44a1-ab40-a557d5fcc34f.png align="center")
    
2. Create an S3 bucket for code deployment, or use an existing one.
    
3. Add the artifacts to the S3 bucket and take note of the object URL.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704262827696/8d659897-f0db-47b9-bd57-db1fb5168dcd.png align="center")
    

***Deploying Your Application***

1. In AWS CodeDeploy, go to **"Applications," "Deployment Groups,"** and select your deployment group.
    
2. Click on **"Create deployment,"** and paste the object URL in the Revision location.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704262917068/89c61ef5-29c9-4673-9a1a-408fd0931f71.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704263007985/3e0a1df6-1655-4c1d-bf9a-5b1c1015e6e5.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704263046076/5742363a-d49e-4e29-a1db-bd1defb0abbe.png align="center")
    
    `Now we can see the deployment is successful and you can check whether the file is running or not by going` [`intoartifact.zip`](http://nginx.sh/)`>index.html and click on index.html file to have output.`