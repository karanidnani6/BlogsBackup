---
title: "Day 58: Ansible Playbooks"
datePublished: Wed Jan 10 2024 05:21:00 GMT+0000 (Coordinated Universal Time)
cuid: clr7c1kia000209l91qzwfagl
slug: day-58-ansible-playbooks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704861990810/b7e0937b-c980-4a0c-859e-d82c1aa74b35.png

---

Ansible playbooks run multiple tasks, assign roles, and define configurations, deployment steps, and variables. If you’re using multiple servers, Ansible playbooks organize the steps between the assembled machines or servers and get them organized and running in the way the users need them to. Consider playbooks as the equivalent of instruction manuals.

### Task-01

* Write an ansible playbook to create a file on a different server
    
* Write an ansible playbook to create a new user.
    
* Write an ansible playbook to install docker on a group of servers
    

### **Key components of an Ansible playbook include:**

1. **Hosts:** Specifies the target hosts or groups on which the playbook tasks will be executed.
    
2. **Tasks:** Describes a list of actions or operations to be performed on the target hosts. Each task typically corresponds to an Ansible module that carries out a specific action, such as installing a package, copying files, or restarting services.
    
3. **Plays:** A play is a set of tasks that are executed on a specific group of hosts. Plays allow you to organize and structure your automation tasks logically.
    
4. **Handlers:** Handlers are tasks that respond to specific events triggered by other tasks in the playbook. For example, restarting a service after a configuration file change.
    
5. **Variables:** Ansible playbooks can use variables to make them more flexible and reusable. Variables can be defined within the playbook or in external files.
    

### Basic Syntax:

```plaintext
---
- name: Playbook Name
  hosts: target_hosts
  become: yes  # Optional, to execute tasks with elevated privileges
  vars:
    variable_name: variable_value  # Optional, define variables for the playbook

  tasks:
    - name: Task 1 Description
      module_name:
        parameter1: value1
        parameter2: value2

    - name: Task 2 Description
      module_name:
        parameter1: value1
        parameter2: value2

  handlers:
    - name: Handler 1
      module_name:
        parameter1: value1
        parameter2: value2

    - name: Handler 2
      module_name:
        parameter1: value1
        parameter2: value2
```

**Explanation:**

* `name`: Descriptive name for the playbook, tasks, and handlers.
    
* `hosts`: Specifies the target hosts or groups on which the playbook tasks will be executed.
    
* `become`: (Optional) Indicates whether tasks should be executed with elevated privileges (sudo).
    
* `vars`: (Optional) Define variables for the playbook to enhance flexibility.
    
* `tasks`: List of tasks to be executed on the target hosts. Each task involves a specific Ansible module and its parameters.
    
* `handlers`: (Optional) List of handlers, which are tasks triggered by specific events. Handlers are defined separately but are called by tasks when needed.
    

---

# **Prerequisites:**

1. **Ansible Installed on the Master Node:**
    
2. **Server Nodes**
    
3. **Connection Established Between Master and Server Nodes:**
    
4. **Optional: Playbook Folder on the Master Node:**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704388297972/61728df5-0a79-4f9e-8271-531077d9ef2d.png?auto=compress,format&format=webp align="left")
    

---

### Tasks:

### Write an ansible playbook to create a file on a different server

**Step 1: Create the playbook file (**`create_file.yml`):

**Step 2: Write the Content:**

```plaintext
---
- name: Create a file on a different server
  hosts: your_target_server  # Replace with the hostname or IP of your target server
  become: true  # To run tasks with elevated privileges

  tasks:
    - name: Create a file
      file:
        path: /path/to/remote/file.txt  # Replace with the desired remote path and filename
        state: touch
```

* Open your preferred text editor (e.g., VSCode, Nano, Vim) and paste the content of the playbook into a new file named `create_file.yml`.
    
* Replace `your_target_server` with the actual hostname or IP address of the server where you want to create the file.
    
* Modify `/path/to/remote/file.txt` to the desired path and filename on the remote server.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704388472606/ea24011a-a810-4dce-9906-db22a6495a41.png?auto=compress,format&format=webp align="left")

**Step 3: Apply the Playbook:**

* Run the following command in the same directory as your playbook file:
    
    ```plaintext
      ansible-playbook create_file.yml
    ```
    
* Ansible will execute the playbook, and the file will be created on the specified server.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704388536286/5f8059d1-dd78-4f5a-bf5b-3d42fb37a160.png?auto=compress,format&format=webp align="left")
    

**Step 4: Verify: (This verify is done on the server 1)**

* SSH into the target server to verify that the file has been created.
    
    ```plaintext
      ssh <username>@<your_target_server>
      ls /path/to/remote/
    ```
    
    Replace `<username>` with your SSH username and `<your_target_server>` with the hostname or IP address of the target server.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704388601619/0db95275-f85c-49b9-b589-ddc254561975.png?auto=compress,format&format=webp align="left")
    

---

### Write an ansible playbook to create a new user.

**Step 1: Create the playbook file (**`create_user.yml`)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704388849592/627d75f3-30fe-4fa8-b097-245d6d18a14b.png?auto=compress,format&format=webp align="left")

