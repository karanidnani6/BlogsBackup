---
title: "Day 50: Your CI/CD pipeline on AWS - Part-1 🚀 ☁"
datePublished: Thu Dec 28 2023 07:46:19 GMT+0000 (Coordinated Universal Time)
cuid: clqowid6q000008jx1brxbsqq
slug: day-50-your-cicd-pipeline-on-aws-part-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703740695632/f939ebfd-8255-4763-93d4-a38a2d5a191f.png
tags: aws, codecommit, 90daysofdevops

---

### Introduction

In the fast-paced world of software development, efficiency and collaboration are key to delivering high-quality applications. Amazon Web Services (AWS) provides a suite of powerful tools to streamline the development, deployment, and delivery processes. In this blog post, we'll explore five essential AWS developer tools: CodeCommit, CodeBuild, CodeDeploy, CodePipeline, and S3, and discuss how they work together to create a seamless development pipeline.

### CodeCommit:

Secure Version Control in the Cloud CodeCommit is AWS's fully-managed source control service that makes it easy for teams to host secure and scalable Git repositories in the cloud. With CodeCommit, developers can collaborate seamlessly, and the service integrates with popular Git tools for a familiar experience. The repository hosting is highly available, and it provides encryption both at rest and in transit, ensuring the security of your source code.

Key features of CodeCommit:

* Fully managed Git repositories
    
* High availability and scalability
    
* Encryption at rest and in transit
    
* Integration with AWS Identity and Access Management (IAM)
    
* Easy collaboration with team members
    

### CodeBuild

Automating Build Processes CodeBuild is a fully-managed build service that compiles source code, runs tests, and produces ready-to-deploy artifacts. It scales automatically, enabling builds to run quickly and efficiently. CodeBuild supports a variety of programming languages and build tools, making it versatile for different project requirements. Integration with other AWS services and third-party tools is seamless, providing a flexible environment for your build processes.

Key features of CodeBuild:

* Fully managed build service
    
* Support for various programming languages and build tools
    
* Automatic scaling for efficiency
    
* Integration with AWS services and third-party tools
    
* Pay-as-you-go pricing model
    

### CodeDeploy:

Automated Deployment to Any Environment CodeDeploy automates the deployment of applications to a variety of compute services such as EC2 instances, Lambda functions, and even on-premises servers. It provides a consistent and repeatable deployment process, reducing the risk of errors and minimizing downtime. CodeDeploy can be easily integrated into your existing development and deployment workflows, supporting both blue/green and in-place deployment strategies.

Key features of CodeDeploy:

* Automated deployment to various environments
    
* Support for EC2 instances, Lambda functions, and on-premises servers
    
* Flexible deployment strategies, including blue/green deployments
    
* Rollback capabilities for quick recovery from issues
    
* Integration with other AWS services
    

### CodePipeline:

Continuous Integration and Delivery CodePipeline is a fully-managed continuous integration and continuous delivery (CI/CD) service that automates the build, test, and deployment phases of your release process. It orchestrates the workflow, allowing you to model, visualize, and automate the steps required to release your application. CodePipeline integrates seamlessly with other AWS services, including CodeBuild, CodeDeploy, and third-party tools, providing a comprehensive CI/CD solution.

Key features of CodePipeline:

* Automated CI/CD workflow orchestration
    
* Visual representation of pipeline stages
    
* Integration with CodeBuild, CodeDeploy, and other AWS services
    
* Flexibility to add manual approval steps
    
* Quick identification and resolution of issues in the pipeline
    

### S3:

Scalable and Secure Object Storage Amazon S3 (Simple Storage Service) is a highly scalable and secure object storage service designed to store and retrieve any amount of data from anywhere on the web. While not a developer tool in the traditional sense, S3 plays a crucial role in the development and deployment process by providing a reliable and cost-effective storage solution for artifacts, backups, and static assets.

Key features of S3:

* Scalable and durable object storage
    
* Fine-grained access controls and encryption options
    
* Integration with AWS developer tools and services
    
* Cost-effective storage for various data types
    
* High availability and reliability
    

# Task-01 :

