---
title: "Day 70 - Terraform Modules"
datePublished: Thu Jan 11 2024 14:51:06 GMT+0000 (Coordinated Universal Time)
cuid: clr9buk2d000309l1fp9s2iby
slug: day-70-terraform-modules
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704984547843/eba3601e-714f-40b1-b06e-c29a3e57232b.png

---

* Modules are containers for multiple resources that are used together. A module consists of a collection of .tf and/or .tf.json files kept together in a directory
    
* A module can call other modules, which lets you include the child module's resources into the configuration in a concise way.
    
* Modules can also be called multiple times, either within the same configuration or in separate configurations, allowing resource configurations to be packaged and re-used.
    

### Below is the format on how to use modules:

```plaintext
# Creating a AWS EC2 Instance
resource "aws_instance" "server-instance" {
  # Define number of instance
  instance_count = var.number_of_instances
 
  # Instance Configuration
  ami                    = var.ami
  instance_type          = var.instance_type
  subnet_id              = var.subnet_id
  vpc_security_group_ids = var.security_group
 
  # Instance Tagsid
  tags = {
    Name = "${var.instance_name}"
  }
}
```

```plaintext
# Server Module Variables
variable "number_of_instances" {
  description = "Number of Instances to Create"
  type        = number
  default     = 1
}
 
variable "instance_name" {
  description = "Instance Name"
}
 
variable "ami" {
  description = "AMI ID"
  default     = "ami-xxxx"
}
 
variable "instance_type" {
  description = "Instance Type"
}
 
variable "subnet_id" {
  description = "Subnet ID"
}
 
variable "security_group" {
  description = "Security Group"
  type        = list(any)
}
```

```plaintext
# Server Module Output
output "server_id" {
  description = "Server ID"
  value       = aws_instance.server-instance.id
}

```

## Task-01

Explain the below in your own words

* In Terraform, modules are containers that organize and encapsulate resources together, allowing for better organization and reuse of configurations. A module typically consists of a collection of `.tf` or `.tf.json` files within a directory. It can be used to define and manage related resources, making it easier to manage and scale infrastructure.
    
    **Difference between Root Module and Child Module:**
    
    1. **Root Module:**
        
        * The root module is the main entry point of a Terraform configuration.
            
        * It's the top-level configuration that usually resides in its own directory.
            
        * In a Terraform execution, the root module is the starting point where the configuration is loaded.
            
        * It may include child modules to organize and manage resources effectively.
            
        * Variables defined in the root module can be passed to child modules.
            
    2. **Child Module:**
        
        * A child module is a module that is called or invoked by another module (possibly the root module).
            
        * It encapsulates a set of related resources and configurations.
            
        * It promotes modularity and reusability by allowing configurations to be packaged and reused.
            
        * A child module can be called multiple times, either within the same configuration or across different configurations.
            
        * Variables specific to a child module are defined within the module, and it can use variables passed from the parent (root) module.
            
    
    **Modules vs. Namespaces:**
    
    1. **Modules:**
        
        * Modules in Terraform are organizational units that group resources together.
            
        * They encapsulate related configurations and resources, promoting modularity and reusability.
            
        * Modules help in organizing code and facilitate the creation of scalable and maintainable infrastructure.
            
    2. **Namespaces:**
        
        * Namespaces, in the context of Terraform, refer to the way resources are named and organized within a module.
            
        * Each module has its own namespace, ensuring that resource names within the module are unique.
            
        * Namespaces are crucial for preventing naming conflicts, especially when using modules in different parts of a larger infrastructure.
            
    
    **Justification for Modules and Namespaces Not Being the Same:**
    
    * **No, Modules and Namespaces are not the same:**
        
        * Modules refer to the organizational structure and encapsulation of resources.
            
        * Namespaces refer to the unique identifiers for resources within a module to avoid naming conflicts.
            
        * While modules use namespaces to ensure uniqueness within their scope, the concept of modules extends beyond just the naming aspect. Modules are broader organizational units that encapsulate configurations, whereas namespaces are more about ensuring uniqueness and avoiding naming clashes within a module.