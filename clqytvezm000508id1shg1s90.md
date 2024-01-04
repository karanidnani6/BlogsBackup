---
title: "Day 53: Your CI/CD pipeline on AWS - Part 4 🚀 ☁"
datePublished: Thu Jan 04 2024 06:30:11 GMT+0000 (Coordinated Universal Time)
cuid: clqytvezm000508id1shg1s90
slug: day-53-your-cicd-pipeline-on-aws-part-4
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704348303953/eb42aa82-29c7-40f0-8476-73dc043b97d6.jpeg
tags: 90daysofdevops

---

## What is CodePipeline ?

* CodePipeline builds, tests, and deploys your code every time there is a code change, based on the release process models you define. Think of it as a CI/CD Pipeline service
    

# Task-01 :

* Create a Deployment group of Ec2 Instance.
    
* Create a CodePipeline that gets the code from CodeCommit, Builds the code using CodeBuild and deploys it to a Deployment Group.
    

**Step 1: Create a Deployment Group of EC2 Instances**

1. Navigate to the CodePipeline section in the AWS management console.
    
2. Provide the Pipeline name, let the service role default and click on Next.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704349540780/1b5aefbb-d733-409d-b645-ab748295326c.png align="center")
    
3. Select the source provider, repository name, branch and detection options and click on Next.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704349593226/5eebc523-c1e6-4872-90ec-80c9175d23c6.png align="center")
    
4. Select Build Provider and click on Next.
    
5. Select Deploy Provider and click on Next.
    
6. Successfully created a CodePipeline that automates the deployment process.
    
7. Now go to the Public IP of your `EC2 Instance` and check the running `index.html` file.
    

In summary, the outlined process establishes an efficient CI/CD pipeline using AWS services. By combining CodeCommit, CodeBuild, and CodeDeploy, developers can automate code integration, build processes, and deployments to EC2 instances. This streamlined workflow enhances development speed, ensures consistency, and reduces manual efforts. Leveraging AWS services enables quick identification and resolution of issues, fostering a reliable and agile software delivery lifecycle. Ultimately, this CI/CD solution empowers teams to deliver high-quality software with efficiency and confidence.