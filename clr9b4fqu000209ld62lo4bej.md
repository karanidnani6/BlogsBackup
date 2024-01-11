---
title: "Day 71 - Let's prepare for some interview questions of Terraform"
datePublished: Thu Jan 11 2024 14:30:47 GMT+0000 (Coordinated Universal Time)
cuid: clr9b4fqu000209ld62lo4bej
slug: day-71-lets-prepare-for-some-interview-questions-of-terraform
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704983326322/701d4d3e-e043-4cd7-873a-54da330ce0ff.png

---

1. **What is Terraform and how is it different from other IaaC tools?**
    
    * Terraform is an open-source Infrastructure as Code (IaC) tool developed by HashiCorp. It allows users to define and provision infrastructure using a declarative configuration language. Terraform supports multiple cloud providers and on-premises infrastructure.
        
    * Unlike some other IaC tools, Terraform uses a declarative approach, meaning you specify the desired end state of your infrastructure rather than scripting the steps to reach that state. Terraform also has a strong focus on providing a unified workflow for managing infrastructure across various providers.
        
2. **How do you call a** [**main.tf**](http://main.tf) **module?**
    
    * In Terraform, the [`main.tf`](http://main.tf) file is typically the default configuration file that is automatically loaded. Therefore, you don't need to explicitly call it. When you run `terraform apply` or `terraform init`, Terraform automatically looks for the [`main.tf`](http://main.tf) file in the current directory.
        
3. **What exactly is Sentinel? Can you provide a few examples where we can use Sentinel policies?**
    
    * Sentinel is a policy as code framework developed by HashiCorp. It allows you to define and enforce policies on the infrastructure provisioned by Terraform. Examples of Sentinel policies include:
        
        * Enforcing naming conventions for resources.
            
        * Restricting the use of specific cloud regions.
            
        * Ensuring the use of approved machine image IDs.
            
        * Enforcing security controls, such as requiring encryption for certain resources.
            
4. **You have a Terraform configuration file that defines an infrastructure deployment. However, there are multiple instances of the same resource that need to be created. How would you modify the configuration file to achieve this?**
    
    * You can use the `count` or `for_each` argument to create multiple instances of the same resource. For example:
        
        ```plaintext
        hclCopy coderesource "aws_instance" "example" {
          count = 3
          ami   = "ami-0c55b159cbfafe1f0"
          instance_type = "t2.micro"
        }
        ```
        
5. **You want to know from which paths Terraform is loading providers referenced in your Terraform configuration (\*.tf files). You need to enable debug messages to find this out. Which of the following would achieve this?**
    
    * A. Set the environment variable `TF_LOG=TRACE`
        
6. **Below command will destroy everything that is being created in the infrastructure. Tell us how would you save any particular resource while destroying the complete infrastructure.**
    
    * You can use the `-target` option to specify a specific resource to destroy. For example:
        
        ```plaintext
        bashCopy codeterraform destroy -target=aws_instance.example
        ```
        
7. **Which module is used to store .tfstate file in S3?**
    
    * The `backend "s3"` module is used to store the `.tfstate` file in an S3 bucket.
        
8. **How do you manage sensitive data in Terraform, such as API keys or passwords?**
    
    * Terraform provides the `sensitive` argument that can be applied to sensitive data. Additionally, you can use environment variables or external systems (like HashiCorp Vault) to manage and retrieve sensitive information securely.
        
9. **You are working on a Terraform project that needs to provision an S3 bucket, and a user with read and write access to the bucket. What resources would you use to accomplish this, and how would you configure them?**
    
    * You would use the `aws_s3_bucket` resource to create the S3 bucket and the `aws_iam_user` and `aws_iam_user_policy_attachment` resources to create the user and attach a policy granting read and write access to the S3 bucket.
        
10. **Who maintains Terraform providers?**
    
    * Terraform providers are maintained by their respective vendors. For example, the AWS provider is maintained by AWS, and the Azure provider is maintained by Microsoft.
        
11. **How can we export data from one module to another?**
    
    * You can use outputs to export data from one module and use it in another. In the module where you want to export data:
        
        ```plaintext
        hclCopy codeoutput "example_output" {
          value = aws_instance.example.id
        }
        ```
        
        In the module where you want to use the exported data:
        
        ```plaintext
        hclCopy codemodule "example_module" {
          source = "./example_module"
        }
        
        resource "aws_instance" "example" {
          ami = "ami-0c55b159cbfafe1f0"
          // other configurations
        }
        
        data "external" "example_external" {
          program = ["echo", module.example_module.example_output]
        }
        ```
        
        In this example, the `example_output` from the first module is accessed in the second module using `module.example_module.example_output`.