---
title: "#Day38:Getting Started with AWS Basics☁"
datePublished: Tue Sep 26 2023 10:36:53 GMT+0000 (Coordinated Universal Time)
cuid: cln06nhwy000608jrhkxn3dt1
slug: day38getting-started-with-aws-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694589979821/2b4d4ac8-8b17-4077-b0c1-7cdbb30c12a5.jpeg
tags: aws, iam, 90daysofdevops

---

Amazon Web Services (AWS) is like a vast playground for businesses and developers in the cloud computing world. 🌐 Whether you're a startup, an enterprise, or an individual, AWS provides a wide range of services to meet your computing, storage, database, analytics, and machine learning needs, just to name a few! 🚀

### What is AWS?

🤖 AWS, an Amazon subsidiary, is the most popular and widely used cloud service provider globally. It offers a scalable, reliable, and cost-effective cloud computing platform that allows you to focus on building your applications rather than managing infrastructure. 💼

Here are some key AWS services :

1. **EC2 (Elastic Compute Cloud)**: 🖥️ - Think of it as your virtual server in the cloud.
    
2. **S3 (Simple Storage Service)**: ☁️ - Your cloud-based storage solution.
    
3. **RDS (Relational Database Service)**: 🗃️ - Database management made easy.
    
4. **Lambda**: 🤖 - Serverless computing at your fingertips.
    
5. **SNS (Simple Notification Service)**: 📢 - Keep your users in the loop.
    
6. **SQS (Simple Queue Service)**: 💌 - Efficient message queuing for your apps.
    

### IAM - The Guardian of AWS Resources

Now, let's talk about AWS Identity and Access Management (IAM). 🛡️

IAM is like the gatekeeper of your AWS resources. It allows you to control who can access your resources and what actions they can perform. 🔑

Here's how IAM works:

* **Users**: 🙋‍♂️🙋‍♀️ - IAM allows you to create and manage users who need access to AWS.
    
* **Groups**: 🧑‍🤝‍🧑 - You can organize users into groups, making it easier to assign permissions.
    
* **Roles**: 🧭 - IAM roles are used to grant permissions to AWS services and resources.
    
* **Policies**: 📜 - Policies define permissions and can be attached to users, groups, or roles.
    
* **MFA (Multi-Factor Authentication)**: 🔒 - Add an extra layer of security with MFA.
    

IAM ensures the principle of least privilege, meaning users and services have only the permissions necessary to perform their tasks. This minimizes the risk of unauthorized access or accidental changes. 👮

### Why is IAM Important?

Imagine giving everyone access to your AWS account without restrictions. Chaos, right? IAM ensures that doesn't happen. It helps you:

* **Enhance Security**: 🔐 Protect your AWS resources from unauthorized access.
    
* **Compliance**: 📜 Meet regulatory requirements by controlling access.
    
* **Least Privilege**: 🚫 Only grant the necessary permissions to avoid accidents.
    
* **Audit Trails**: 📊 Keep track of who did what in your AWS account.
    
* **Manage Resources**: 📦 Organize users and resources efficiently.
    

In conclusion, AWS is a versatile cloud platform offering a wide range of services, while IAM helps you maintain control and security over your resources. Together, they empower you to harness the full potential of the cloud while keeping your data and applications safe. ☁️🔐

### [Task1:](https://github.com/karanidnani6/90DaysOfDevOps/blob/master/2023/day38/tasks.md#task1)

Create an IAM user with username of your own wish and grant EC2 Access. Launch your Linux instance through the IAM user that you created now and install jenkins and docker on your machine via single Shell Script.

Here are the general steps to accomplish this task:

**Step 1: Create an IAM User**

1. Log in to the AWS Management Console.
    
2. Navigate to the IAM (Identity and Access Management) dashboard.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695711983363/c0ceea0d-d737-4e07-a187-02260fb09e12.png align="center")
    
3. Click on "Users" in the left-hand navigation pane.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695713149472/e9004a94-8169-44aa-bdf6-d6044c3fd890.png align="center")
    
4. Click the "Create User" button.
    
5. Enter a username of your choice.
    
6. Select the "Programmatic access" checkbox to enable programmatic access.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695713759573/5458f283-ec8e-4c07-8176-6402260ba35b.png align="center")
    
7. Attach an existing policy or create a custom policy with EC2 access.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695714636976/e2eaf0ae-ca78-4713-8c23-da24796dd31e.png align="center")
    
8. Review the user details and click "Create user."
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695714662827/0d98434b-0f75-4f5d-96f5-55519e3b90cf.png align="center")
    
