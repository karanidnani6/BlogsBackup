---
title: "#Day23:Jenkins Freestyle Project for DevOps Engineers."
datePublished: Fri Aug 25 2023 14:42:27 GMT+0000 (Coordinated Universal Time)
cuid: cllqpc13n00060amf6vdx3qiv
slug: day23jenkins-freestyle-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692680313940/3bda36fe-e1ac-4747-9b67-07eefebdfa92.jpeg
tags: docker, jenkins, 90daysofdevops

---

### **Continuous Integration (CI): Harmonizing the Codebase**

Imagine a bustling kitchen where chefs work together to create a gourmet dish. In the realm of software, CI is akin to chefs harmoniously preparing ingredients. It involves multiple developers frequently integrating their code changes into a shared repository. Automated tests and quality checks are performed on each integration, quickly identifying issues like bugs or compatibility conflicts. This proactive approach ensures a smooth blend of code and minimizes the chances of "code clashes" during the final stages. 🧑‍💻🧑‍💻🧑‍💻

### **Continuous Delivery (CD): A Grand Finale Without the Drama**

Picture this: the chef's masterpiece is ready to be served, plated to perfection. CD takes the integrated code, tests it thoroughly in an environment similar to the real world, and automatically deploys it to a staging area. This meticulous rehearsal ensures that the final dish – or in this case, your software – is free of glitches and performs flawlessly. Once validated, the code is swiftly and reliably pushed into production, allowing users to savor new features without disruption. 🍰🚀

### **Continuous Deployment (CD): Taking It One Step Further**

If you're ready to go beyond the rehearsal and bring the curtain up immediately after testing, you're in the realm of Continuous Deployment. Here, validated code changes are automatically released into production. While this approach demands rigorous testing and confidence in your automated pipeline, it's the pinnacle of delivering value to users at unprecedented speed. 🚀🎉

**The Ultimate Collaboration: CI/CD Benefits**

✅ **Speed:** CI/CD accelerates development cycles, enabling quick feature releases and bug fixes. Developers see the fruits of their labor come to life faster.

✅ **Quality:** Automated testing at every step catches bugs early, ensuring software quality and reducing the likelihood of issues in production.

✅ **Collaboration:** Developers work in sync, resolving integration issues swiftly, and maintaining a healthy codebase.

✅ **Reliability:** Automated deployments minimize human errors, ensuring consistent and reliable releases.

✅ **Feedback Loop:** Rapid testing and deployment provide continuous feedback, aiding developers in making improvements.

✅ **Customer Delight:** Users experience quicker access to new features and fewer disruptions due to well-tested deployments.

### What Is a Build Job?

In Jenkins, a Build Job is like a special recipe that tells the robot chef (Jenkins) how to transform your raw code into a working software application. Just as a recipe has steps for making a yummy dish, a Build Job has steps for compiling, testing, and preparing your code for action.

**Cooking Up the Build Job Steps: Ingredients and Instructions**

Imagine you're baking a cake. You gather ingredients, mix them, bake, and voila – a cake! Similarly, in a Jenkins Build Job:

1. **Gathering Ingredients (Code):** Jenkins grabs your code from a special place (like a code repository), making sure it's ready to cook.
    
2. **Mixing It Up (Compiling):** Just like mixing flour, eggs, and sugar in baking, Jenkins compiles your code, turning it into something the computer can understand.
    
3. **Testing the Taste (Testing):** Imagine if you tasted the cake batter to check if it's good. Jenkins tests your code to see if it works properly and doesn't have any mistakes.
    
4. **Getting Ready to Serve (Packaging):** After baking, you put the cake on a nice plate. Jenkins packages your code neatly, making it ready for people to use.
    

**Why Jenkins Build Jobs Are Handy Chefs:**

1. **Less Mess:** Robot chefs (Build Jobs) follow the recipe exactly, so there's less chance of messing up.
    
2. **Quick Cooking:** Robot chefs are super fast, turning your code into software much quicker than doing it by hand.
    
3. **No Spoilers:** Robot chefs catch mistakes early, so your software comes out great without surprises.
    
4. **Repetitive Magic:** Just as you can use the same cake recipe for different cakes, you can reuse Jenkins Build Jobs for different projects.
    

### What is Freestyle Projects

In Jenkins, a Freestyle Project is like a blank canvas waiting for you to create your software masterpiece. It's a way to tell Jenkins how to build, test, and package your code in a way that fits your project's unique needs.

**Imagine Building a Treehouse:**

Think of it like building a treehouse. You start with an empty treehouse platform, and then you decide how to design it, what materials to use, and what features to include. Similarly, in a Jenkins Freestyle Project:

1. **Project Name:** You give your project a name, just like you'd name your treehouse.
    
2. **Building Steps:** Here's where the magic happens. You add building steps to your project, just like you'd add steps to building your treehouse. Each step is a specific action Jenkins should perform. Want to compile your code, run tests, or do some other task? You get to choose!
    
3. **Freedom in Tools:** Just as you might use different tools to build your treehouse, you can use different tools and scripts in your Jenkins Freestyle Project. It's your choice, whether you're comfortable with shell scripts, Python, or something else.
    
4. **Setting the Scene:** You configure the environment, like picking the location and materials for your treehouse. In Jenkins, you set up dependencies, configurations, and variables to make sure your project gets the right setup.
    

### Task-01

**Creating a Jenkins Freestyle Project with Docker Integration**

