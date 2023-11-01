---
title: "#Day44:Relational Database Service in AWS"
datePublished: Wed Nov 01 2023 08:09:39 GMT+0000 (Coordinated Universal Time)
cuid: clofh8t6n000908msehx9965h
slug: day44relational-database-service-in-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698825451482/ffe62b72-814f-4459-92cc-d855f7265826.jpeg
tags: aws-rds, 90daysofdevops

---

Amazon Relational Database Service (Amazon RDS) is a managed relational database service provided by Amazon Web Services (AWS). It makes it easier to set up, operate, and scale a relational database in the cloud. Amazon RDS supports multiple database engines, including MySQL, PostgreSQL, MariaDB, Oracle, and Microsoft SQL Server.

Here are some key features and benefits of Amazon RDS:

1. **Managed Service:** Amazon RDS handles routine database tasks such as provisioning, patching, backup, recovery, and scaling, allowing you to focus on your application and data.
    
2. **Scalability:** You can easily scale your database instance vertically by changing the instance type or horizontally by adding read replicas to handle read traffic.
    
3. **High Availability:** Amazon RDS offers automated backups and automated software patching. It also supports Multi-AZ deployments, which provide high availability and failover support for DB instances.
    
4. **Security:** RDS provides security features such as network isolation using Amazon VPC, encryption at rest using AWS Key Management Service (KMS), and encryption in transit using SSL.
    
5. **Compatibility:** RDS supports multiple database engines, allowing you to choose the one that best fits your application requirements.
    
6. **Monitoring and Metrics:** Amazon RDS provides Amazon CloudWatch integration, enabling you to monitor your databases and set up alarms for specific events.
    
7. **Automated Backups:** RDS automatically backs up your database and maintains these backups for a user-defined retention period. You can also manually create backups whenever needed.
    
8. **Maintenance:** RDS handles routine database maintenance tasks, including hardware provisioning, database setup, patching, and backups, freeing you from these administrative tasks.
    

By using Amazon RDS, you can focus on building applications without worrying about the complexities of managing a relational database infrastructure.

Certainly, I can provide you with a step-by-step guide to achieve the tasks you described. Before you begin, make sure you have an AWS account and you're logged in to the AWS Management Console.

### Task 1: Create a Free Tier RDS Instance of MySQL

1. **Go to Amazon RDS:**
    
    * Open the AWS Management Console.
        
    * Go to the Amazon RDS dashboard.
        
2. **Launch a DB Instance:**
    
    * Click on "Create database."
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698826060609/ddcd3693-9ae2-4b7f-9015-663bd3a22d4e.png align="center")
        
    * Select "Standard Create."
        
    * Choose "MySQL" as the engine and select the version.
        
    * Under Templates, select "Free tier."
        
    * Configure your DB instance details, username, and password.
        
    * Click on "Create database."
        

### Task 2: Create an EC2 Instance

1. **Go to Amazon EC2:**
    
    * From the AWS Management Console, go to the EC2 dashboard.
        
2. **Launch an EC2 Instance:**
    
    * Click on "Launch Instance."
        
    * Choose an Amazon Machine Image (AMI).
        
    * Select an instance type eligible for the free tier.
        
    * Configure the instance details, add storage, and configure security group rules.
        
    * Launch the instance.
        

### Task 3: Create an IAM Role with RDS Access

1. **Go to AWS IAM:**
    
    * From the AWS Management Console, go to the IAM dashboard.
        
2. **Create a New Role:**
    
    * Click on "Roles" in the left menu.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698826104920/76fd7c05-09cc-4600-96da-07ad933617b9.png align="center")
        
    * Click on "Create role."
        
    * Choose the service that will use this role (EC2 in this case).
        
    * Attach the policy that grants RDS access (e.g., `AmazonRDSReadOnlyAccess`).
        
    * Review and create the role.
        

### Task 4: Assign the Role to EC2 Instance

1. **Assign IAM Role to EC2:**
    
    * Go to the EC2 dashboard.
        
    * Select your EC2 instance.
        
    * Click on "Actions" &gt; "Security" &gt; "Modify IAM Role."
        
    * Choose the IAM role you created earlier.
        
    * Save the changes.
        

### Task 5: Connect EC2 Instance to RDS

1. **SSH into EC2 Instance:**
    
    * Use an SSH client to connect to your EC2 instance.
        
2. **Install MySQL Client:**
    
    * Run the following command to install the MySQL client:
        
        ```plaintext
        sudo apt-get update
        sudo apt-get install mysql-client
        ```
        
3. **Get RDS Endpoint and Credentials:**
    
    * Go to the RDS dashboard.
        
    * Click on your RDS instance to get the endpoint (Host) and database credentials (Username, Password).
        
4. **Connect to RDS from EC2 using MySQL Client:**
    
    * Run the following command, replacing `<endpoint>` with your RDS endpoint, `<username>` with your RDS username, and `<password>` with your RDS password:
        
        ```plaintext
        mysql -h <endpoint> -u <username> -p
        ```
        
    * Enter your password when prompted to connect to the MySQL database on RDS.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695265169325/0f598473-3235-4da5-bca9-1da7deaff0c7.png?auto=compress,format&format=webp align="left")
        

Now, you've successfully created an RDS instance, an EC2 instance, an IAM role with RDS access, assigned the role to EC2, and connected your EC2 instance to the RDS instance using a MySQL client. Remember to replace placeholders like `<endpoint>`, `<username>`, and `<password>` with your actual RDS endpoint and credentials.