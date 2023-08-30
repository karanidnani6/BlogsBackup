---
title: "#Day28: Jenkins Agents"
datePublished: Wed Aug 30 2023 08:53:37 GMT+0000 (Coordinated Universal Time)
cuid: cllxi2oxt000209kzayyq8pfo
slug: day28-jenkins-agents
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693372069547/0856857a-8f53-4831-9807-3289b26904ab.png
tags: jenkins, 90daysofdevops, jenkinsmasterslave

---

### 🚀 **Exploring Jenkins: Master and Agent** 🚀

Are you ready to dive into the world of Jenkins? 🌐 Well, you're in the right place! In this blog, we're going to talk about the heart and soul of Jenkins - the Jenkins Master and its trusty sidekick, the Jenkins Agent. 🕵️‍♂️

### **Jenkins Master (Server) 🧙‍♂️**

Picture the Jenkins Master as the supreme commander of your Jenkins world. 🌟 This server holds all the key configurations, making it the control tower 🗼 that orchestrates all the workflows defined in your pipelines. From scheduling jobs to monitoring their progress, the Jenkins Master is your go-to hero. 🦸‍♂️

### **Jenkins Agent 🤖**

Now, meet the Jenkins Agent! 🤝 This Agent isn't a secret spy, but rather a machine or container that partners with the Jenkins Master to execute the steps defined in a job. 🏃‍♂️ Every Jenkins job needs an Agent buddy to do the heavy lifting. 🏋️‍♂️ Each Agent has a unique label, helping Jenkins identify who's who in the Jenkinsverse. 🏷️

When you hit that Jenkins job trigger button on the Master, all the action takes place on the Agent node configured for that job. It's like a dynamic duo, working together to get things done! 🦸‍♂️🤖

### **Scaling Up Your Jenkins Game 📈**

For small teams with a handful of projects, a single Jenkins installation might do the trick. But as your empire grows, you'll want to level up your Jenkins game. That's where the "master to agent connection" comes into play. 🌐

Instead of cramming everything on one system, you can enlist Agents to handle job executions while the Master remains the UI wizard 🧙‍♂️ and control node. It's like having a team of superheroes to tackle your tasks! 🦸‍♂️💼

### **Pre-requisites 🛠️**

Before embarking on your Jenkins journey, let's talk pre-requisites. If you're starting with a fresh Ubuntu 22.04 Linux installation, here's your checklist:

1. **Java**: Install Java on your system. Make sure it's the same version as your Jenkins Master server. ☕
    
2. **Docker**: Get Docker up and running. It's like your Agent's superpower suit! 🐳
    

Remember, while creating an Agent, don't forget about permissions and ownership for Jenkins users. We want harmony in our Jenkins universe! 🤝🔒

So there you have it, a brief tour of the Jenkins Master and Agent dynamic duo. Stay tuned for more Jenkins adventures! 🌠 Until next time, happy building! 🏗️🚀

# Task-01

* Create an agent by setting up a node on Jenkins
    
* Create a new AWS EC2 Instance and connect it to master(Where Jenkins is installed)
    
* The connection of master and agent requires SSH and the public-private key pair exchange.
    
* Verify its status under "Nodes" section.
    

step -1: Create EC2 instances - Jenkins-server, Jenkins-agent

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693009576129/75e7c5bc-d784-430e-bc80-9528fdb029e0.png?auto=compress,format&format=webp align="left")

Step 2: Generate SSH keys on “Jenkins-Master” using the **“ssh-keygen”** command\*\*.\*\*

step 3: Now go to the **“.ssh”** folder and there will be public and private key in Jenkins Master server - **id\_**[**rsa.pub**](http://rsa.pub/) **& id\_rsa**

**COPY**

```plaintext
cd .ssh
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693010023204/4d888265-5fbe-47fb-8ffc-e5c30e633feb.png?auto=compress,format&format=webp align="left")

Step 4: Go to the Jenkins agent server , Add the public key from “Jenkins-Master” to “Jenkins-agent-1” under location “.ssh/authorized\_keys”

In Jenkins master : Copy the public\_key

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693010232224/3a51a9c7-1890-425e-9444-6a1c6883b0f8.png?auto=compress,format&format=webp align="left")

In Jenkins agent :

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693010277987/e20d0b1b-2f13-4a4d-b471-2c95573b2751.png?auto=compress,format&format=webp align="left")

Paste the public\_key in the authorized\_keys.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693010164034/4e33f024-c589-4800-8678-e4a3835a3b83.png?auto=compress,format&format=webp align="left")

step 5: Now, go to the Jenkins dashboard, and click on **“Manage Jenkins”.**

step 6: Now, click on **“ Nodes ”**

step 7: Click on new-Node.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693385373331/f9926b16-19ab-4476-bf3a-1bb074aadb96.png align="center")

step 8: Add details to add second node, accordingly.

step 9: Add Credentials &gt;&gt; kind: SSH with private\_key & enter the details accordingly.

step 10: To enter the private\_key, In Jenkin-Master:

**COPY**

```plaintext
cat id_rsa
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693385536306/84289347-09c3-4d0c-8a0f-7cffb712b90f.png align="center")

Copy & Paste the Private\_key

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693011003320/5682b35d-6387-4d3b-917a-8c13784f2f01.png?auto=compress,format&format=webp align="left")

step 11: Connection is Successfull.

# **Task-02**

* Run your previous Jobs (which you built on Day 26, and Day 27) on the new agent
    
* Use labels for the agent, your master server should trigger builds for the agent server.
    

step 12: Now build a job, here **restrict the job to the particular agent.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693011643254/fcea3cd1-1061-4bde-96ae-fa1aef749353.png?auto=compress,format&format=webp align="left")

step 13: Build Now

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693011595598/84eda24d-daae-4ac1-aa2a-4086d2fef45c.png?auto=compress,format&format=webp align="left")