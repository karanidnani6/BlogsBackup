---
title: "Day 51: Your CI/CD pipeline on AWS - Part 2 🚀 ☁"
datePublished: Fri Dec 29 2023 07:20:25 GMT+0000 (Coordinated Universal Time)
cuid: clqqb0wpb000608lcf9956u7s
slug: day-51-your-cicd-pipeline-on-aws-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703822979314/7ee7b265-3c65-4e11-8669-374842d934d5.jpeg
tags: aws, 90daysofdevops

---

## What is CodeBuild ?

AWS CodeBuild is a fully managed build service in the cloud. CodeBuild compiles your source code, runs unit tests, and produces artifacts that are ready to deploy. CodeBuild eliminates the need to provision, manage, and scale your own build servers.

# Task-01 :

* Read about Buildspec file for Codebuild.
    
* create a simple index.html file in CodeCommit Repository
    
* you have to build the index.html using nginx server
    

### **Step 1: Read about Buildspec file for CodeBuild**

The `buildspec.yml` file is used in AWS CodeBuild to define the build process. It contains a series of build commands and settings that CodeBuild uses to run your build. Here is a simple example of a `buildspec.yml` file:

```plaintext
version: 0.2

phases:
  build:
    commands:
      - echo "Build phase"
      - npm install
      - npm run build

artifacts:
  files: 'index.html'
```

This is a basic example for a Node.js project, and it may vary based on your project requirements.

### **Step 2: Create a simple** `index.html` file in CodeCommit Repository

Create a new file named `index.html` with some simple content. For example:

```plaintext
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Nginx Website</title>
</head>
<body>
    <h1>Hello, this is a simple Nginx website!</h1>
</body>
</html>
```

This creates a simple HTML file with a **"**Hello, this is a simple Nginx website!**"** message.

* Navigate to the CodeCommit service.
    
* Create and select the repository where you want to add the `index.html` file.
    
* Click on "**Commit Changes**" to save the changes.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703824641363/c0705b29-6890-4efd-8d60-5c47600d65fa.png align="center")
    
* Clone the repository to your instance and verify the files.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703825307458/41aaabdb-b05d-4b73-a510-ccbd6c45550f.png align="center")
    
    # Task-02 :
    
    * Add buildspec.yaml file to CodeCommit Repository and complete the build process.
        
        Now that we've successfully built our HTML page, it's time to integrate this process into our CodeCommit repository.
        
        **Step 1: Add** `buildspec.yaml` **file to CodeCommit Repository**
        
        * To make the build process automatic, we need to commit the `buildspec.yaml` file to our CodeCommit repository.
            
        * Push this file to our repository.
            
            ```plaintext
              version: 0.2
            
              phases:
                install:
                  commands:
                    - echo Installing NGINX
                    - sudo apt-get update
                    - sudo apt-get install nginx -y
                build:
                  commands:
                    - echo Build started on 'date'
                    - cp index.html /var/www/html/
                post_build:
                  commands:
                    - echo Configuring NGINX
            
              artifacts:
                files:
                  - /var/www/html/index.html
            ```
            
            ```plaintext
            
              $ git add .
              $ git commit -m "Commit Message"
              $ git push <branch-name>
            ```
            
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703828081375/02ffb215-955d-4978-b66d-492fd80d8be1.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703828096157/be5c5521-b304-4fb6-86cd-d81679bfd5ba.png align="center")
    
    **Step 2: Complete the Build Process**
    
    Once the `buildspec.yaml` file is in your repository, AWS CodeBuild will automatically pick it up when you push changes to your repository.
    
    It will execute the build process as defined and generate the `index.html` file.
    
    * Create a `CodeBuild` project in `AWS Console`
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703830106093/bdbb406b-f1e2-4cb3-bd9d-231d9e71a08d.png align="center")
        
        * Select the source provider, repository, and branch.
            
        * Select your environment and operating system & create the codeBuild Project
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703830264887/2b8aa501-1261-4ce7-9e1e-244b8e276ae1.png align="center")
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703831182829/f2a974d7-c43f-430f-982e-37c243a3841e.png align="center")
            
        * Now, start the build by clicking on **Start Build** & wait to complete it
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703831208175/7f84ad28-bede-4283-829a-b48e044c0b97.png align="center")
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703831540349/8ee585f4-ad73-48bd-b421-4954b29fecca.png align="center")
            
        * Store the build details in the artifacts
            
            `Before that, create an S3 bucket. Navigate to the S3 bucket in the AWS console and provide the bucket name and create the bucket.`
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703833422799/68e31e36-7dce-40be-a8ba-86f00280ac56.png align="center")
            
        * Click on edit and select artifact. Provide all the details and create an artifact.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703833525776/11f3282c-641c-43c0-98b5-7cca5e0836b7.png align="center")
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703833599147/87fcb54b-4f29-4115-abf4-9127f17edce5.png align="center")
            
        * Now if you rebuild the project you can see the **UPLOAD\_ARTIFACTS** section.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703833689197/de42a5ed-8220-451d-bd2b-557950cf6835.png align="center")
            
        * Navigate to the S3 bucket and you can see the build.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703833724255/39dec941-765f-425f-a07a-5d02b41c271c.png align="center")
            
        * Click on the **Open URL** to open the nginx & see the output of the index.html file.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703833758892/d5e10d8a-2e32-4e81-9f89-7e28f400cdd2.png align="center")
            
        * You've successfully set up AWS CodeBuild to automate the build process of your HTML page.