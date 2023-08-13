---
title: "#Day20: Docker  Cheat sheet  for DevOps Engineers."
datePublished: Sun Aug 13 2023 05:05:04 GMT+0000 (Coordinated Universal Time)
cuid: cll8zfaa8000709mnaegj7nyd
slug: day20-docker-cheat-sheet-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691902046729/53f2b7e6-ee69-4a85-81db-95e56b485b80.png
tags: docker, docker-compose, docker-images, 90daysofdevops

---

Docker is a powerful tool in DevOps workflows. Here's a set of detailed commands that cover various aspects of using Docker in a DevOps context:

### **1\. Working with Images:**

* **Pull an Image:**
    
    ```plaintext
    docker pull image-name:tag
    ```
    
* **Build an Image from Dockerfile:**
    
    ```plaintext
    docker build -t image-name:tag path/to/Dockerfile-directory
    ```
    
* **List Images:**
    
    ```plaintext
    docker images
    ```
    
* **Remove an Image:**
    
    ```plaintext
    docker rmi image-id
    ```
    

### **2\. Running Containers:**

* **Run a Container:**
    
    ```plaintext
    docker run -it image-name:tag
    ```
    
* **Run a Detached Container:**
    
    ```plaintext
    docker run -d image-name:tag
    ```
    
* **Run with Port Mapping:**
    
    ```plaintext
    docker run -p host-port:container-port image-name:tag
    ```
    
* **Run with Environment Variables:**
    
    ```plaintext
    docker run -e VARIABLE_NAME=value image-name:tag
    ```
    

### **3\. Container Management:**

* **List Running Containers:**
    
    ```plaintext
    docker ps
    ```
    
* **List All Containers (including stopped):**
    
    ```plaintext
    docker ps -a
    ```
    
* **Start a Stopped Container:**
    
    ```plaintext
    docker start container-id
    ```
    
* **Stop a Running Container:**
    
    ```plaintext
    docker stop container-id
    ```
    
* **Restart a Container:**
    
    ```plaintext
    docker restart container-id
    ```
    
* **Remove a Container:**
    
    ```plaintext
    docker rm container-id
    ```
    

### **4\. Networking:**

* **Create a Custom Network:**
    
    ```plaintext
    docker network create network-name
    ```
    
* **Run a Container on a Specific Network:**
    
    ```plaintext
    docker run --network network-name image-name:tag
    ```
    

### **5\. Volumes:**

* **Create a Volume:**
    
    ```plaintext
    docker volume create volume-name
    ```
    
* **Run a Container with a Volume:**
    
    ```plaintext
    docker run -v volume-name:/path/in/container image-name:tag
    ```
    

### **6\. Docker Compose:**

* **Run Services Defined in docker-compose.yml:**
    
    ```plaintext
    docker-compose up
    ```
    
* **Stop and Remove Services:**
    
    ```plaintext
    docker-compose down
    ```
    

### **7\. System Cleanup:**

* **Prune Unused Resources:**
    
    ```plaintext
    docker system prune
    ```
    
* **Remove All Stopped Containers:**
    
    ```plaintext
    docker container prune
    ```
    
* **Remove Dangling Images:**
    
    ```plaintext
    docker image prune
    ```
    

Remember that these commands provide a solid foundation for using Docker in a DevOps environment. As your requirements evolve, you might need to explore more advanced Docker features and workflows to optimize your DevOps processes.