**Step 1: Setting Up a Docker Agent**

Ensure Docker is installed on your Jenkins server before proceeding.

* Log in to your Jenkins dashboard.
    
* Navigate to "Manage Jenkins" in the left sidebar.
    
* Select "Manage Nodes and Clouds."
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692972425898/b05ff8d4-4400-4235-b34c-9225dc062049.png align="center")

* Click on "New Node" or "New Agent."
    
* Assign a name to the agent, such as "Docker-Agent."
    
* Opt for the "Permanent Agent" option.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692972490391/7cc3c65a-d605-4ba0-a8e7-8d622f7f8b2a.png align="center")

* Choose "Launch agents via SSH" under "Launch method."
    
* Fill in the SSH credentials and host information.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692972783258/2c8a5485-27cd-489b-b03c-6db92a5d242f.png align="center")

* Define the agent's root directory for storing files.
    
* Save the agent configuration.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692972955141/1aadb4b6-b5b7-4408-8c6d-fef5b6452df1.png align="center")

**Step 2: Creating a Jenkins Freestyle Project**

1. Access your Jenkins dashboard.
    
2. Click "New Item" to initiate a new project.
    
3. Give the project a name.
    
4. Select "Freestyle project" as the project type.
    
5. Confirm by clicking "OK."
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692973457095/86e6255f-0bbd-418b-afe1-593c456fa1f9.png align="center")

**Step 3: Configuring Build Steps**

1. On the project's configuration page, proceed to the "Build" section.
    
2. Add a new build step by selecting "Add build step."
    
3. Opt for "Execute shell" to add a shell script build step.
    

**Step 4: Implementing the "docker build" Command**

Within the shell script build step, include the following commands:

**COPY**

```plaintext
#!/bin/bash

# Navigate to your app's directory
cd /path/to/your/app

# Build the Docker image
docker build -t your-app-image .
```

Replace `/path/to/your/app` with your app's actual directory path and `your-app-image` with the preferred Docker image name.

**Step 5: Executing the "docker run" Command**

1. Choose "Add build step" once more.
    
2. Select "Execute shell" to add another shell script build step.
    

In the shell script build step, insert these commands:

**COPY**

```plaintext
#!/bin/bash

# Launch the Docker container
docker run -d -p 8000:8000 your-app-image
```

Substitute `your-app-image` with the same image name used earlier.

**Step 6: Saving and Triggering the Project**

1. Scroll down and click "Save" to store the project configuration.
    
2. Click "Build Now" to initiate the project's build process.
    

Jenkins will execute the configured build steps. It will first create the Docker image using the "docker build" command and then initiate a Docker container via the "docker run" command. The container will expose port 8000 from the app to port 8080 on the host.

### **Task-02: Jenkins Project for Docker Compose Management**

In this task, your objective is to set up a Jenkins project that effectively utilizes Docker Compose to manage the deployment and cleanup of multiple containers as defined in a compose file.

**Step 1: Preparing Your Jenkins Environment**

Ensure that Docker and Docker Compose are properly installed on your Jenkins server before proceeding.

**Step 2: Creating a Jenkins Freestyle Task**

1. Log in to the Jenkins dashboard.
    
2. Initiate the creation of a new project by selecting "New Item."
    
3. Assign a name to your project
    
4. Opt for "Freestyle project" as the chosen project type.
    
5. Confirm your selection by clicking "OK."
    

**Step 3: Configuring the Build Stages**

1. Within the project's configuration page, navigate to the "Build" section.
    
2. Choose "Add build step."
    
3. Opt for "Execute shell" to incorporate a shell script build stage.
    

**Step 4: Executing the "docker-compose up -d" Command**

Inside the shell script build stage, integrate the following commands:

**COPY**

```plaintext
#!/bin/bash

# Navigate to the directory containing your docker-compose.yml file
cd /path/to/your/compose/directory

# Initiate the containers defined in the compose file
docker-compose up -d
```

Replace `/path/to/your/compose/directory` with the specific path to your directory containing the docker-compose.yml file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692070073380/d6660151-1caf-4eb0-8ea4-aab94df0e459.png?auto=compress,format&format=webp align="left")

**Step 5: Introducing a Cleanup Stage**

1. Choose "Add build step" once more.
    
2. Opt for "Execute shell" to introduce another shell script build stage.
    

Within this shell script build stage, add the following commands:

**COPY**

```plaintext
#!/bin/bash

# Navigate to the directory containing your docker-compose.yml file
cd /path/to/your/compose/directory

# Halt and remove the containers defined in the compose file
docker-compose down
```

Again, replace `/path/to/your/compose/directory` with the appropriate path.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692070240149/82e32b0c-e0be-4a16-b3ec-1ca9001d9e71.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692070281593/262b70b1-b4c1-4615-b8be-dec0cd0d07c8.png?auto=compress,format&format=webp align="left")

**Step 6: Saving and Initiating the Project**

1. Scroll down to "Save" and store the project configuration.
    
2. Initiate the build process by clicking "Build Now."
    

Jenkins will proceed to execute the configured build stages. It will employ the **"docker-compose up -d"** command to activate containers as specified in the **docker-compose.yml** file. Subsequently, it will perform cleanup by discontinuing and removing those containers, all facilitated through the "docker-compose down" command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692071241604/301708c6-971c-463d-b09d-9da2e44d1f0b.png?auto=compress,format&format=webp align="left")