* Set up a code repository on CodeCommit and clone it on your local.
    
* You need to setup GitCredentials in your AWS IAM.
    
* Use those credentials in your local and then clone the repository from CodeCommit
    
    **Step 1: Create a CodeCommit Repository**
    
    1. Log in to your AWS Control Console and navigate to the **CodeCommit** service.
        
    2. Click on the "**Create repository**" button.
        
    3. Enter a repository name and configure get admission to controls as wished.
        
    4. A repository gets created.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703743599033/2daa98ca-491f-4779-982a-e99b66c40bdb.png align="center")
    
    **Step 2: Set up GitCredentials in AWS IAM**
    
    To get the right of entry to your CodeCommit repository from your local machine, you want to configure **GitCredentials** for your **AWS IAM**
    
    1. Within the AWS control Console, go to **IAM**.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696223105453/b4882a31-0bc5-46f0-9bd5-848da16548d7.png?auto=compress,format&format=webp align="left")
        
    2. Pick out **"users"** from the left navigation pane.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703743698544/83f9d1b9-949f-4ebe-b1a1-08d029af584b.png align="center")
        
    3. Choose the IAM consumer you may be the usage of for Git access by selecting “**AWSCodeCommitFullAccess**” and “**AWSCodeCommitPowerUser**”.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703746552930/4b0c90a4-7704-4802-867c-0f8266f7a869.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703747338638/ee5a366c-e53d-47bf-a1c5-d33e4e2cfb33.png align="center")
        
    4. Inside the **"Safety credentials"** tab, click on the **"Create get right of entry to key"** button to generate GitCredentials.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703747664051/dcde9199-2821-4357-8cf4-0b2a01122710.png align="center")
        
    5. Now, Navigate to the repository we created earlier and let's add a file there.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703747825160/de837f8b-6d41-47b2-a47a-a535d8cef28f.png align="center")
        
    6. Click on "Create file" and Add the information
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703747949870/a477b131-b2c3-407b-8306-b706daf85eae.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703748017033/d53afa04-d665-4330-8207-0efbefe60cd3.png align="center")
        

Copy the repository URL

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703748096886/4c744a79-f619-4a19-b764-7f35d9945404.png align="center")

**Step 3: Clone the Repository regionally**

1. Now you have a CodeCommit repository and GitCredentials set up, it's time to clone the repository in your local machine.
    
2. Open your terminal and execute the subsequent instructions, replacing **with the URL of your CodeCommit repository**:
    
    ```plaintext
     git clone <your-codecommit-repo-clone-https-url>
    ```
    

1. This will clone the repository in your local system, and you may be prepared to start operating with your code.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703748868295/f035ebae-3023-4fec-9d73-c56bfad6ed4b.png align="center")
    

# Task-02 :

* Add a new file from local and commit to your local branch
    
* Push the local changes to CodeCommit repository.
    

**Step 1: Add a new file from local and commit to your local branch**

1. It Permit's to create a new file in your nearby repository. you can use any textual content editor or command-line equipment to do this.
    
    ```plaintext
     # Create a new file
     echo "new file from local" > demolocal.txt
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703749099512/d2ddd579-8136-4334-a13e-da7fb228497a.png align="center")
    

**Step 2: Commit and Push changes**

1. Now, let's commit your files and push them back to the CodeCommit repository.
    
    ```plaintext
     git status
     git add .
     git commit -m "commit message"
     git push origin <branch name>
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703749363827/3a5d969b-0109-430f-8524-2b3f0fd65ea7.png align="center")
    

You've successfully added a new file, committed the changes, and pushed them to your CodeCommit repository.

**Step 3: Verify the pushed changes to the CodeCommit repository:**

### Conclusion

AWS developer tools, including CodeCommit, CodeBuild, CodeDeploy, CodePipeline, and S3, form a powerful ecosystem that enables teams to build, test, and deploy applications efficiently. By leveraging these services, development teams can streamline their workflows, enhance collaboration, and deliver high-quality software faster. Whether you are a small startup or a large enterprise, AWS developer tools provide the flexibility and scalability needed to meet the demands of modern software development.