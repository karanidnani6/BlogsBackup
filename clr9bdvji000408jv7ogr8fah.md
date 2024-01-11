---
title: "Day 68 - Scaling with Terraform 🚀"
datePublished: Thu Jan 11 2024 14:38:07 GMT+0000 (Coordinated Universal Time)
cuid: clr9bdvji000408jv7ogr8fah
slug: day-68-scaling-with-terraform
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704982970197/02a8ccf9-cb78-48f3-8fdf-7e1b1af0f756.jpeg

---

## Understanding Scaling

Scaling is the process of adding or removing resources to match the changing demands of your application. As your application grows, you will need to add more resources to handle the increased load. And as the load decreases, you can remove the extra resources to save costs.

Terraform makes it easy to scale your infrastructure by providing a declarative way to define your resources. You can define the number of resources you need and Terraform will automatically create or destroy the resources as needed.

## Task 1: Create an Auto Scaling Group

Auto Scaling Groups are used to automatically add or remove EC2 instances based on the current demand. Follow these steps to create an Auto Scaling Group:

* In your [main.tf](https://github.com/karanidnani6/90DaysOfDevOps/blob/master/2023/day68/tasks.md#task-1-create-an-auto-scaling-group) file, add the following code to create an Auto Scaling Group:
    

```plaintext
resource "aws_launch_configuration" "web_server_as" {
  image_id        = "ami-005f9685cb30f234b"
  instance_type  = "t2.micro"
  security_groups = [aws_security_group.web_server.name]

  user_data = <<-EOF
              #!/bin/bash
              echo "<html><body><h1>You're doing really Great</h1></body></html>" > index.html
              nohup python -m SimpleHTTPServer 80 &
              EOF
}

resource "aws_autoscaling_group" "web_server_asg" {
  name                 = "web-server-asg"
  launch_configuration = aws_launch_configuration.web_server_lc.name
  min_size             = 1
  max_size             = 3
  desired_capacity     = 2
  health_check_type    = "EC2"
  load_balancers       = [aws_elb.web_server_lb.name]
  vpc_zone_identifier  = [aws_subnet.public_subnet_1a.id, aws_subnet.public_subnet_1b.id]
}


```

This Terraform script generates two AWS components: an autoscaling group and a launch configuration. The launch configuration defines parameters such as image ID, instance type, security group, and user data for initiating new instances. The user data script, upon instance launch, installs a basic web server and presents a straightforward HTML page conveying the message "You're doing exceptionally well."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703334745529/9912b013-c92d-498b-a0e9-beda5d588a8f.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703334750702/40d6bdf9-947a-446d-836e-75c4ba656408.png?auto=compress,format&format=webp align="left")

Regarding the AWS resources:

1. **aws\_launch\_configuration:** This section establishes a launch configuration tailored for EC2 instances set to be deployed within our autoscaling group. It mandates the following arguments:
    
    * `image_id`: The ID of the EC2 image to launch.
        
    * `instance_type`: The type of instance to launch.
        
    * `security_groups`: An array of associated security group IDs.
        
2. **aws\_autoscaling\_group:** This segment introduces an Auto Scaling Group resource, specifying parameters such as:
    
    * `max_size`: The maximum size allowed for the Auto Scaling Group.
        
    * `min_size`: The minimum size required for the Auto Scaling Group.
        
    * `desired_capacity`: The desired number of Amazon EC2 instances to maintain within the group.
        

This Terraform script sets up an AWS VPC with two public subnets in different availability zones. It includes an internet gateway, a public route table, and route table associations. The script also creates an AWS security group that permits SSH and HTTP traffic. Additionally, it defines a launch configuration that uses user data to start a Python HTTP server on port 80. Finally, it establishes an autoscaling group with a minimum of 1 instance, a maximum of 3 instances, and a desired capacity of 2 instances, spread across the two subnets.

To get started, run `terraform init` to initialize the Terraform project.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703334754477/0aa3153a-1086-42a0-be11-d7bba2c0021f.png?auto=compress,format&format=webp align="left")

After that, run `terraform plan` to review the execution plan,

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703334757811/ba2e7fd2-462a-4849-a5a5-c34714810df2.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703334773534/d2d6715a-06dc-4326-b0dc-7263b2777d6c.png?auto=compress,format&format=webp align="left")

and execute `terraform apply` to create the Auto Scaling Group.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703334776975/b2abad94-848d-41a9-b338-91aaa50e6e2d.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703334780646/090e5868-11ef-4a5d-9894-789504c3b32e.png?auto=compress,format&format=webp align="left")

After these steps, two new EC2 instances will be created, as the desired capacity is set to 2.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704983760302/4eecb4d2-5831-4e09-b651-6f7d1a6996f4.png align="center")

The launch configuration is successfully created, and the auto-scaling group is now up and running with two instances.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704983785507/7ade3207-4a70-40ba-9630-9f61c6d1273f.png align="center")

## Task 2: Test Scaling

* Go to the AWS Management Console and select the Auto Scaling Groups service.
    
* Select the Auto Scaling Group you just created and click on the "Edit" button.
    
* Increase the "Desired Capacity" to 3 and click on the "Save" button.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704983823094/1a632240-028a-4f6f-93d4-f9a3654adb6b.png align="center")
    
    Wait a few minutes for the new instances to be launched.
    
* Go to the EC2 Instances service and verify that the new instances have been launched.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704983843013/2095152f-b141-4a67-8923-8615848bbbde.png align="center")
    
    Decrease the "Desired Capacity" to 1 and wait a few minutes for the extra instances to be terminated.
    
* Go to the EC2 Instances service and verify that the extra instances have been terminated.
    

### **Conclusion**

Scaling your infrastructure is pivotal in managing contemporary applications.

The combination of Terraform and AWS provides a potent framework for dynamically adjusting your resources to cater to shifting demands.