---
title: "#Day8: Basic Git & GitHub for DevOps Engineers."
datePublished: Wed Jul 26 2023 13:53:09 GMT+0000 (Coordinated Universal Time)
cuid: clkjsd2qq001a09mmfv5u2x94
slug: day8-basic-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690366292617/abed4c26-cc10-49ee-ae26-36c5a3e9977c.jpeg
tags: cloud, github, version-control, git, 90daysofdevops

---

🌟 Demystifying Git and GitHub: Your Journey to Version Control! 🌟

Hey there, tech enthusiasts! 👋 Are you ready to embark on a fun-filled adventure to discover the world of Git and GitHub? 🚀 Let's dive in!

### 🎉 What is Git? 🎉

Git is like a superhero for developers 🦸‍♂️ - it helps them track changes in their code and collaborate with ease! It's a version control system that acts as a time machine ⏰, allowing developers to go back in time to previous versions of their projects. So, if something goes wrong, fear not! Git has your back!

### 🐙 What is GitHub? 🐙

Think of GitHub as a cosmic hub 🌌 where developers gather to work on their projects. It's a web-based platform that hosts Git repositories, making it super easy for teams to collaborate and contribute to the same project. GitHub adds a layer of social interaction too! You can follow other developers, and star repositories you love, and even raise issues if you spot any bugs 🐛.

### 🗂️ What is Version Control? 🗂️

Version control is like an organized filing system 📂 for your code. It keeps track of changes made over time, allowing developers to collaborate seamlessly. With version control, you can see who made what changes, when they did it, and even why! It's like magic for team collaboration ✨.

### 🔄 How many types of version controls do we have? 🔄

There are two main types of version control systems: centralized and distributed.

1. Centralized Version Control 🎯: In a centralized system, there's a single, central repository 🏢 where all the code lives. Developers checkout files from this central hub, work on them locally and then commit changes back to the central repository. It's like checking out a library book 📚 and returning it once you're done.
    
2. Distributed Version Control 🌐: Distributed version control takes collaboration to the next level! In this system, every developer has their local repository 🏠. They can work independently, commit changes locally, and even create branches 🌿 to experiment. When they're ready, they can push their changes to the remote repository, like GitHub, and share them with the team. It's like having your private playground and then merging the best ideas into the main project.
    

### 💡 Why use distributed version control over centralized version control? 💡

Great question! 🤔 Distributed version control offers several advantages over the traditional centralized approach:

1. **Faster and Safer Collaboration:** With local repositories, developers can work offline and commit changes more frequently. This speeds up collaboration and reduces the risk of losing work.
    
2. **Branching Bliss:** Creating branches in distributed version control allows developers to experiment without affecting the main project. It's like having multiple parallel universes for trying out different ideas!
    
3. **No Single Point of Failure:** In centralized version control, if the central server goes down, it's a disaster! But with distributed systems, every developer has a complete copy of the project, so there's no single point of failure.
    
4. **Open Source Awesomeness:** Many popular open-source projects, like Linux 🐧 and Node.js 🚀, thrive on distributed version control platforms like GitHub. It fosters a sense of community and encourages more contributions!
    

That's a wrap! 🎬 Now you have a solid understanding of Git, GitHub, version control, and why distributed version control rocks! Happy coding 🚀 and may the commits be ever in your favor! 🌟

## **Task 1: Create a New Repository on GitHub and Clone It 🐣**

1. 🖥️ **Step 1: Set Up Your GitHub Account** 📝 If you haven't already, go to [**https://github.com**](https://github.com) and create a free account. It'll be your coding wonderland! 🏰
    
2. 🎉 **Step 2: Creating Your First Repository** 🚀 Click on the '+' sign in the top right corner and select "New repository." Give it a cool name and maybe a description. You can keep it public or private, it's your choice! 🔍
    
3. 🔗 **Step 3: Copy the Repository URL** 📋 Once your repository is created, you'll see a green button that says "Code." Click on it, and copy the repository URL. This will be essential for cloning your repository to your local machine! 🗝️
    
4. 💻 **Step 4: Clone the Repository Locally** 🚚 Open your terminal or command prompt on your local machine, navigate to the folder where you want to save your project, and type:
    
    ```plaintext
    git clone <repository_url>
    ```
    
    Replace `<repository_url>` with the URL you copied earlier. Hit Enter, and voilà! Your repository is now on your computer! 🎉
    

## **📝 Task 2: Making Changes and Committing Them with Git 🖋️**

1. 📂 **Step 1: Add Your Changes** ➕ Open the project folder on your computer and make some exciting changes to your files using your favorite code editor. Maybe add a cool feature or a fun comment! 😎
    
2. 💾 **Step 2: Stage the Changes** 🚦 Once you're satisfied with your changes, go back to the terminal and navigate to your project folder. Use this command to stage your changes:
    
    ```plaintext
    git add .
    ```
    
    The dot `.` means all changes in the current directory will be staged. You can also use `git add <filename>` to stage-specific files.
    
3. 📝 **Step 3: Commit Your Changes** 📌 It's time to commit your changes and create a snapshot of your work. Use this command:
    
    ```plaintext
    git commit -m "Your commit message here"
    ```
    
    Write a meaningful message in place of "Your commit message here." This will help you remember what you did in this commit! 🗒️
    

## **🚀 Task 3: Pushing Changes back to GitHub 🚀**

1. 🚀 **Step 1: Push Your Commits** 🔝 You've committed your changes locally. Now it's time to push them to GitHub, so the world can see your brilliance! Use this command:
    
    ```plaintext
    git push origin master
    ```
    
    "origin" is the remote repository on GitHub, and "master" is the branch you're pushing to. It's like launching your work into orbit! 🚀
    
2. 🎉 **Step 2: Celebrate!** 🎉 Congratulations! 🎊 You've successfully pushed your changes back to GitHub. Go to your repository on GitHub, and you'll see all your awesome changes there! 🌟
    

Now, you're a GitHub superhero! 🦸‍♂️ You've created a repository, cloned it, made changes, committed them with Git, and pushed them back to GitHub. Keep exploring and experimenting – the tech world is full of wonders! 🌈 Happy coding! 🚀