---
title: "Day 69 - Meta-Arguments in Terraform"
datePublished: Thu Jan 11 2024 14:48:32 GMT+0000 (Coordinated Universal Time)
cuid: clr9br9qs000409ld8x1n1ezy
slug: day-69-meta-arguments-in-terraform
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704984065783/b348be12-3d89-466b-b3c4-7dafecf9e440.jpeg

---

When you define a resource block in Terraform, by default, this specifies one resource that will be created. To manage several of the same resources, you can use either count or for\_each, which removes the need to write a separate block of code for each one. Using these options reduces overhead and makes your code neater.

count is what is known as a ‘meta-argument’ defined by the Terraform language. Meta-arguments help achieve certain requirements within the resource block.

## Count

The count meta-argument accepts a whole number and creates the number of instances of the resource specified.

When each instance is created, it has its own distinct infrastructure object associated with it, so each can be managed separately. When the configuration is applied, each object can be created, destroyed, or updated as appropriate.

eg.

```plaintext

terraform {

required_providers {

aws = {

source = "hashicorp/aws"

version = "~> 4.16"

}

}

required_version = ">= 1.2.0"

}

  

provider "aws" {

region = "us-east-1"

}

  

resource "aws_instance" "server" {

count = 4

  

ami = "ami-08c40ec9ead489470"

instance_type = "t2.micro"

  

tags = {

Name = "Server ${count.index}"

}

}

  

```

## for\_each

Like the count argument, the for\_each meta-argument creates multiple instances of a module or resource block. However, instead of specifying the number of resources, the for\_each meta-argument accepts a map or a set of strings. This is useful when multiple resources are required that have different values. Consider our Active directory groups example, with each group requiring a different owner.

```plaintext

terraform {

required_providers {

aws = {

source = "hashicorp/aws"

version = "~> 4.16"

}

}

required_version = ">= 1.2.0"

}

  

provider "aws" {

region = "us-east-1"

}

  

locals {

ami_ids = toset([

"ami-0b0dcb5067f052a63",

"ami-08c40ec9ead489470",

])

}

  

resource "aws_instance" "server" {

for_each = local.ami_ids

  

ami = each.key

instance_type = "t2.micro"

tags = {

Name = "Server ${each.key}"

}

}

  

Multiple key value iteration

locals {

ami_ids = {

"linux" :"ami-0b0dcb5067f052a63",

"ubuntu": "ami-08c40ec9ead489470",

}

}

  

resource "aws_instance" "server" {

for_each = local.ami_ids

  

ami = each.value

instance_type = "t2.micro"

  

tags = {

Name = "Server ${each.key}"

}

}

```

## Task-01

* Create the above Infrastructure as code and demonstrate the use of Count and for\_each.
    

### ***Meta argument- count***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703418436865/88db38af-7b43-43e1-bee3-658480a176b8.png?auto=compress,format&format=webp align="left")

The first part of the code is called the "terraform" block. Here, we say what version of Terraform we need and which providers are necessary. In this case, we're asking for the AWS provider, and we want it to come from the "hashicorp/aws" module with a version of 4.16 or higher.

Next, we have the "provider" block, where we set up the configuration for the AWS provider. In this example, we're specifying the region as ap-south-1.

After that, we get to the "aws\_instance" part, which is like a recipe for creating EC2 instances. We use the "count" thing to make four instances, each with a specific AMI and instance type. The "tags" part helps give each instance a unique name based on its count.

To get things started, run "terraform init" to set up the Terraform project.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703418439218/a69f6726-1328-4102-a652-50258aad065a.png?auto=compress,format&format=webp align="left")

Then, run "terraform plan".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703418442090/74ffb3b6-d59a-4230-9c44-2cb5b2ab73f0.png?auto=compress,format&format=webp align="left")

Finally, run "terraform apply" to actually create those four instances.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703418446382/bc7a598c-c7b3-46ca-a5ad-d02e319297c8.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703418447863/a012a67a-dab7-4dff-a04f-dc76a75cd950.png?auto=compress,format&format=webp align="left")

Congratulations! You've just made four new EC2 instances successfully.

### ***Meta argument - for\_each***

Start by creating a "locals" section to gather different AMI IDs for our instances. We use the "toset" function to change a list of names into a unique set.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703421281476/a8287328-b792-43f3-8f31-0d59991276dc.png?auto=compress,format&format=webp align="left")

In the "resource" part, set up the "aws\_instance" resource and use the "for\_each" method to make an instance for each AMI ID in our "ami\_ids" map. The "ami" is set to the current key (the AMI ID), and the "instance\_type" is set to "t2.micro." We also use the "tags" to give each instance a unique name based on the current key.

Run the Terraform apply command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703421283263/10d523df-46c7-47a6-9868-2b7ae3e7a9ad.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703421285823/b7f02bb4-3f86-45e1-a22c-2644a6d9ed52.png?auto=compress,format&format=webp align="left")

See two new instances created successfully, thanks to a simple process of going through different sets of information.

Now, let's use the "for\_each" method with a map containing various key-value pairs. This helps us create instances with different AMIs. We have a map with two pairs: the key is the AMI's name, and the value is its actual ID.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703421704123/aac96e05-7ba9-4bd1-8560-3e2967f982d2.png?auto=compress,format&format=webp align="left")

In the "resource" part, we use "each.value" to get the current value (AMI ID) and set the "ami" to it. Also, we use "each.key" to get the current key (AMI name) and use it to give a unique name to each instance using "tags."

Using "for\_each" with maps is handy to make several instances with different settings in just one block of code.

Run Terraform apply.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703421706328/323ba173-b9d3-4bf5-87be-a42fcfc69288.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703421710301/f4f6017d-b58a-4259-950e-220e52f47835.png?auto=compress,format&format=webp align="left")

Now, observe two new instances made using the 'for\_each' method with maps. It simplifies handling various sets of information.

### Write about meta-arguments and its use in Terraform***.***

Meta-arguments in Terraform are special settings that help decide how resources get handled—whether they get made, updated, or taken away. They're not just for one type of resource; instead, they let you set things up for all your resources in Terraform.

The main job of meta-arguments is to handle connections between resources. For example, with the "depends\_on" meta-argument, you can say that one resource needs another to be there first. This comes in handy when you're making resources that rely on others, like a load balancer needing an auto-scaling group.

Another way to use meta-arguments a lot is to control the order in which resources are made. The "count" and "for\_each" meta-arguments help make many instances of a resource. Also, the "lifecycle" meta-argument helps decide when resources get made, updated, or taken away.

The "provider" meta-argument is important too. It says which provider manages a specific resource. Providers are like plugins that Terraform uses to manage resources, such as AWS, Google Cloud, or Azure.

In short, meta-arguments are a handy feature in Terraform, letting you finely control how resources behave. Using these settings well helps Terraform users build stronger and more flexible infrastructure through code.