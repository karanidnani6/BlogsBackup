---
title: "Day 47: Test Knowledge on aws 💻 📈"
datePublished: Tue Dec 19 2023 06:46:11 GMT+0000 (Coordinated Universal Time)
cuid: clqbzecwg000009jqahmk579b
slug: day-47-test-knowledge-on-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702956897367/ac3e2053-8ab7-4510-a872-8329a2709d57.jpeg
tags: aws, 90daysofdevops

---

Today, we will be test the aws knowledge on services in AWS, as part of the 90 Days of DevOps Challenge.

### Task-01

* Launch an EC2 instance using the AWS Management Console and connect to it using SSH.
    
* Install a web server on the EC2 instance and deploy a simple web application.
    
* Monitor the EC2 instance using Amazon CloudWatch and troubleshoot any issues that arise
    

Launching an EC2 instance on AWS, installing a web server, deploying a simple web application, and monitoring with Amazon CloudWatch involves several steps. Here's a step-by-step guide:

### **Step 1: Launch EC2 Instance**

### **Login to AWS Console:**

* Go to the AWS Management Console.
    
* Sign in or create an AWS account.
    

1. **Navigate to EC2:**
    
    * In the AWS Management Console, go to the EC2 Dashboard.
        
2. **Launch an Instance:**
    
    * Click on "Instances" in the left navigation pane.
        
    * Click the "Launch Instance" button.
        
3. **Choose an Amazon Machine Image (AMI):**
    
    * Select an AMI based on your requirements (e.g., Amazon Linux 2 AMI).
        
4. **Choose an Instance Type:**
    
    * Select an instance type based on your needs.
        
5. **Configure Instance:**
    
    * Configure the instance details, including the number of instances, network settings, etc.
        
6. **Add Storage:**
    
    * Configure storage options based on your needs.
        
7. **Add Tags:**
    
    * Add tags to your instance for better organization.
        
8. **Configure Security Group:**
    
    * Configure security group rules to allow inbound traffic on port 22 (SSH) and any other ports your web application needs.
        
9. **Review and Launch:**
    
    * Review your settings and click "Launch."
        
    * Select an existing key pair or create a new one to connect to your instance.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702958639492/4417f932-65d7-4120-9e64-b6913c8fc23b.png align="center")
        
        ### **Step 2: Connect to EC2 Instance**
        
        1. **Get Public IP:**
            
            * Once the instance is running, note the public IP address.
                
        2. **SSH into the Instance:**
            
            * Open a terminal on your local machine.
                
            * Use the following command to connect to your EC2 instance:
                
                ```plaintext
                ssh -i "test_aws.pem" ubuntu@ec2-54-198-221-76.compute-1.amazonaws.com
                ```
                
                Replace `/path/to/your/key.pem` with the path to your private key and `your-public-ip` with your EC2 instance's public IP address.
                
                ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702958819883/cf065705-bd38-4c33-ba4e-ad8d60002d13.png align="center")
                
        
        ### **Step 3: Install Web Server and Deploy Web Application**
        
        1. **Updating Package Manager**: On the EC2 instance, update the package manager using the command
            
            ```plaintext
             sudo apt update -y
            ```
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702959073905/2a6338cf-6c01-4d3a-bbe7-80bba153ddcf.png align="center")
            
        2. **Installing Apache Web Server**: Install the Apache Web Server on the EC2 instance with the command
            
            ```plaintext
             sudo apt install apache2 -y
            ```
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702959837114/eb8a2605-9b98-47a9-9615-2405b67060e8.png align="center")
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702962991414/080df619-09fb-436d-a172-f4eaa2763ab2.png align="center")
            
        
        #### Step 3: Deploy a Simple Web Application
        
        1. Create a simple HTML file (e.g., index.html):
            
            ```plaintext
            echo "<html><body><h1>Hello from your EC2 instance!</h1></body></html>" | sudo tee /var/www/html/index.html
            ```
            

Open a web browser and navigate to your EC2 instance's public IP address. You should see the simple web application.

## **Monitoring EC2 Instance with Amazon CloudWatch**

2. **Accessing AWS CloudWatch**: Go to the AWS CloudWatch service in the AWS Management Console.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695707454137/3f1f5d6a-a0f3-4a0b-842b-54049c1c8e00.png?auto=compress,format&format=webp align="left")
    
3. **Creating an Alarm**: Click on **"Create alarm"** and select the EC2 metric you want to monitor, e.g. **CPU utilization**
    
4. **Configuring Conditions**: Set up alarm conditions and notification settings as needed.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695707644689/a62294c5-b23c-419b-84a9-7844ccaa51b0.png?auto=compress,format&format=webp align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695707698300/b3ec8dbb-a8d3-41f3-9a04-6adcf270ca95.png?auto=compress,format&format=webp align="left")
    
