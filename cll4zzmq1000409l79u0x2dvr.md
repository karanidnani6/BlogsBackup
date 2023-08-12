---
title: "#Day18:Docker Compose for DevOps Engineers"
datePublished: Thu Aug 10 2023 10:09:48 GMT+0000 (Coordinated Universal Time)
cuid: cll4zzmq1000409l79u0x2dvr
slug: day18docker-compose-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691648118778/83a9e746-ecce-45fd-9e94-cd59b5651fb2.jpeg
tags: docker, docker-compose, 90daysofdevops

---

### 🐳 **Setting Sail with Docker Compose: The Magic of YAML 🚢**

Hey there, tech adventurers! 🌊 Ready to explore the world of Docker Compose and its secret ingredient, YAML? 🧙‍♂️ Well, grab your virtual compass because we're about to embark on a journey that'll make managing multiple containers feel like a breeze! 🌬️

**📦 What's Docker Compose All About?**

Picture this: you're hosting a party with various activities – a dance floor, a food corner, and even a cozy chill-out zone. Docker Compose is like your party planner, helping you manage all these different things at once. 🎉

But wait, there's more! 🎈 You don't just manage the party; you also create a detailed plan (Docker Compose YAML file) that tells your planner how to set up everything.

**🧙‍♂️ YAML: The Magical Blueprint**

Okay, let's talk about YAML – your secret weapon in this adventure. Think of YAML as a language that speaks to computers in a way they actually understand. It's like giving your computer a magical spell to follow. ✨

But here's the best part: YAML isn't some cryptic code; it's super friendly! It's like writing down your party plans in a way that even your non-tech-savvy friend would get. And guess what? YAML files end with .yml or .yaml. 📝

### Task-1

Learn how to use the docker-compose.yml file, to set up the environment, configure the services and links between different containers, and also to use environment variables in the docker-compose.yml file.

let's dive into Task-1 and understand how to use the `docker-compose.yml` file to set up your environment, configure services, create links between containers, and use environment variables.

**Step 1: Create the docker-compose.yml File**

The `docker-compose.yml` file is like a blueprint for your multi-container setup. It's written in YAML format and guides Docker Compose on what to do. You can create it using a text editor of your choice.

**Step 2: Define Services**

In your `docker-compose.yml` file, you define the services you want to run. A service is essentially a container. For example, let's consider you're building a web app (`web` service) and a database (`db` service).

```plaintext
version: '3'  # The version of Docker Compose file format

services:
  web:
    image: my-awesome-app:latest
    # other configurations for the web service

  db:
    image: my-cool-database:latest
    # other configurations for the db service
```

**Step 3: Set Up Links Between Containers**

If your services need to communicate with each other, you can set up links between them. For instance, if your web app needs to connect to the database, you can create a link from the `web` service to the `db` service.

```plaintext
version: '3'

services:
  web:
    image: my-awesome-app:latest
    links:
      - db  # Linking to the db service

  db:
    image: my-cool-database:latest
```

**Step 4: Using Environment Variables**

Environment variables provide a way to pass configuration information to containers. Let's say your database service needs a root password.

```plaintext
version: '3'

services:
  web:
    image: my-awesome-app:latest

  db:
    image: my-cool-database:latest
    environment:
      - MYSQL_ROOT_PASSWORD=secretpassword
```

With this setup, the `db` service will have the `MYSQL_ROOT_PASSWORD` environment variable set to `secretpassword`.

**Step 5: Bringing It All Together**

Once your `docker-compose.yml` file is ready, you can use the `docker-compose` command to bring your multi-container setup to life. For example, `docker-compose up` will start all the defined services based on the configuration you've provided.

In essence, Task-1 revolves around creating a clear, organized plan in the `docker-compose.yml` file. You define services, set up connections between containers, and pass essential configuration information using environment variables. It's like creating a detailed party plan for Docker to execute, ensuring your containers work harmoniously together in the tech fiesta! 🎉🐳

### Task-2

Let's walk through Task-2 step by step:

**Step 1: Pull and Run the Docker Image**

1. Pull a Docker image from a public repository like Docker Hub:
    
    ```plaintext
    docker pull image-name:tag
    ```
    
2. Run the container as a non-root user by adding your user to the `docker` group:
    
    ```plaintext
    sudo usermod -aG docker $USER
    ```
    
3. Reboot your machine for the changes to take effect:
    
    ```plaintext
    sudo reboot
    ```
    
4. Once your machine is back up, start the container:
    
    ```plaintext
    docker run -d --name my-container image-name:tag
    ```
    

**Step 2: Inspect Container's Processes and Ports**

1. Use the `docker inspect` command to get detailed information about the container:
    
    ```plaintext
    docker inspect my-container
    ```
    
2. In the output, you'll find details about the container's configuration, networking, and more. Look for `"State"` to check if the container is running, and `"Ports"` to see the exposed ports.
    

**Step 3: View Container Logs**

1. To view the log output of the container, use the `docker logs` command:
    
    ```plaintext
    docker logs my-container
    ```
    
2. This will display the logs generated by the processes running inside the container.
    

**Step 4: Stop and Start the Container**

1. To stop the running container, use the `docker stop` command:
    
    ```plaintext
    docker stop my-container
    ```
    
2. To start the container again, use the `docker start` command:
    
    ```plaintext
    docker start my-container
    ```
    

**Step 5: Remove the Container**

1. Once you're done with the container, you can remove it using the `docker rm` command:
    
    ```plaintext
    docker rm my-container
    ```
    
2. This will clean up the resources associated with the container.
    

And there you have it! You've successfully pulled a Docker image, ran it as a non-root user, inspected its processes and ports, viewed its logs, and managed its lifecycle using Docker commands. It's like orchestrating your own tech show with containers! 🎉🐳

### How to run Docker commands without sudo?

**Step 1: Install Docker and Update System** Ensure that Docker is installed on your system and your system is up to date. If you've already completed this step, you're all set for the next ones.

**Step 2: Grant User Docker Permissions** Run the following command to add your user to the `docker` group, granting the necessary permissions:

```plaintext
sudo usermod -aG docker $USER
```

**Step 3: Reboot Your Machine** After adding your user to the `docker` group, it's important to reboot your machine to apply the changes effectively:

```plaintext
sudo reboot
```

**Step 4: Run Docker Commands** Once your system restarts, you'll be able to run Docker commands without needing `sudo`. You've successfully unlocked the power of Docker without any extra chants!

### **Wrapping Up Docker Adventures for DevOps Explorers! 🚀**

You've rocked Docker's world so far! From crafting Docker files to sharing them, you've leveled up your DevOps game. But guess what? There's still cool stuff ahead! 🎉

Meet Docker Compose – it's like a maestro for containers. Imagine orchestrating a container symphony with a magic YAML wand! You'll create, connect, and rule your container universe. 🎵🪄

Now, peek into pulling public images, making containers dance on your machine, and even giving them new roles – all without complex spells! ✨

Wait, there's more! Say goodbye to the "sudo" spell. With a simple reboot, you'll be casting Docker commands freely – no more "sudo" mutterings! 🧙‍♂️

So, fellow explorer, keep the curiosity alive! Your Docker adventure has just begun. Let's keep exploring, one tech discovery at a time! 🌟🐳