**Step 2: Write the Content:**

* Open your preferred text editor (e.g., VSCode, Nano, Vim) and paste the content of the playbook into a new file named `create_user.yml`.
    
* Replace `your_target_server` with the actual hostname or IP address of the server where you want to create the new user.
    
* Modify `your_new_user` to the desired username you want to create.
    

```plaintext
---
- name: Create a new user on a server
  hosts: your_target_server  # Replace with the hostname or IP of your target server
  become: true  # To run tasks with elevated privileges

  tasks:
    - name: Create a new user
      user:
        name: your_new_user  # Replace with the desired username
        state: present
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704389107197/c3f098c3-fbae-402b-a9ed-2d816c11ca14.png?auto=compress,format&format=webp align="left")

**Step 3: Apply the Playbook:**

* Run the following command in the same directory as your playbook file:
    
    ```plaintext
      ansible-playbook create_user.yml
    ```
    
* Ansible will execute the playbook, and the new user will be created on the specified server.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704389131727/0ed1c045-d1b9-4f76-bdf4-bfc649985ba6.png?auto=compress,format&format=webp align="left")
    

**Step 4: Verify:**

* Just for check - connect the server 1 using ssh then
    
    ```plaintext
      cat /etc/passwd | grep <your_new_user>
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704389160805/b615dba1-3a4d-4dd8-ae59-ae5e50040f47.png?auto=compress,format&format=webp align="left")
    

---

### Write an ansible playbook to install docker on a group of servers

**Step 1: Create the Playbook File** Create a new file named `install_docker.yml` to store your playbook.

**Step 2: Write the Playbook Content** Add the following content to your `install_docker.yml` file:

**COPY**

```plaintext
---
- name: Install Docker
  hosts: your_server_group
  become: true

  tasks:
    - name: Add Docker GPG key
      apt_key:
        url: https://download.docker.com/linux/ubuntu/gpg
        state: present

    - name: Add Docker APT repository
      apt_repository:
        repo: deb https://download.docker.com/linux/ubuntu focal stable
        state: present

    - name: Install Docker
      apt:
        name: docker-ce
        state: present
```

Replace `your_server_group` with the name of the group where you want to install Docker.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704389915528/f31cfd55-4d7c-4de0-9459-a9814c2f77a7.png?auto=compress,format&format=webp align="left")

**Step 3: Apply the Playbook** Run the following command to apply the playbook:

```plaintext
ansible-playbook install_docker.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704389640469/31ca9dde-e80a-49ad-969a-4ff4d8622b24.png?auto=compress,format&format=webp align="left")

**Step 4: Verify** After applying the playbook, SSH into one of the servers in your group and run the following command to verify that Docker has been installed:

```plaintext
docker --version
```

You should see information about the Docker version if the installation was successful.

```plaintext
sudo docker ps
```

###   
Task-02

* Write a blog about writing ansible playbooks with the best practices.
    

In the realm of DevOps, Ansible Playbooks serve as the orchestrators, defining the infrastructure as code. Let's dive into the best practices to craft efficient and maintainable Ansible Playbooks.

\*\*1. **Organize Your Playbooks:**

* **Playbook Structure:** Divide playbooks into logical sections, such as variables, tasks, and handlers.
    
* **Roles:** Consider using roles for modularizing and reusing code across different playbooks.
    

\*\*2. **Use Descriptive Naming:**

* **Roles and Tasks:** Name roles and tasks descriptively to enhance readability and maintainability.
    

\*\*3. **Leverage Variables:**

* **Centralize Variables:** Use `vars` directories and separate variable files for organized variable management.
    
* **Environment-specific Variables:** Utilize environment-specific variable files for flexibility.
    

\*\*4. **Task Implementation:**

* **Idempotency:** Ensure tasks are idempotent to avoid unintended side effects during playbook runs.
    
* **Handlers:** Implement handlers for actions triggered by events, keeping your playbook efficient.
    

\*\*5. **Secure Sensitive Data:**

* **Vault:** Use Ansible Vault to encrypt sensitive data like passwords and API keys.
    

\*\*6. **Documentation:**

* **Comments:** Add comments to explain complex tasks or roles.
    
* **README Files:** Include README files for playbooks and roles to document usage and dependencies.
    

\*\*7. **Testing:**

* **Dry Runs:** Run playbooks with `--check` to perform a dry run without making changes.
    
* **Use Molecule:** Incorporate Molecule for testing roles in isolation.
    

\*\*8. **Logging and Notifications:**

* **Logging:** Enable verbose logging for troubleshooting.
    
* **Notifications:** Implement alerting or notifications for playbook results.
    

\*\*9. **Version Control:**

* **Git Best Practices:** Follow Git best practices, including versioning, branching, and commit messages.
    

\*\*10. **Continuous Integration:**

* **CI/CD Integration:** Integrate Ansible playbooks into CI/CD pipelines for automated testing and deployment.
    

Conclusion: Mastering Ansible Playbooks requires adherence to best practices, ensuring scalability, maintainability, and security. By following these guidelines, you can streamline your infrastructure as code journey and empower your DevOps practices.

Happy automating! 🚀🔧