9. Make note of the Access Key ID and Secret Access Key for this user.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695714754517/9d36358d-6ab6-4c52-85ab-2e273f8212af.png align="center")
    

**Step 2: Launch an EC2 Instance**

1. Navigate to the EC2 dashboard.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695715243599/5628a435-c353-4cd9-bbe6-dc5a5d89357d.png align="center")
    
2. Click "Launch Instance" to create a new EC2 instance.
    
3. Choose an Amazon Machine Image (AMI) with your preferred Linux distribution.
    
4. Select an instance type.
    
5. Configure the instance details, including the IAM role you created in the previous step.
    
6. Add storage and configure other details as needed.
    
7. Review and launch the instance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695715882303/eb9a64b1-146e-4cbc-8d4b-d066d81d6333.png align="center")
    

**Step 3: SSH into the EC2 Instance**

1. Once the instance is running, SSH into it using the private key associated with the key pair you selected during instance creation.
    

Example:

```bash
 ssh -i "aws_demo_iam.pem" ubuntu@ec2-34-238-39-47.compute-1.amazonaws.com
```

**Step 4: Create and Run a Shell Script**

1. Create a shell script (e.g., `install_jenkins_docker.sh`) on the EC2 instance using a text editor such as `nano` or `vim`.
    
2. Add the following script to the file to install Jenkins and Docker:
    

```bash
#!/bin/bash

# Update the package list
sudo apt-get update -y

# Install Jenkins
sudo apt-get install -y openjdk-8-jdk
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update -y
sudo apt-get install -y jenkins

# Install Docker
sudo apt-get install -y docker.io

# Start Jenkins and Docker services
sudo systemctl start jenkins
sudo systemctl enable jenkins
sudo systemctl start docker
sudo systemctl enable docker

# Add the current user to the docker group to run Docker without sudo
sudo usermod -aG docker $(whoami)

# Clean up
sudo apt-get clean
```

1. Save and exit the text editor.
    
2. Make the script executable:
    

```bash
chmod +x install_jenkins_docker.sh
```

1. Execute the script to install Jenkins and Docker:
    

```bash
./install_jenkins_docker.sh
```

The script will install Jenkins, Docker, and configure them on your EC2 instance. After the script completes, you should be able to access Jenkins from your instance's public IP address and port 8080 in a web browser. Remember to configure security settings and access controls for Jenkins according to your requirements.

### [Task2:](https://github.com/karanidnani6/90DaysOfDevOps/blob/master/2023/day38/tasks.md#task2)

In this task you need to prepare a devops team of avengers. Create 3 IAM users of avengers and assign them in devops groups with IAM policy.

1. Log in to your AWS Management Console.
    
2. Navigate to the IAM service.
    
3. Click on "Users" in the left navigation pane.
    
4. Click "Add user."
    
5. Enter the usernames of the IAM users.
    
6. Select "Programmatic access" and "AWS Management Console access" as access types.
    
7. Choose "Autogenerated password" or "Custom password" to set initial passwords.
    
8. Uncheck the "User must create a new password at next sign-in" option (if you set a custom password).
    
9. Choose "**Add user to group**" and Create the **"DevOps"** group
    
10. Search for and attach relevant policies to the group. For DevOps access, you might attach policies like "**AmazonEC2FullAccess," "AmazonS3FullAccess," "AmazonRDSFullAccess,"** etc.
    
11. Review and create the group.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694167438304/e33d35db-17af-47a1-ae54-59a34fed2b1a.png?auto=compress,format&format=webp align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694167561867/9a4b3cfd-4457-4751-a90a-4d677323c57f.png?auto=compress,format&format=webp align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694167730540/28e1d94e-60ed-43c1-b57e-27245e76bf38.png?auto=compress,format&format=webp align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694167766973/966b1955-f6ae-492d-8196-7e25ec2cd399.png?auto=compress,format&format=webp align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694167845932/1903b18d-5e75-4136-88a5-cdd6a6200b91.png?auto=compress,format&format=webp align="left")
    
12. Now, Review and create the users.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694167875699/55678242-59cd-426a-b922-cc7230562737.png?auto=compress,format&format=webp align="left")
    
13. Now, **each user** is associated with a specific **DevOps** group with the necessary **IAM policies**. You can add more users by clicking **“create users”** from Users.
    
    In summary, AWS users and groups are fundamental components for managing access and security within Amazon Web Services. Careful configuration and adherence to the principle of least privilege are crucial for maintaining a secure environment. AWS offers robust tools like IAM and Organizations for efficient user and group management. As more organizations embrace AWS, mastering these aspects is vital for data and resource protection.