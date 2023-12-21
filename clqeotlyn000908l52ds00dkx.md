---
title: "Day-48 - ECS AWS Elastic Container Service"
datePublished: Thu Dec 21 2023 04:13:25 GMT+0000 (Coordinated Universal Time)
cuid: clqeotlyn000908l52ds00dkx
slug: day-48-ecs-aws-elastic-container-service
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703070515485/b422384c-f22b-4735-82ce-ad07e8916d6f.png
tags: aws, ecs, 90daysofdevops

---

## What is ECS ?

ECS (Elastic Container Service) is a fully-managed container orchestration service provided by Amazon Web Services (AWS). It allows you to run and manage Docker containers on a cluster of virtual machines (EC2 instances) without having to manage the underlying infrastructure.

With ECS, you can easily deploy, manage, and scale your containerized applications using the AWS Management Console, the AWS CLI, or the API. ECS supports both "Fargate" and "EC2 launch types", which means you can run your containers on AWS-managed infrastructure or your own EC2 instances.

ECS also integrates with other AWS services, such as Elastic Load Balancing, Auto Scaling, and Amazon VPC, allowing you to build scalable and highly available applications. Additionally, ECS has support for Docker Compose and Kubernetes, making it easy to adopt existing container workflows.

Overall, ECS is a powerful and flexible container orchestration service that can help simplify the deployment and management of containerized applications in AWS.

## Difference between EKS and ECS ?

KS (Elastic Kubernetes Service) and ECS (Elastic Container Service) are both container orchestration platforms provided by Amazon Web Services (AWS). While both platforms allow you to run containerized applications in the AWS cloud, there are some differences between the two.

**Architecture**: ECS is based on a centralized architecture, where there is a control plane that manages the scheduling of containers on EC2 instances. On the other hand, EKS is based on a distributed architecture, where the Kubernetes control plane is distributed across multiple EC2 instances.

**Kubernetes Support**: EKS is a fully managed Kubernetes service, meaning that it supports Kubernetes natively and allows you to run your Kubernetes workloads on AWS without having to manage the Kubernetes control plane. ECS, on the other hand, has its own orchestration engine and does not support Kubernetes natively.

**Scaling**: EKS is designed to automatically scale your Kubernetes cluster based on demand, whereas ECS requires you to configure scaling policies for your tasks and services.

**Flexibility**: EKS provides more flexibility than ECS in terms of container orchestration, as it allows you to customize and configure Kubernetes to meet your specific requirements. ECS is more restrictive in terms of the options available for container orchestration.

**Community**: Kubernetes has a large and active open-source community, which means that EKS benefits from a wide range of community-driven development and support. ECS, on the other hand, has a smaller community and is largely driven by AWS itself.

In summary, EKS is a good choice if you want to use Kubernetes to manage your containerized workloads on AWS, while ECS is a good choice if you want a simpler, more managed platform for running your containerized applications.

# Task :

Set up ECS (Elastic Container Service) by setting up Nginx on ECS.

Establish an ECS Cluster: Navigate to the ECS service and select "Create Cluster."

Configure essential cluster settings, including the cluster name, VPC, and subnet.

Click 'Create.'

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703129288926/f946daa1-2737-472f-9d71-926258950f51.png align="center")

Verify the successful creation of the cluster.

Formulate a Task Definition: Access the ECS service, proceed to "Task Definitions," and choose "Create new Task Definition."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703129374827/a529f9ec-72c2-4d75-a232-29d50399be66.png align="center")

Assign the container name as "nginx" and insert the Image URL from the 'Amazon ECR public gallery' site. Define port mappings for HTTP by setting the "Container port" to 80.

Explore the Amazon ECR public gallery to locate and copy the nginx image URL.

Click 'Next.'

Opt for the Fargate launch type, and configure task settings, specifying task memory and CPU limits (e.g., .5vCPU and 1GB of memory).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703131131229/006a4632-c676-4597-a2d4-3376e79e2f1d.png align="center")

Click 'Create.'

Confirm the successful creation of the task.

Set Up a Service: Within ECS, select "Clusters" and pick the previously created cluster.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703131195681/d43f3b6e-3048-48c1-8383-4f48d8677df5.png align="center")

Click on "Create Service."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703131398097/fc36c242-9d0b-4b1d-aae0-dc19a8415754.png align="center")

Choose the task definition created in the previous steps.

Configure service settings, such as VPC, subnet, and security group settings (create a new security group).

Specify port mappings for HTTP using port 80.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703131811082/0e9d35a2-dd13-4118-9848-0c8fcdd415ee.png align="center")

Click 'Create.'

Confirm the successful creation of the service.

Upon the ECS service running, evaluate the Nginx container by accessing the Fargate task's public IP address in a web browser. Locate the public IP address in the "Tasks" tab of the ECS service, under the "Configuration" section.

Verify the Nginx Container: Access the 'Cluster' you established.

Click on 'Task.'

Navigate to the 'Configuration' section within the task details to find the public IP.

Open the web browser and enter the public IP address to view the default Nginx welcome page.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703131908978/aa8295d4-efc0-444e-a554-1ced2e546e87.png align="center")

Thanks for reading until here. Happy Learning!