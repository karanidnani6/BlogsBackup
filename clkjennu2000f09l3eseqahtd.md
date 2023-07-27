---
title: "#Day7: Understanding Package Manager and SystemCtl"
datePublished: Wed Jul 26 2023 07:29:28 GMT+0000 (Coordinated Universal Time)
cuid: clkjennu2000f09l3eseqahtd
slug: day7-understanding-package-manager-and-systemctl
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690352322287/315dfa77-ae1a-4b6c-84e5-71092ce210ea.png
tags: docker, package, devops, jenkins, 90daysofdevops

---

### 🐧📦 All About Package Managers in Linux! 🚀

Hey there, fellow Linux explorers! 🤗 Today, we're diving into the world of package managers in Linux. 🌍 If you've ever wondered how software gets installed and managed on your Linux system, you're in the right place! 🎉

### 🤔 What is a Package Manager?

Imagine you want to download and install new apps or programs on your computer. In the Linux world, we have these cool tools called "Package Managers" that make this process super easy! 😎 A package manager is like a magic genie 🧞‍♂️ that fetches, installs, and updates software for you with just a few simple commands! 💻🔮

### 📦 What is a Package?

A package is like a neatly wrapped gift box 🎁 that contains all the necessary files, code, and instructions for a software application to work smoothly on your Linux system. 🎈 It's like a little software package ready to be delivered to your computer doorstep! 🚚💨

### 💼 Different Kinds of Package Managers:

Linux has several package managers, each with its unique style and preferences! Let's look at two popular ones:

1. 🧶 Debian Package Manager (dpkg) & Advanced Package Tool (APT): APT is like a dynamic duo, working together to manage packages like superheroes! 🦸‍♂️🦸‍♀️ They are the dynamic duo found in Debian-based distributions like Ubuntu, Linux Mint, and more. With APT, you can easily install, update, and remove software. Just type a simple command, and it'll handle the rest! 👾
    
2. 🐍 Python Package Manager (pip): If you're a Python developer 🐍, you'll love pip! It's like a personal assistant 🧞 for Python packages. Whenever you need to add a new Python library or update an existing one, pip will make it happen in a snap! 💫
    
3. 📦 Red Hat Package Manager (RPM): RPM is another handy package manager used in Red Hat-based distributions like Fedora, CentOS, and others. It's like a trusty delivery service 🚚, efficiently managing software packages on your system. RPM makes sure everything is in its place and runs smoothly! 🧰
    
4. 🎁 Snapcraft: Snapcraft brings the gift of universal packages! 🎁 It's like a Swiss Army Knife 🇨🇭 of package managers, working across various Linux distributions. Snap packages come with all the dependencies they need, making software installation a breeze! 🌬️💨
    

Remember, each Linux distribution may have its unique package manager, but they all share the same goal: to make software management a piece of cake! 🍰

## 🐧📦 How to Install Docker and Jenkins on Ubuntu using Package Managers! 🚀

Are you ready to supercharge your Ubuntu system with Docker and Jenkins? 🚀 In this guide, we'll walk you through the process of installing these powerful tools using package managers. Buckle up, and let's get started! 🌟

### 🐳 Installing Docker with APT:

Docker is like a magician for developers, allowing them to create, deploy, and run applications in containers. Let's use the APT package manager to install Docker on Ubuntu:

Step 1: Update Your Package List Open a terminal by pressing `Ctrl + Alt + T`, and let's update our package list to ensure we get the latest versions:

```plaintext
sudo apt update
```

Step 2: Install Docker Now, we can install Docker using the following command:

```plaintext
sudo apt install docker.io
```

Step 3: Verify Docker Installation To confirm that Docker is up and running, run this command:

```plaintext
docker --version
```

You should see the version number of Docker installed on your system. Congratulations! 🎉 Docker is now ready to create and manage containers on your Ubuntu system.

### 🔧 Installing Jenkins with APT:

Jenkins is a fantastic automation tool, perfect for continuous integration and continuous deployment (CI/CD) pipelines. Let's use APT to install Jenkins on Ubuntu:

📝 **Before We Begin:** Before installing Jenkins, let's make sure we have Java installed on our system. Jenkins relies on Java to run, so it's essential to have Java set up first.

Step 0: **Check Java Installation** To check if Java is already installed, open your terminal and run:

```plaintext
java -version
```

If you see the version information, great! You already have Java installed, and you can proceed to install Jenkins. 🎉 If not, no worries—we'll install it now.

Step 1: **Install Java** If you need to install Java, use the APT package manager to install OpenJDK, which is the most popular Java version for Linux systems:

```plaintext
sudo apt install openjdk-17-jre
java -version
```

Step 3: **Install Jenkins** It's time for Jenkins to shine! Use the APT package manager to install Jenkins:

```plaintext
 curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
   /usr/share/keyrings/jenkins-keyring.asc > /dev/null
 echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
   https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
   /etc/apt/sources.list.d/jenkins.list > /dev/null
 sudo apt-get update
 sudo apt-get install jenkins
```

🕐 Time to sit back and relax while Jenkins gets installed. ☕

Step 4: **Start and Enable Jenkins** Once Jenkins is installed, we need to start the service and make sure it automatically starts whenever you boot up your system:

```plaintext
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

🔌 Jenkins is now plugged in and ready to go!

Step 5: **Unlock Jenkins and Set Up** Now, let's access Jenkins through its web interface. Open your favorite web browser and enter this address: [`http://localhost:8080`](http://localhost:8080)

🔑 You'll be greeted with an admin password prompt. No worries, we've got you covered! To retrieve the password, run this command in the terminal:

```plaintext
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Copy the password and paste it into the Jenkins web page to unlock the magic of Jenkins! 🧙‍♂️

Step 6: **Jenkins Is All Yours!** Follow the on-screen instructions to customize your Jenkins setup, choose your favorite plugins, and create your admin user. 🛠️

🎉 Congratulations! You now have Jenkins up and running on your system! 🎉

🚀 **Time to Explore Jenkins's Power** Jenkins is your ultimate automation hero 🦸‍♂️🦸‍♀️, helping you build, test, and deploy your projects effortlessly. With Jenkins pipelines, you can automate complex tasks and focus on what matters most—your code! 💻🔍

**Task 1: Check Docker Status** First things first! Let's check if Docker is up and running on your system. Open your terminal and enter this command:

```plaintext
sudo systemctl status docker
```

You should see a detailed status report of the Docker service. If it shows "active" and "running," congrats! Docker is good to go. 🎉 If not, make sure you completed the Docker installation correctly before proceeding. 🐳💻

**Task 2: Stopping Jenkins Service** Now, let's get our hands on Jenkins! We'll stop the Jenkins service and see the difference before and after with screenshots. 📸

Before:

![Jenkins Service Running](https://example.com/before_jenkins_stop.png align="left")

To stop the Jenkins service, run this command:

```plaintext
sudo systemctl stop jenkins
```

After:

![Jenkins Service Stopped](https://example.com/after_jenkins_stop.png align="left")

Awesome! Jenkins is now stopped, and you can see the change in the status. 🛑✨

**Task 3: Understanding systemctl vs. service** You might have noticed that we used "systemctl" to manage Docker and Jenkins services. But wait, what about "service"? Let's find out! 🤔

"systemctl" and "service" are both used to control services on your system. However, "systemctl" is more modern and flexible, while "service" is a legacy command. 🏛️

* "systemctl": Used in systemd-based systems (like Ubuntu 16.04 and newer). It provides more advanced control and additional features.
    
* "service": Used in older sysvinit-based systems. It's simpler but doesn't offer all the functionalities of "systemctl."
    

In our tasks, we opted for "systemctl" because it's widely supported and recommended for newer systems. 🌟

🎉 **Congratulations!** You've successfully completed our tasks! 🏆🚀 By now, you should feel more confident with Docker, Jenkins, and managing services using "systemctl." It's time to embrace the power of automation and continuous integration with Jenkins! 🤖💻

Keep exploring, learning, and creating wonders in the tech world! 🌈 Happy coding! 🎈🎉