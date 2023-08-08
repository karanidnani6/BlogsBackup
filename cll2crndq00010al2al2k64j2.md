---
title: "#Day16:Docker for DevOps Engineers."
datePublished: Tue Aug 08 2023 13:44:12 GMT+0000 (Coordinated Universal Time)
cuid: cll2crndq00010al2al2k64j2
slug: day16docker-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691473548474/931cfe68-6d92-4525-b4d6-1db1bb8c5042.png
tags: docker, containers, 90daysofdevops

---

### 🐳 Docker for DevOps Engineers 🚀

Hey there, fellow DevOps Engineers! 👋 Today, we're diving into the wonderful world of Docker, the magical software platform that makes our lives easier when it comes to building, testing, and deploying applications! 🎉

### What's Docker all about? 🤔

Well, Docker is like a magic box 📦 that contains everything your application needs to run smoothly. It wraps up your software, libraries, system tools, code, and runtime into neat little packages called containers 📦🏃. These containers are super consistent and can run anywhere, so you don't have to worry about compatibility issues anymore! 💯

### Tasks for Today! 📝

First things first, make sure you've already installed Docker . Once you're all set, let's jump into some fun exercises! 🎯

1. **docker run**: This command is your best buddy when it comes to starting a new container and playing with it through the command line. Try it out with `docker run hello-world` 🌟. It's like saying "Hello, Docker!" to the world! 😄
    
    Example:
    
    ```plaintext
    docker run hello-world
    ```
    
    Output:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691483307551/c131e9c8-423a-4035-a9ce-58c574b80975.png align="center")
    
2. **docker inspect**: If you want to know all the nitty-gritty details about a container or image, just use `docker inspect`. It's like peeking inside the container to see what's happening! 🔍
    
    Example:
    
    ```plaintext
    docker inspect my_container
    ```
    
    Output: Lots of detailed information about the container 📋
    
3. **docker port**: Need to find out the port mappings for a container? Use `docker port`. It's like a treasure map 🗺️ that leads you to the right door! 🚪
    
    Example:
    
    ```plaintext
    docker run -d -p 8080:80 my_web_app
    docker port my_web_app
    ```
    
    Output:
    
    ```plaintext
    80/tcp -> 0.0.0.0:8080
    ```
    
4. **docker stats**: Monitoring is essential, right? Check out `docker stats` to get a sneak peek at how your containers are using resources. It's like a health checkup for your app! 💓
    
    Example:
    
    ```plaintext
    docker stats my_container
    ```
    
    Output:
    
    ```plaintext
    CONTAINER ID   NAME         CPU %     MEM USAGE / LIMIT     MEM %     NET I/O     BLOCK I/O   PIDS
    abcdef123456   my_container  0.50%     100.2MiB / 1GiB     10.02%    1.5kB / 0B  7.25MB / 0B  20
    ```
    
5. **docker top**: Wondering what's happening inside a container? `docker top` gives you a peek at the processes running inside. It's like being a detective 🔍 in the container world!
    
    Example:
    
    ```plaintext
    docker top my_container
    ```
    
    Output:
    
    ```plaintext
    PID    USER     TIME      COMMAND
    1234   root     0:00      nginx
    5678   root     0:00      node app.js
    ```
    
6. **docker save and docker load**: When you want to share your awesome images with others, `docker save` comes to the rescue. It saves an image to a tar archive. And when you want to load an image from a tar archive, use `docker load`. It's like mailing packages 📦 to your friends!
    
    Example:
    
    ```plaintext
    docker save -o my_image.tar my_image:latest
    docker load -i my_image.tar
    ```
    

That's a wrap! 🎬

Today, we covered some basic but powerful Docker commands. Docker makes life easier by keeping your applications contained and ready to run wherever you need them. 🏃💨 So, go ahead and experiment with these commands to become a Docker expert! You'll find it incredibly handy in your DevOps journey! 🚀