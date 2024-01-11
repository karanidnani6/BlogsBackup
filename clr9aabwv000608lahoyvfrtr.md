---
title: "Day 66 - Terraform Hands-on Project"
datePublished: Thu Jan 11 2024 14:07:22 GMT+0000 (Coordinated Universal Time)
cuid: clr9aabwv000608lahoyvfrtr
slug: day-66-terraform-hands-on-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704981062387/a4ac1272-a7f8-469c-9546-5e8d8e5ac726.jpeg

---

## Task:

* Create a VPC (Virtual Private Cloud) with CIDR block 10.0.0.0/16
    
* Create a public subnet with CIDR block 10.0.1.0/24 in the above VPC.
    
* Create a private subnet with CIDR block 10.0.2.0/24 in the above VPC.
    
* Create an Internet Gateway (IGW) and attach it to the VPC.
    
* Create a route table for the public subnet and associate it with the public subnet. This route table should have a route to the Internet Gateway.
    
* Launch an EC2 instance in the public subnet with the following details:
    
* AMI: ami-0557a15b87f6559cf
    
* Instance type: t2.micro
    
* Security group: Allow SSH access from anywhere
    
* User data: Use a shell script to install Apache and host a simple website
    
* Create an Elastic IP and associate it with the EC2 instance.
    
* Open the website URL in a browser to verify that the website is hosted successfully.
    

### ***1.Create a VPC (Virtual Private Cloud) with CIDR block 10.0.0.0/16***

Establish a Virtual Private Cloud (VPC) using the CIDR block 10.0.0.0/16 with the following Terraform configuration:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165142926/2ded0d75-d0c4-4c4a-95eb-fc9986bfdbdb.png?auto=compress,format&format=webp align="left")

```plaintext
resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"

  tags = {
    Name = "main"
  }
}
```

This configuration will generate a new VPC in your AWS account, featuring the designated CIDR block and labeled as "main."

The specified Terraform block outlines the required version of Terraform to execute this setup. In this instance, it mandates that the Terraform version should be &gt;= 1.2.0. Additionally, include the region where you desire your instances to be located.

Execute the `terraform init` command to set up the working directory and download the necessary providers. Subsequently, utilize `terraform apply` to instantiate the VPC in your AWS account.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165146152/4797e6c8-6ed0-4a88-8b6a-363991654598.png?auto=compress,format&format=webp align="left")

Verify the successful creation of the new VPC named 'main' by accessing the VPC console.

### ***2\. Create a public subnet with CIDR block 10.0.1.0/24 in the above VPC.***

To generate a public subnet within the previously established VPC, employing the CIDR block 10.0.1.0/24, utilize the subsequent Terraform code:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165151728/7de91f1f-df7d-439f-baf5-6fb14c33b9f6.png?auto=compress,format&format=webp align="left")

```plaintext
resource "aws_subnet" "public_subnet" {
  vpc_id     = aws_vpc.main.id
  cidr_block = "10.0.1.0/24"

  tags = {
    Name = "Public Subnet"
  }
}
```

Execute the `terraform apply` command to instantiate the public subnet in your AWS account.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165158056/0828374d-74b3-47f8-8a77-bfa1f1c91030.png?auto=compress,format&format=webp align="left")

Navigate to the VPC console, proceed to the Subnets section, and verify the successful creation of the "Public Subnet."

### ***3\. Create a private subnet with CIDR block 10.0.2.0/24 in the above VPC.***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165160325/6913a9fc-1a83-4a64-8a7b-244b6526e185.png?auto=compress,format&format=webp align="left")

This Terraform configuration generates a private subnet with the CIDR block 10.0.2.0/24 within the VPC identified by the ID `aws_`[`vpc.main.id`](https://pmgoriya.hashnode.dev/terraform-hands-on-project-build-your-own-aws-infrastructure-with-ease-using-infrastructure-as-code-iac#heading-2-create-a-public-subnet-with-cidr-block-1001024-in-the-above-vpc). The subnet is tagged with the name "Private Subnet."

```plaintext
resource "aws_subnet" "private_subnet" {
  vpc_id     = aws_vpc.main.id
  cidr_block = "10.0.2.0/24"

  tags = {
    Name = "Private Subnet"
  }
}
```

Execute the `terraform apply` command to execute the configuration and create the "Private Subnet."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165164045/aa1085a2-536d-4d9d-a7f4-b5c53a485988.png?auto=compress,format&format=webp align="left")

Confirm the successful creation of the "Private Subnet" by checking the results in the VPC console after running Terraform apply.

### ***4\. Create an Internet Gateway (IGW) and attach it to the VPC.***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165172392/90d06145-2323-4104-85b7-bb1eb302dc64.png?auto=compress,format&format=webp align="left")

This Terraform configuration generates an internet gateway within the VPC identified by the ID `aws_`[`vpc.main.id`](https://pmgoriya.hashnode.dev/terraform-hands-on-project-build-your-own-aws-infrastructure-with-ease-using-infrastructure-as-code-iac#heading-2-create-a-public-subnet-with-cidr-block-1001024-in-the-above-vpc). The internet gateway is tagged with the name "igw."

```plaintext
resource "aws_internet_gateway" "gw" {
  vpc_id = aws_vpc.main.id

  tags = {
    Name = "igw"
  }
}
```

Execute the `terraform apply` command to apply the configuration and create the internet gateway.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165177768/6758b272-d932-40d4-a305-473fb1326fef.png?auto=compress,format&format=webp align="left")

