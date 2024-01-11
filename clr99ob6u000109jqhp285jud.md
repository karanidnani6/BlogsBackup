---
title: "Day 65 - Working with Terraform Resources"
datePublished: Thu Jan 11 2024 13:50:15 GMT+0000 (Coordinated Universal Time)
cuid: clr99ob6u000109jqhp285jud
slug: day-65-working-with-terraform-resources
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704980629882/8e7a884b-dd9a-4c1f-aa58-5e1e46e5bdc1.png

---

## **Understanding Terraform Resources**

A resource in Terraform represents a component of your infrastructure, such as a physical server, a virtual machine, a DNS record, or an S3 bucket. Resources have attributes that define their properties and behaviors, such as the size and location of a virtual machine or the domain name of a DNS record.

When you define a resource in Terraform, you specify the type of resource, a unique name for the resource, and the attributes that define the resource. Terraform uses the resource block to define resources in your Terraform configuration.

## Task 1: Create a security group

To allow traffic to the EC2 instance, you need to create a security group. Follow these steps:

In your [**main.tf**](https://pmgoriya.hashnode.dev/working-with-terraform-resources#heading-task-1-create-a-security-group) file, add the following code to create a security group:

```plaintext
resource "aws_security_group" "web_server" {
  name_prefix = "web-server-sg"

  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}
```

<mark>Note:</mark> Where to find the references for these codes? The answer is in the Terraform registry.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703074894015/49aa820b-0307-404f-87bb-28fd80dcb8af.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703074903985/f3969b5c-d909-46ee-9087-d8316406d881.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703074907726/b99326e6-0c73-4c20-a05a-2cad39f8c684.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703074915324/dd8d6b07-3dcf-49b0-a94c-9649d561ab2c.png?auto=compress,format&format=webp align="left")

## Task 2: Create an EC2 instance

Now you can create an EC2 instance with Terraform. Follow these steps:

In your [**main.tf**](https://pmgoriya.hashnode.dev/working-with-terraform-resources#heading-task-1-create-a-security-group) file, add the following code to create an EC2 instance:

```plaintext
resource "aws_instance" "web_server" {
  ami           = "ami-0557a15b87f6559cf"
  instance_type = "t2.micro"
  key_name      = "my-key-pair"
  security_groups = [
    aws_security_group.web_server.name
  ]

  user_data = <<-EOF
              #!/bin/bash
              echo "<html><body><h1>Welcome to my website!</h1></body></html>" > index.html
              nohup python3 -m http.server80 &
  EOF
}

///if you use python2 version then use-

   nohup python -m SimpleHTTPServer 80 &
```

Note: Replace the ami and key\_name values with your own.

We use the **user\_data** parameter to execute a Bash script that sets up a basic web server using Python's SimpleHTTPServer.

* The `<<-EOF` and `EOF` syntax is a way to create a multi-line string in Terraform. It's a heredoc syntax, allowing you to include multiline strings without the need for excessive escaping.
    
* `#!/bin/bash`: This is known as a shebang line, specifying that the script should be executed using the Bash shell.
    
* `echo "<html><body><h1>Welcome to my website!</h1></body></html>" > index.html`: This line creates an HTML file named `index.html` with a simple "Welcome to my website!" message. The `echo` command is used to write the HTML content into the file.
    
* `nohup python3 -m http.server 80 &`: This line starts a simple HTTP server using Python. It uses `nohup` to run the server in the background and allows the script to continue executing. The server listens on port 80, serving the contents of the current directory.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703079527485/2ef77897-1762-469f-a9fc-053ca7056506.png?auto=compress,format&format=webp align="left")
    
    Upon launching an EC2 instance using Terraform and incorporating this `user_data` script, a web server will be configured to serve the content of the `index.html` file on port 80. To access the website, simply navigate to the public IP address of your instance using a web browser.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703079544436/b39873e0-721b-4cdc-9210-cf9b6c45b005.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703079547626/160d2f51-d7f9-40de-9c36-a22729e52898.png?auto=compress,format&format=webp align="left")

Execute `terraform apply` to generate the EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703079536787/6771afeb-a30d-4845-b3f8-f4c30404f51c.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703079541257/765c89ec-00d1-4466-8536-7672b3c1b2e3.png?auto=compress,format&format=webp align="left")

The EC2 instance has been successfully generated.

Retrieve the public IP address of the instance created through Terraform.

Navigate to the public IP address of your instance in a web browser to view the webpage.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703079557484/d16bdbd7-7ea1-4f33-9038-51c6c230d386.png?auto=compress,format&format=webp align="left")