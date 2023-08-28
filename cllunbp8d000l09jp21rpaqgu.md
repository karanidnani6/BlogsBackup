---
title: "#Day26:Jenkins Declarative Pipeline"
datePublished: Mon Aug 28 2023 08:57:17 GMT+0000 (Coordinated Universal Time)
cuid: cllunbp8d000l09jp21rpaqgu
slug: day26jenkins-declarative-pipeline
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693209640723/80646a04-ab5b-4981-b4ca-6ae62e53ea16.png
tags: 90daysofdevops, jenkins-declarative-pipeline

---

Hey there, tech enthusiasts! 👋 Are you tired of manually handling repetitive tasks in your software development process? 🤖 Well, look no further – Jenkins Pipelines are here to rescue you! 🌟 In this blog, we'll break down the basics of Jenkins Pipelines, including Declarative and Scripted pipelines. Let's dive in! 🚀

### **What is Jenkins Pipeline? 🤔**

Imagine you're baking cookies 🍪 - you follow a series of steps like mixing ingredients, shaping dough, and baking to get the delicious treats. Similarly, Jenkins Pipelines are a set of steps that automate your software development lifecycle. From code building and testing to deployment and delivery, Jenkins Pipelines make it seamless! 🛠️

### **Declarative Pipeline - Simple and Structured ✨**

Think of Declarative Pipelines as a well-organized to-do list. 📋 You tell Jenkins what you want to achieve, and it figures out how to do it! This approach uses a set of predefined syntax and simplifies pipeline creation. If you're new to pipelines, Declarative is your best friend. It's like following a recipe - you list the ingredients (steps), and Jenkins takes care of the cooking! 🍳

### **Scripted Pipeline - Unleash Your Creativity! 🎨**

Now, if you're a coding wizard 🧙‍♂️, Scripted Pipelines might be your jam. It's like having a blank canvas 🎨 - you can paint your automation masterpiece using Groovy scripting. Every detail is in your hands - from defining stages to handling complex logic. However, with great power comes great responsibility! 🦸‍♂️ Scripted Pipelines offer flexibility but might be a bit overwhelming for beginners.

### **Which One to Choose? 🤷‍♀️🤷‍♂️**

Deciding between Declarative and Scripted Pipelines depends on your experience and project needs. If you're new to pipelines and prefer a structured approach, go for Declarative. But if you're comfortable with coding and need intricate customization, Scripted is your playground. Remember, the goal is to streamline your workflow while having fun! 🎉

In a nutshell, Jenkins Pipelines are your secret weapon to conquer monotonous tasks in the software world. Whether you opt for Declarative's simplicity or Scripted's flexibility, automation will be your best friend. 🤖🤝 So, don't hesitate - jump into the world of Jenkins Pipelines and let your creativity flow while leaving manual work behind! 🚀🌈

### Why you should have a Pipeline?

Are you tired of the never-ending cycle of manual software development tasks? ⏳ Are you looking for a way to streamline your workflow and boost productivity? 🚀 Look no further! In this blog, we'll explore five compelling reasons why you should embrace Jenkins Pipelines for your projects. Let's dive in and unlock the world of efficiency! 💡

**1\. Automate with Precision 🤖**

Picture this: you're managing a complex project with multiple stages like building, testing, and deploying. One wrong move, and the entire process crumbles. Jenkins Pipelines offer a structured way to automate each step, ensuring accuracy and consistency. No more human errors messing up your hard work - the pipeline executes tasks precisely, every single time.

**2\. Save Time and Resources ⏱️💰**

Time is money, and every minute spent on repetitive tasks is a minute wasted. Jenkins Pipelines free up your team from manual chores by automating them. This means developers can focus on creative problem-solving, innovation, and improving your software. Plus, you'll save resources by optimizing the use of manpower and reducing the risk of bottlenecks.

**3\. Consistent Quality 📊**

Manual processes can lead to variations in quality due to human oversight or inconsistency. With Jenkins Pipelines, you establish a standardized workflow. This consistency leads to higher-quality code, better testing practices, and reliable deployments. Your end-users will thank you for the enhanced user experience and fewer bugs!

**4\. Traceability and Insights 🔍📈**

Ever wondered which stage caused a glitch in your deployment? Jenkins Pipelines offer transparent traceability. You can easily track each step's progress and identify where things went awry. Moreover, you'll gain valuable insights into your development process, enabling data-driven decisions for continuous improvement.

**5\. Scalability and Collaboration 🌐👥**

As your projects grow, maintaining manual processes becomes a nightmare. Jenkins Pipelines scale effortlessly. Whether you're working on a small team or a massive enterprise project, pipelines adapt to your needs. Moreover, they encourage collaboration by providing a clear visual representation of the entire development lifecycle, ensuring everyone's on the same page.

**Final Thoughts 🌈**

Jenkins Pipelines aren't just a fancy tool - they're a game-changer for modern software development. With automation, accuracy, time savings, quality assurance, traceability, and scalability on your side, adopting pipelines is a no-brainer. Embrace the future of efficiency and let Jenkins Pipelines elevate your development process to new heights! 🚀🔗

### Pipeline syntax -

```plaintext
pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                // 
            }
        }
        stage('Test') { 
            steps {
                // 
            }
        }
        stage('Deploy') { 
            steps {
                // 
            }
        }
    }
}
```

### Task-01:**Create a New Job using Pipeline Hello World Example**

1. **Log in to Jenkins**: Open your web browser and navigate to your Jenkins server's URL. Log in with your credentials.
    
2. **Create a New Pipeline Job**:
    
    * Click on "New Item" on the Jenkins dashboard.
        
    * Enter a name for your pipeline job (e.g., "HelloWorldDeclarative") and select "Pipeline" as the job type.
        
    * Click "OK" to proceed.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693212937199/0455982d-aec2-41f0-b384-c1d08d94a176.avif align="center")
        
3. **Configure Pipeline Settings**:
    
    * Scroll down to the "Pipeline" section.
        
    * In the "Definition" dropdown, select "Pipeline script".
        
    * Leave the "Script" field empty for now; we'll fill this in shortly.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693212951364/e001702f-1d83-44b9-85fa-8dceb61329d5.avif align="center")
        
4. **Define the Declarative Pipeline Script**:
    
    * Now we'll define the Declarative pipeline script based on the "Hello World" example.
        

Here's the complete Declarative pipeline script for the "Hello World" example:

```plaintext
pipeline {
    agent any
    
    stages {
        stage('Hello') {
            steps {
                echo 'Hello, world!'
            }
        }
        
        stage('Goodbye') {
            steps {
                echo 'Goodbye, world!'
            }
        }
    }
}
```

1. **Save and Run the Pipeline**:
    
    * Scroll down and click the "Save" button to save your pipeline configuration.
        
    * After saving, you'll be redirected to the pipeline's overview page.
        
    * Click on "Build Now" to start the pipeline run.
        
2. **View Pipeline Execution**:
    
    * You'll see the pipeline running with the two stages: "Hello" and "Goodbye."
        
    * Click on the pipeline run number to view the details of each stage's execution.
        
    * You can see the "Hello, world!" and "Goodbye, world!" messages in the console output.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693212970939/aa31ab7f-e99f-4427-b36f-f68b7fb6af55.avif align="center")
        

Congratulations! You've successfully created a Jenkins pipeline using the Declarative syntax based on the official "Hello World" example. This simple pipeline demonstrates how stages and steps work in the Declarative pipeline. You can further customize and expand your pipelines to include more complex workflows and integrations. Happy automating! 🚀👨‍💻