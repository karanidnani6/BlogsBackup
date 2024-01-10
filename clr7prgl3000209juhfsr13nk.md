---
title: "Day 63 - Terraform Variables"
datePublished: Wed Jan 10 2024 11:45:03 GMT+0000 (Coordinated Universal Time)
cuid: clr7prgl3000209juhfsr13nk
slug: day-63-terraform-variables
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704874349340/3f416df6-281b-4d3b-999f-f792b50a287f.jpeg

---

variables in Terraform are quite important, as you need to hold values of names of instance, configs , etc.

We can create a [variables.tf](http://variables.tf) file which will hold all the variables.

```plaintext
variable "filename" {
default = "/home/ubuntu/terrform-tutorials/terraform-variables/demo-var.txt"
}
```

```plaintext
variable "content" {
default = "This is coming from a variable which was updated"
}
```

These variables can be accessed by var object in [main.tf](http://main.tf) This way, we keep everything tidy and have a central place to manage our variables for a smoother and more scalable Terraform setup.

## Task-01

* Create a local file using Terraform Hint:
    

Create a [**variable.tf**](http://variable.tf/) file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702967010275/7de491e2-c3e5-4f38-aaaa-862703bdd27e.png?auto=compress,format&format=webp align="left")

In this file, we set up two variables. One called `filename` stores the path where the local file will be created, and the other, `content`, holds the text that will be written to the local file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702967017774/14a9bd06-544d-43fb-89ed-b26b60eb04e0.png?auto=compress,format&format=webp align="left")

Create a [**main.tf**](http://variable.tf/) file

In this file, we use Terraform to create a resource called `local_file` named "devops." This resource is like a set of instructions for Terraform to follow. It tells Terraform to create a file on your computer with the name and content specified by the `filename` and `content` variables.

Here's a breakdown:

* `resource "local_file" "devops"`: We're telling Terraform to create a local file resource named "devops."
    
* `filename = var.filename`: This sets the filename of the local file to the value of the `filename` variable.
    
* `content = var.content`: This sets the content of the local file to the value of the `content` variable.
    

After making these files, follow these steps:

1. **Get Ready:** Start by setting things up:
    
    ```plaintext
     terraform init
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702967028907/2437739a-8c82-47f7-878e-0e9efc7bcf0e.png?auto=compress,format&format=webp align="left")
    
2. **Preview Changes:** Check out what Terraform plans to do:
    
    ```plaintext
     terraform plan
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702967034843/7f16b7a8-23de-4cbc-8e28-0d0bfd521ff1.png?auto=compress,format&format=webp align="left")
    
3. **Make It Happen:** If the plan looks good, go ahead:
    
    ```plaintext
     terraform apply
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702967038881/27c33ce2-6224-4792-8015-780f21e6b6ac.png?auto=compress,format&format=webp align="left")
    
    Confirm by typing "yes."
    
4. **See the New File:** After applying, make sure the file is there:
    
    ```plaintext
     ls /home/ubuntu/terraform/terraform-variable/
    ```
    
    Look for a file called `var-demo.txt` in that spot.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702967047588/56a00c03-1c04-419a-8ba9-2d439f642c5b.png?auto=compress,format&format=webp align="left")

## Task-02

* Use terraform to demonstrate usage of List, Set and Object datatypes
    

### ***Map:***

A map is like a labelled collection of values, where each value is identified by a unique string label. It is like dictionary in programming languages i.e having key-value pair.

[**variables.tf**](http://variables.tf/)**:**

```plaintext
# variables.tf

variable "content_map" {
  type    = map
  default = {
    "content1" = "this is cool content1"
    "content2" = "this is cooler content2"
  }
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702967809767/dfeacf0e-b926-4ace-b27f-795ab63eed18.png?auto=compress,format&format=webp align="left")

This part introduces a Terraform variable called `content_map`.

* `variable "content_map"`: Declares a variable named `content_map`. This variable is a map, which is a way of organizing data with labels.
    
* `type = map`: Specifies that the variable is of type map. In Terraform, a map is a structure that holds key-value pairs.
    
* `default = { "content1" = "this is cool content1" "content2" = "this is cooler content2" }`: Sets a default value for the `content_map` variable. The default value is a map with two key-value pairs. The keys are "content1" and "content2," and their corresponding values are the strings "this is cool content1" and "this is cooler content2."
    

Now, let's explore how this variable is utilized in the Terraform configuration:

[**main.tf**](http://variables.tf/)**:**

```plaintext
# main.tf

resource "local_file" "devops" {
  filename = "/home/ubuntu/terraform/variables/demo.txt"
  content  = var.content_map["content1"]
}

resource "local_file" "devops_var" {
  filename = var.filename
  content  = var.content_map["content2"]
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702968577808/9df9749e-9185-49f9-8150-3e5180721d97.png?auto=compress,format&format=webp align="left")

In this part, the `content_map` variable is applied within two `local_file` resources:

* `resource "local_file" "devops"`: Declares a resource of type `local_file` with the name "devops."
    
    * `filename = "/home/ubuntu/terraform/terraform-variable/type-map/demo.txt"`: Specifies the filename for the local file, defining a specific path and filename.
        
    * `content = var.content_map["content1"]`: Sets the content of the local file to the value associated with the key "content1" in the `content_map` variable. In this case, it will be "this is cool content1" based on the default value set earlier.
        
* `resource "local_file" "devops_var"`: Declares a second resource of type `local_file` with the name "devops\_var."
    
    * `filename = var.filename`: Specifies the filename for this new local file, taking its value from the `filename` variable.
        
    * `content = var.content_map["content2"]`: Sets the content of this local file to the value associated with the key "content2" in the `content_map` variable. In this case, it will be "this is cooler content2" based on the default value set earlier.
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702968598354/311a0fbb-4aad-431f-96bd-de4014677057.png?auto=compress,format&format=webp align="left")
        

When you execute Terraform and apply this configuration, it will generate two local files. The first, named `demo.txt` in the specified path, will have the content "this is cool content1." The second file will use a filename specified by the `filename` variable and have the content "this is cooler content2."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702968610515/73769a1a-2682-4ec1-b9ce-e1e90ec751b7.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702968617039/3df7f1ab-54d0-4861-865b-336a50c1e04f.png?auto=compress,format&format=webp align="left")

### ***List:***

A list is like a well-ordered group of values, all of the same type. To declare a list variable, specify the list type and indicate the type of elements within the list. Here's an illustration:

[**variables.tf**](http://variables.tf/)**:**

```plaintext
# variables.tf

variable "file_list" {
  type    = list
  default = [
    "/home/ubuntu/terraform/variables/file1.txt",
    "/home/ubuntu/terraform/variables/file2.txt"
  ]
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702969666828/e74c4843-8517-4a52-aeba-8dee00bb0911.png?auto=compress,format&format=webp align="left")

In this snippet, we define a variable named "file\_list" as a list of strings with a default value containing file paths.

* `variable "file_list"`: Declares a variable named "file\_list" as a list. This variable represents an ordered collection of values.
    
* `type = list`: Specifies that the variable is of type list. In Terraform, a list is a sequential collection of elements.
    
* `default = ["/home/ubuntu/terraform/terraform-variable/type-map/file1.txt", "/home/ubuntu/terraform/terraform-variable/type-map/file2.txt"]`: Sets a default value for the "file\_list" variable. The default value is a list containing two strings representing file paths.
    

Now, let's explore how this variable is utilized in the Terraform configuration:

[**main.tf**](http://variables.tf/)**:**

```plaintext
# main.tf

resource "local_file" "devops" {
  filename = var.file_list[0]
  content  = var.content_map["content1"]
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702969680693/c459a826-b3d6-4a18-97ae-33b399039bc2.png?auto=compress,format&format=webp align="left")

In this example, the "file\_list" variable is applied to set the filename parameter of a `local_file` resource.

* `resource "local_file" "devops"`: Declares a resource of type `local_file` with the name "devops."
    
    * `filename = var.file_list[0]`: Sets the filename of the local file to the first element of the "file\_list" variable using square bracket notation and `var.file_list[0]` syntax.
        
    * `content = var.content_map["content1"]`: Sets the content of the local file to the value associated with the key "content1" in the `content_map` variable.
        

After defining these variables and resources, you can run the following Terraform commands:

```plaintext
terraform init
terraform plan
terraform apply
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702969753297/3b0e3257-a832-45a9-8a5b-2d2edd6b4560.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702969763419/75ce68c8-f23e-46fc-b9af-5fa026a15d7b.png?auto=compress,format&format=webp align="left")

Upon applying, check for the creation of two files with different content based on the specified paths and the content associated with the variables in your Terraform configuration.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702969772071/1fb5df54-ed50-47d1-9652-fb5d4d9e043c.png?auto=compress,format&format=webp align="left")

### ***Object:***

**Object:** An object is like a container that can hold different types of values, making it distinct from maps and lists. It's a collection of named attributes, each with its own type.

[**variables.tf**](http://variables.tf/)**:**

```plaintext
# variables.tf

variable "aws_ec2_object" {
  type = object({
    name      = string
    instances = number
    keys      = list(string)
    ami       = string
  })

  default = {
    name      = "test-ec2-instance"
    instances = 4
    keys      = ["key1.pem", "key2.pem"]
    ami       = "ubuntu-bfde24"
  }
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702970499606/953ab663-99c9-467c-9338-3d9885636332.png?auto=compress,format&format=webp align="left")

In this section, we define a Terraform variable named `aws_ec2_object` as an object with a default value. The object includes properties for configuring an EC2 instance.

* `variable "aws_ec2_object"`: Declares a variable named `aws_ec2_object` as an object. This variable represents a structured collection of attributes.
    
* `type = object({...})`: Specifies the type of the variable, defining its structure with named attributes and their respective types.
    
* `default = {...}`: Sets a default value for the `aws_ec2_object` variable. The default value is an object with properties like "name," "instances," "keys," and "ami," each configured with specific values.
    

[**main.tf**](http://variables.tf/)**:**

```plaintext
# main.tf

output "aws_ec2_instances" {
  value = var.aws_ec2_object.ami
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702970485688/59732756-319b-4e6c-b694-4128f2a74362.png?auto=compress,format&format=webp align="left")

In the [`main.tf`](http://variables.tf/) file, we use an output block to display the value of the "ami" property in the Terraform output after applying the configuration.

* `output "aws_ec2_instances"`: Declares an output named "aws\_ec2\_instances."
    
    * `value =` [`var.aws`](http://variables.tf/)`_ec2_object.ami`: Specifies that the output should display the value of the "ami" property from the `aws_ec2_object` variable.
        

After defining these variables and outputs, you can run the following Terraform commands:

```plaintext
terraform init
terraform plan
terraform apply
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702970468994/a82f0ff8-321d-4515-a716-92218e73e4ba.png?auto=compress,format&format=webp align="left")

Upon applying, you will see the output displaying the value of the "ami" property in the Terraform output.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702970452385/3dfccd43-290b-4e35-b4eb-d306031df916.png?auto=compress,format&format=webp align="left")

### ***Set:***

A set is like a bag of unique values, where the order doesn't matter. To declare a set variable, use the set type and specify the type of elements in the set.

[**variables.tf**](http://variables.tf/)**:**

```plaintext
# variables.tf

variable "security_groups" {
  type    = set(string)
  default = ["sg-12345678", "sg-87654321"]
}
```

In this snippet, we define a Terraform variable named "security\_groups" as a set of strings with a default value.

* `variable "security_groups"`: Declares a variable named "security\_groups" as a set. This variable represents an unordered collection of unique values of the same type.
    
* `type = set(string)`: Specifies that the variable is of type set, and the elements within the set are of type string.
    
* `default = ["sg-12345678", "sg-87654321"]`: Sets a default value for the "security\_groups" variable. The default value is a set containing two strings representing security group IDs.
    

Now, you can use this variable in your Terraform configuration to reference the set of security group IDs.

### \*\*

Refreshing Terraform State:\*\*

Using `terraform refresh` is a command in Terraform that helps you synchronize the state of your resources with the configuration file. When you run `terraform refresh`, it retrieves the current state of the resources defined in your configuration and updates the Terraform state file to accurately reflect that state.

**Command Usage:**

```plaintext
terraform refresh
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702970440043/6d8d2610-44f5-405e-9a95-f40511d9935f.png?auto=compress,format&format=webp align="left")

**Explanation:**

Running `terraform refresh` serves to update the state file without making any actual changes to your resources. It ensures that the Terraform state file is in sync with the real-world state of your infrastructure.