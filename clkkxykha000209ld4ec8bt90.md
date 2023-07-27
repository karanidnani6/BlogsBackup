---
title: "#Day9: Deep Dive in Git & GitHub for DevOps Engineers."
datePublished: Thu Jul 27 2023 09:17:36 GMT+0000 (Coordinated Universal Time)
cuid: clkkxykha000209ld4ec8bt90
slug: day9-deep-dive-in-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690436817306/5e47af1d-5b24-4cec-a336-4a4d836ae51b.jpeg
tags: github, git, devops, 90daysofdevops

---

### 🐙 What is Git and why is it important? 🌟

Hey there! 👋 Have you ever wondered how developers manage their code and work together on software projects? 🤔 That's where Git comes in! 🎉 Git is a version control system that helps developers track changes to their code over time. 📝 It allows them to collaborate effectively, work on different features simultaneously, and keep a history of all the changes made to the project. 🔄 This way, they can easily revert to previous versions if needed and avoid chaos when multiple people are working on the same codebase. 🙌

### 🌿 Difference Between Main Branch and Master Branch? 🌳

In the past, the default branch in Git was commonly named "master." However, this terminology has evolved to be more inclusive and respectful. So, nowadays, we often use the term "main" instead of "master" to refer to the primary branch of a Git repository. The "main" branch is the default branch where all the latest changes and updates come together. 🌈

### 🤝 Difference between Git and GitHub? 🏠

Git and GitHub are related but serve different purposes. Git is the version control system itself, while GitHub is a web-based hosting service for Git repositories. 🌐 Git helps you manage your code locally on your computer, while GitHub allows you to store and share your Git repositories with others over the internet. Think of Git as the engine that powers version control, and GitHub as the platform that provides a user-friendly interface and online collaboration features. 🚀

### 🏞️ How to create a new repository on GitHub? 🏗️

Creating a new repository on GitHub is a piece of 🍰! Just follow these simple steps:

1. 🔑 Make sure you have a GitHub account. If not, create one for free.
    
2. 📋 Once you're logged in, click on the "+" sign on the top-right corner, and select "New repository."
    
3. 📝 Give your repository a name and a short description. Choose whether it should be public (visible to everyone) or private (only visible to you and collaborators).
    
4. ✔️ Initialize the repository with a README file to give it a starting point.
    
5. 🎉 Click on the "Create repository" button, and voilà! Your new repository is ready to use. 🎊
    

### 🏠 Difference between local & remote repository? How to connect local to remote? 🌐

A local repository is the one stored on your personal computer, where you can work on your code and make changes. It helps you keep track of your progress and history while having complete control over the code. On the other hand, a remote repository is hosted on a server, often on platforms like GitHub, GitLab, or Bitbucket. It allows you to share your code with others and collaborate on projects together.

To connect your local repository to a remote one, follow these steps:

1. 🔗 First, create a new repository on GitHub (as explained earlier).
    
2. 📁 On your local machine, navigate to the folder where your code resides using the terminal or command prompt.
    
3. 📡 Add the remote repository URL to your local repository using the command:
    
    ```plaintext
    git remote add origin <remote_repository_url>
    ```
    
4. 🔄 Now, you can push your local repository to the remote using:
    
    ```plaintext
    git push -u origin main
    ```
    
    This pushes the changes from your local "main" branch to the remote repository.
    

And that's it! Your local and remote repositories are now connected, and you can easily collaborate with others and sync your code between the two. 🤝

### **📋 Tasks 1:**

### Set your user name and email address, which will be associated with your commits.

To associate your user name and email address with your commits in Git, you'll need to configure your global settings. This step is essential because it helps identify who made each commit in a project. Follow the simple steps below to set up your user name and email address:

Step 1: Open Git Bash (for Windows) or Terminal (for macOS/Linux).

Step 2: Type the following commands, replacing "Your Name" with your actual name and "[**youremail@example.com**](mailto:youremail@example.com)" with your email address. Make sure to use the email associated with your GitHub account.

```plaintext
git config --global user.name "Your Name"
git config --global user.email youremail@example.com
```

Step 3: Press Enter after typing each command to execute them.

That's it! 🎉 Now your user name and email address are associated with your commits whenever you make changes and commit them using Git. From now on, your contributions to repositories will be linked to this information, making it easier for others to recognize your work.

### **📋 Tasks 2:**

1. ### Create a repository named "Devops" on GitHub
    

Create a "Devops" Repository on GitHub

1. Sign in to your GitHub account or create one if you don't have it already.
    
2. Click on the "+" sign in the top right corner and select "New repository."
    
3. Enter "Devops" as the repository name.
    
4. You can add an optional description if you like.
    
5. Choose if you want the repository to be public or private.
    
6. Initialize the repository with a README file (you can leave this option unchecked as we'll add our own file).
    

Click on the "Create repository" button to create the "Devops" repository on GitHub.

1. ### Connect your local repository to the repository on GitHub.
    

Connect Your Local Repository to the Repository on GitHub

1. Open Git Bash (for Windows) or Terminal (for macOS/Linux).
    
2. Navigate to the folder where you want to create the "Devops" repository. Use the "cd" command to change directories.
    
3. To clone the remote repository to your local machine, use the following command, replacing "your\_username" with your GitHub username:
    

```plaintext
git clone https://github.com/your_username/Devops.git
```

1. ### Create a new file in Devops/Git/Day-02.txt & add some content to it
    

1. Navigate into the "Devops" folder using the "cd" command.
    
2. Create a new folder named "Git" inside the "Devops" folder:
    

```plaintext
mkdir Git
```

1. Move into the "Git" folder:
    

```plaintext
cd Git
```

1. Create a new file named "Day-02.txt" inside the "Git" folder. You can use any text editor to create the file:
    

```plaintext
touch Day-02.txt
```

1. Open "Day-02.txt" and add some content to it. You can use the text editor of your choice.
    

1. ### Push your local commits to the repository on GitHub
    
    ```plaintext
    git push origin main
    ```
    
    (Note: If you encountered any issues during the push, make sure you have write access to the repository and that you correctly configured your GitHub credentials.)
    
    And there you go! 🎉 Your local changes are now pushed to the "Devops" repository on GitHub. You can visit your GitHub repository to see the "Day-02.txt" file with the content you added. Happy coding! 💻😄