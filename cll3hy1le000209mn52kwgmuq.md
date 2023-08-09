---
title: "#Day17:Docker Project for DevOps Engineers."
datePublished: Wed Aug 09 2023 08:56:55 GMT+0000 (Coordinated Universal Time)
cuid: cll3hy1le000209mn52kwgmuq
slug: day17docker-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691557866490/fd6806aa-9f9e-4060-a8c1-665aea372af4.png
tags: docker, docker-container, 90daysofdevops

---

### 🐳 **Diving into Docker: Building a Container with Dockerfile** 🚀

Hey there, tech explorers! 👋 Have you ever wondered how to package up your cool apps so they can roam freely on any computer? Well, that's where Docker comes in, like a magic backpack for your software! 🎩✨ Let's embark on a journey to discover the wonders of Dockerfiles and containers! 🌍

### **What's Docker and Containers?**

Picture this: you want to send a friend a cake recipe. Instead of mailing the whole cake, you send a recipe card. Docker does something similar with apps! It helps bundle your app's ingredients and instructions into a "container". These containers are like portable homes for your apps – they have all the necessities packed in, so they run smoothly no matter where they land. 🏡📦

### **Meet the Dockerfile: Your App's Recipe**

Just like a cake recipe has step-by-step instructions, a Dockerfile guides Docker on how to cook up your app's container. It's a simple text file that says things like "Use this base image", "Run these commands", and "Include these files". Think of it as a magic spell to conjure your app's container! 📜✨

### **Let's Make a Web App Container!**

Imagine you're baking a website cake. You'd need ingredients like a web server (flour) and your website files (toppings). Here's a simplified Dockerfile recipe for your Node.js web app:

```plaintext
# Use an official Node.js image as the base
FROM node:14

# Create and set the working directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json to the container
COPY package*.json ./

# Install app dependencies
RUN npm install

# Copy the rest of your app's files
COPY . .

# Specify the command to run your app
CMD ["node", "app.js"]
```

### **Baking Time!**

With your Dockerfile ready, it's time to bake the container cake! Open a terminal, navigate to your app's directory, and run:

```plaintext
docker build -t my-web-app .
```

This command tells Docker to build an image named `my-web-app` using the current directory (`.`). Docker follows your Dockerfile's recipe to create the container image. 🍰👩‍🍳

### **Let's Taste the Web App!**

Now that your image is ready, let's fire up a container:

```plaintext
docker run -p 8080:80 my-web-app
```

This command runs your `my-web-app` image as a container. It maps port `8080` on your computer to port `80` inside the container. Open a web browser and go to [`http://localhost:8080`](http://localhost:8080) to see your app live! 🌐🥳

### **Sharing is Caring: Push to Docker Hub**

Imagine sharing your cake masterpiece with the world! You can do the same with your app container by pushing it to Docker Hub.

1. Create an account on Docker Hub.
    
2. Tag your image:
    

```plaintext
docker tag my-web-app your-docker-id/my-web-app
```

1. Log in to Docker Hub:
    

```plaintext
docker login
```

1. Push your image:
    

```plaintext
docker push your-docker-id/my-web-app
```

Now anyone can taste your app by pulling it from Docker Hub! 🍰🌍

And there you have it! 🎉 With Docker and Dockerfiles, you've become a container sorcerer, packaging apps like a pro. So go ahead, whip up containers for your various apps, and watch them sail smoothly on any computer's sea! ⛵🌊 Happy coding and container crafting! 🚢👩‍💻👨‍💻