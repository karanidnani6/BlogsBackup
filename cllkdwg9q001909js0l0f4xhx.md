---
title: "#Day22:Getting Started with Jenkins 😃"
datePublished: Mon Aug 21 2023 04:35:47 GMT+0000 (Coordinated Universal Time)
cuid: cllkdwg9q001909js0l0f4xhx
slug: day22getting-started-with-jenkins
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692588684086/16a52be6-54fb-4189-91d1-c98039683a18.webp
tags: jenkins, 90daysofdevops

---

### 🚀 **Jenkins: Your DevOps Best Friend!** 🌟

In the bustling world of software development, efficiency is key. Meet Jenkins, your trusty DevOps companion, here to make your coding life a breeze! 🛠️

### **What's the Buzz About Jenkins?** 🐝

Jenkins is like the Swiss Army knife of DevOps tools. It's an open-source automation server, and its main mission is to simplify and automate all those nitty-gritty tasks that come with building and delivering software. 🤖

### **Why Jenkins, You Ask?** 🤔

Well, picture this: You're working on a cool project with a team of awesome developers. 🤓 You're all writing code, but you need a way to ensure that the code works smoothly together and that any new changes don't break the existing stuff. That's where Jenkins struts onto the stage. 🎤

### **Continuous Integration (CI) - The Teamwork Dance!** 💃🕺

CI is like a well-choreographed dance. 💃 Imagine you and your teammates are all dancing in sync, making sure your moves complement each other. In Jenkins' world, this means every time someone adds new code to the project, Jenkins automatically checks it to see if it plays nicely with the rest of the code. If there are any hiccups, Jenkins lets you know right away. 🚦

### **Continuous Delivery (CD) - The Dress Rehearsal!** 🎭

CD is like a dress rehearsal before the big show. 🎪 You've got your code ready, but you want to make sure it's not just working but ready to be shown to the world. Jenkins helps you automate this process too. It packages your code neatly, runs more tests, and ensures it's all set to be deployed whenever you're ready. 🎁

### **Continuous Deployment (CD) - The Grand Premiere!** 🎬

CD takes it one step further. It's like the grand premiere of your show. 🌟 With Jenkins in the spotlight, your code is automatically deployed to where it needs to go – whether that's a website, a mobile app, or anywhere else. All the checks and balances Jenkins has done ensure a smooth and flawless release. 🚀

So, in simple terms, Jenkins is your DevOps assistant, making sure your code works together, is ready to show to the world, and even takes the stage when it's time for the big reveal. 🎉

Whether you're a coding superstar or just starting your DevOps journey, Jenkins is here to make your life easier and your software better. So, go ahead, embrace Jenkins, and let the automation magic begin! 🌈✨

### **🛠️Installation of Jenkins**

Installing Jenkins is a straightforward process, and you have a few options depending on your operating system and preferences. Here, I'll outline the steps for installing Jenkins on a common setup: Ubuntu Linux.

**Installing Jenkins on Ubuntu:**

1. **Update Packages:** Open a terminal window and run the following commands to make sure your package list and installed packages are up to date:
    
    ```bash
    sudo apt update
    sudo apt upgrade
    ```
    
2. **Install Java:** Jenkins requires Java to run. You can install OpenJDK using the following command:
    
    ```bash
    sudo apt install openjdk-11-jdk
    ```
    
3. **Add Jenkins Repository:** Add the Jenkins repository to your package sources:
    
    ```bash
    wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
    sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
    ```
    
4. **Install Jenkins:** Install Jenkins using the following commands:
    
    ```bash
    sudo apt update
    sudo apt install jenkins
    ```
    
5. **Start Jenkins:** Jenkins should start automatically after installation. You can check its status using:
    
    ```bash
    sudo systemctl status jenkins
    ```
    
6. **Access Jenkins Web Interface:** By default, Jenkins runs on port 8080. Open your web browser and enter [`http://your_server_ip:8080`](http://your_server_ip:8080) to access the Jenkins setup wizard.
    
7. **Unlock Jenkins:** The setup wizard will ask you to retrieve the initial administrative password. Run the following command to get the password:
    
    ```bash
    sudo cat /var/lib/jenkins/secrets/initialAdminPassword
    ```
    
    Copy the password and paste it into the setup wizard.
    
8. **Customize Jenkins Installation:** Follow the instructions in the setup wizard to customize Jenkins by selecting recommended plugins or installing plugins manually.
    
9. **Create First Admin User:** Set up the first admin user by providing a username, password, and other details.
    
10. **Start Using Jenkins:** Once the setup is complete, you can start using Jenkins to create and manage your pipelines and jobs.
    

Remember, these instructions are specific to Ubuntu. If you're using a different operating system, the installation steps might vary slightly. Always refer to the official Jenkins documentation for the most accurate and up-to-date installation instructions.

### Task:

**Create a freestyle pipeline to print "Hello World!!**

Creating a "Hello World" pipeline in Jenkins is a simple yet effective way to understand how pipelines work. Here's a step-by-step guide on how to create a freestyle pipeline to print "Hello World!!":

1. **Log into Jenkins**: Open your web browser and navigate to your Jenkins dashboard.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692592438686/8c945c11-4397-41ef-8b5b-da144b91f33c.png align="center")

1. **Create a New Item**:
    
    * Click on "New Item" on the left-hand side of the dashboard.
        
    * Enter a name for your pipeline, like "HelloWorldPipeline".
        
    * Select "Freestyle project" and click "OK".
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692592461804/91cb2508-2dc3-4a81-bb40-328f7f6cc109.png align="center")

1. **Configure the Pipeline**:
    
    * Under the "General" section, you can provide a description if you wish.
        
    * In the "Build" section, click on "Add build step" and select "Execute shell" (or "Execute Windows batch command" if you're on a Windows system).
        
2. **Write the Command**:
    
    * In the command box, type the command to print "Hello World!!". For Unix-like systems, use:
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692592493755/ef6fd30b-3569-43d6-a7f3-feae5b082d1e.png align="center")
        
        ```plaintext
        echo "Hello World!!"
        ```
        
3. **Save the Configuration**:
    
    * Scroll down and click "Save" to save the pipeline configuration.
        
4. **Run the Pipeline**:
    
    * On your Jenkins dashboard, find your newly created pipeline item and click on it.
        
5. **Build the Pipeline**:
    
    * On the pipeline's page, click "Build Now" to start the pipeline.
        
6. **View the Console Output**:
    
    * Once the build is triggered, you'll see the build number listed in the build history.
        
    * Click on the build number to view the console output.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692592513939/1edadd4e-e67d-454c-a8fd-5dc1bf9b9eca.png align="center")
    
7. **Check the Output**:
    
    * In the console output, you'll see the "Hello World!!" message printed as the result of the command you wrote in the pipeline configuration.
        

Congratulations! You've successfully created a basic freestyle pipeline in Jenkins that prints "Hello World!!" when executed. This simple example demonstrates the power of Jenkins in automating tasks and executing commands in a controlled environment. As you delve deeper into Jenkins, you can explore more complex pipeline configurations and integrate various tools and stages into your CI/CD workflows.