5. **Creating the Alarm**: Give your alarm a name and create the alarm. This will trigger alerts based on the conditions you've set.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695707883718/e6a63b76-788a-4138-9b19-dc5deafa041e.png?auto=compress,format&format=webp align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702874641696/b712e2b4-f3e4-4357-90c8-d21c64174eef.png align="left")
    
    ## Task-02
    
    * Create an Auto Scaling group using the AWS Management Console and configure it to launch EC2 instances in response to changes in demand.
        
    * Use Amazon CloudWatch to monitor the performance of the Auto Scaling group and the EC2 instances and troubleshoot any issues that arise.
        
    * Use the AWS CLI to view the state of the Auto Scaling group and the EC2 instances and verify that the correct number of instances are running.
        
    
    **Create a Launch Template:** Begin by generating a 'Launch Template' from an EC2 instance.
    
6. **Launch Template Successfully Created:** Confirm that the launch template has been successfully created.
    
7. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702966325496/3089f3a0-d8a3-4541-b221-97ca8c26df0c.png align="center")
    
    **Commence Auto Scaling Group Creation:** Initiate the process by clicking on the "Create Auto Scaling group" button.
    
8. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702966406766/7e3fe246-d2f1-49fa-953a-a64f3dcf1e6f.png align="center")
    
    **Select Launch Template:** Choose the launch template to be applied to the instances within the group.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702966658267/6bb893f5-cffc-484e-a24c-11cd1c07ae69.png align="center")
    
9. **Define Instance Type and Configuration:** Specify the instance type and configure additional details, such as VPC, subnet, security groups, and storage.
    
10. **Establish Scaling Policies:** Set up scaling policies to govern when new instances should be launched. Configure desired, minimum, and maximum capacity for instances.
    
11. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702966748982/cd003f3f-17e4-4ac6-a0a5-9c9a9e90e2db.png align="center")
    
    **Choose Target Tracking Scaling Policy:** Opt for the 'Target Tracking Scaling Policy' and select 'metric type' as CPU utilization, which will automatically create an alarm.
    
12. **Finalize Auto Scaling Group Creation:** Click on "Create Auto Scaling group" to complete the creation of the auto-scaling group.
    
13. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702966822212/956bc826-4955-4c52-bd98-844bd517969a.png align="center")
    
    **Auto-Scaling Group Successfully Created:** Confirm the successful creation of the auto-scaling group.
    

**Use Amazon CloudWatch to monitor the performance of the Auto Scaling group and the EC2 instances and troubleshoot any issues that arise.**

1. **Set Up Target Tracking Policy in Auto Scaling:** Configure a target tracking policy in auto scaling that generates two distinct alarms with unique conditions.
    

1. **Monitoring Activation for Auto-Scaling Group:** Once the alarms are in place, the monitoring of the specified metric for the Auto Scaling group begins. If the metric surpasses the set threshold, the alarm triggers and executes the predefined action.
    
2. **Enable Auto Scaling Group Metric Monitoring:** Navigate to the auto-scaling group previously created, access the "Monitoring" tab, and activate "Auto Scaling Group Metric."
    
3. **Create Alarm via CloudWatch Dashboard:** Alternatively, you can craft an alarm through the CloudWatch dashboard.
    
4. **Initiate Alarm Creation:** Click on the "Create Alarm" button to initiate the alarm setup.
    
5. **Select EC2 as the Target:** Navigate to the "EC2" section and choose 'By Auto Scaling Group.'
    
6. **Choose Metric for Monitoring:** Pick the metric you wish to monitor, searching for it by name.
    
7. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700753961289/b2698421-9b49-481a-b9d8-69ec8d99eb22.png?auto=compress,format&format=webp align="left")
    
    **Metric Selection and Alarm Setup:** Select the desired metric and proceed to create an alarm.
    
8. **Monitoring and Triggering:** Following alarm creation, continuous monitoring of the specified metric begins. If conditions are met, the configured action is triggered.
    
9. **Manage and Update Alarms:** Monitor the alarm status in the CloudWatch console. Manage and update the alarm settings as required to ensure optimal functionality.
    

**Use the AWS CLI to view the state of the Auto Scaling group and the EC2 instances and verify that the correct number of instances are running.**

1. **AWS CLI Installation:** Begin by installing the AWS CLI on your local machine using the following command:
    
    ```plaintext
     sudo apt-get install awscli
    ```
    
2. **AWS CLI Configuration:** Configure the AWS CLI to establish the necessary connections and settings.
    
3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700755685375/749f5d2a-50ec-474d-a1ef-fe8137f68992.png?auto=compress,format&format=webp align="left")
    
4. **Check Auto Scaling Group State:** Utilize the command below to inspect the current state of the Auto Scaling group and the instances it manages:
    
    ```plaintext
     aws autoscaling describe-auto-scaling-groups
    ```
    
5. **Auto Scaling Group Instance Overview:** Confirm that the Auto Scaling group has launched the specified number of instances (in this case, 2) by checking the desired capacity setting:
    
    ```plaintext
     aws ec2 describe-instances
    ```
    
6. **Instance Verification:** Validate that the correct number of instances are not only running but also in a healthy and operational state.
    

You can also do stress test to check for auto-scaling and to check that our trigger is functioning.

For that use commands:

```plaintext
sudo apt-get install stress
stress --cpu $(nproc) --timeout 3600s
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700756367014/4d4089a5-0093-414a-908a-abceaa52c737.png?auto=compress,format&format=webp align="left")