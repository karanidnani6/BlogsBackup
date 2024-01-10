---
title: "Day 60 - Terraform"
datePublished: Wed Jan 10 2024 07:21:51 GMT+0000 (Coordinated Universal Time)
cuid: clr7gcywd000308l68p4ugilr
slug: day-60-terraform
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704867344277/c442a934-43a4-4a11-ba64-d4c535fb8875.png

---

Terraform is an open-source Infrastructure as Code (IaC) tool developed by HashiCorp. It enables users to define and provision infrastructure using a declarative configuration language. Terraform automates the creation, modification, and management of infrastructure resources across various cloud providers and on-premises environments.

## Task 1:

Install Terraform on your system

Create an EC2 instance

SSH into your Ubuntu EC2 instance

* Go to the official Terraform website at [**https://www.terraform.io/downloads.html**](https://www.terraform.io/downloads.html).
    
* Choose Linux as your operating system and Ubuntu as your package manager.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702814805483/7d514919-4f6f-4ad4-8216-bf9f3dc97918.png?auto=compress,format&format=webp align="left")
    
    Copy and paste the following three commands into your terminal.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702814810592/fd510a84-b816-4a7a-8b30-0ad2ba2ea88d.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702814854609/828800bc-16ff-4178-81d5-23c3a175fa24.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702814858223/dc445fff-dcc8-4fd4-b886-6807149fb355.png?auto=compress,format&format=webp align="left")

Verify that Terraform is installed correctly by running the following command:  
`terraform --version`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702814862270/15d69293-8fe5-4322-bfb6-d8814270a383.png?auto=compress,format&format=webp align="left")

### Task 2: Answer below questions

1. **Why we use Terraform?**
    
    * Terraform provides a consistent and scalable way to manage infrastructure.
        
    * It enables version-controlled infrastructure, facilitating collaboration and code review.
        
    * Automation reduces the risk of errors in manual provisioning and ensures repeatability.
        
2. **What is Infrastructure as Code (IaC)?**
    
    * IaC is a concept where infrastructure configurations are defined and managed as code.
        
    * It allows for versioning, collaboration, and automation in infrastructure provisioning.
        
    * Changes to infrastructure can be tracked, tested, and deployed in a controlled manner.
        
3. **What is Resource?**
    
    * In Terraform, a resource is a declarative representation of an infrastructure component, such as a virtual machine, network, or database.
        
    * Resources are defined in Terraform configuration files and managed by Terraform during the provisioning process.
        
4. **What is Provider?**
    
    * A provider in Terraform is a plugin that defines and manages resources in a specific infrastructure platform.
        
    * Examples include AWS, Azure, Google Cloud, and many others. Providers allow Terraform to interact with and manage resources on the chosen platform.
        
5. **What is State file in Terraform? What’s the importance of it?**
    
    * The state file in Terraform is a JSON file that keeps track of the resources managed by Terraform and their current state.
        
    * It records the mapping between the declared configuration and the real-world infrastructure.
        
    * The state file is crucial for Terraform to understand what changes need to be applied during subsequent runs.
        
6. **What is Desired and Current State?**
    
    * **Desired State:** The state in which you declare the desired configuration of your infrastructure using Terraform code. It defines how you want your infrastructure to be.
        
    * **Current State:** The actual state of your infrastructure as tracked by Terraform. It reflects the real-world status of resources after applying the Terraform configuration.
        

Understanding the difference between desired and current states allows Terraform to determine the necessary changes required to align the infrastructure with the declared configuration.

In summary, Terraform simplifies and automates infrastructure management through IaC, enabling efficient collaboration, version control, and consistent provisioning across various cloud platforms.