Afterwards, navigate to the VPC console, proceed to the Internet Gateways section, and verify the successful creation of the new internet gateway labeled 'igw.' Confirm that the VPC is attached to the internet gateway.

### ***5\. Create a route table for the public subnet and associate it with the public subnet. This route table should have a route to the Internet Gateway.***

Declare a route table for the public subnet using the following Terraform configuration:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165186678/e933f746-851f-48ed-a6e0-ad17d5a7c09b.png?auto=compress,format&format=webp align="left")

```plaintext
resource "aws_route_table" "public" {
  vpc_id = aws_vpc.main.id

  route {
    cidr_block = "0.0.0.0/0"
    gateway_id = aws_internet_gateway.gw.id
  }

  tags = {
    Name = "route-table"
  }
}

resource "aws_route_table_association" "public" {
  subnet_id      = aws_subnet.public_subnet.id
  route_table_id = aws_route_table.public.id
}
```

The `aws_route_table` block establishes a new route table within the VPC specified by the `vpc_id` attribute. It defines a route directing all traffic with a destination CIDR of "0.0.0.0/0" to the internet gateway identified by the `gateway_id` attribute. The `tags` attribute assigns a name ("route-table") to facilitate easy identification.

Subsequently, the `aws_route_table_association` block associates the newly created route table with a public subnet, identified by the `subnet_id` attribute. The `route_table_id` attribute refers to the ID of the route table created in the preceding block.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165191922/24fe2151-73c8-4e88-91e9-879bde25266e.png?auto=compress,format&format=webp align="left")

Verify the successful creation of the new route table in the Route Tables section. Confirm that the routes direct traffic to the internet gateway. Additionally, acknowledge the association of the route table with the public subnet through Terraform.

### ***6\. Launch an EC2 instance in the public subnet with the following details:***

* ***AMI***
    
* ***Instance type: t2.micro***
    

The `aws_instance` block initiates the creation of a new EC2 instance in the specified public subnet, denoted by the `subnet_id` attribute. The Amazon Machine Image (AMI) ID utilized is ami-0f8ca728008ff5af4, representing an Ubuntu 18.04 LTS image. The `key_name` attribute designates the key pair name for SSH access, and the `vpc_security_group_ids` attribute identifies the security group by its ID, created in the subsequent block.

```plaintext
resource "aws_instance" "web_server" {
  ami           = "ami-0c7217cdde317cfec"
  instance_type = "t2.micro"
  key_name      = "ansible_key"
  subnet_id     = aws_subnet.public_subnet.id

  vpc_security_group_ids = [
      aws_security_group.ssh_access.id
  ]
 tags = { 
    name = "terraform-instance"
}
}
```

### ***Security group: Allow SSH access from anywhere***

The `aws_security_group` block establishes a security group allowing inbound traffic on ports 22 (SSH) and 80 (HTTP) from any source (0.0.0.0/0). The `name_prefix` attribute sets a prefix for the security group name, and the `vpc_id` attribute specifies the VPC's ID where the security group is created.

```plaintext
resource "aws_security_group" "ssh_access" {
  name_prefix = "ssh_access"
  vpc_id      = aws_vpc.main.id

  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}
```

### **User data: Use a shell script to install Apache and host a simple website**

The `user_data` attribute contains a shell script that installs Apache, creates a basic HTML file, and restarts Apache upon instance launch.

```plaintext
user_data = <<-EOF
  #!/bin/bash
  sudo apt-get update -y
  sudo apt-get install apache2 -y
  sudo systemctl start apache2
  sudo systemctl enable apache2
  echo "<html><body><h1>Namaste! Welcome to my website!</h1></body></html>" > /var/www/html/index.html
  sudo systemctl restart apache2
EOF
```

### ***Create an Elastic IP and associate it with the EC2 instance.***

The `aws_eip` block creates an Elastic IP associated with the EC2 instance created earlier, specifying the instance ID in the `instance` attribute. The `tags` attribute names the Elastic IP for easy identification.

```plaintext
resource "aws_eip" "eip" {
  instance = aws_instance.web_server.id

  tags = {
    Name = "test-eip"
  }
}
```

After running `terraform apply`, the EC2 instance, named "terraform-instance," is successfully created in the AWS account.

Ultimately our [**main.tf**](https://pmgoriya.hashnode.dev/terraform-hands-on-project-build-your-own-aws-infrastructure-with-ease-using-infrastructure-as-code-iac#heading-2-create-a-public-subnet-with-cidr-block-1001024-in-the-above-vpc) file looks like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165240509/8d7c115d-7183-4cec-9b10-5d3c8d22822e.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165243789/231d992c-7a70-4644-bf27-e988ab27e4f9.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165247782/c555fc72-5c87-4923-bb3d-2b73ff17f5e0.png?auto=compress,format&format=webp align="left")

### ***7\. Open the website URL in a browser to verify that the website is hosted successfully.***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703165234723/cf1cff6d-6ee9-47f6-88a7-bef1f8405f0e.png?auto=compress,format&format=webp align="left")