---
title: "Day 55: Understanding Configuration Management with Ansible"
datePublished: Tue Jan 09 2024 05:06:44 GMT+0000 (Coordinated Universal Time)
cuid: clr5w3d5h000g0al5hh8ic6ag
slug: day-55-understanding-configuration-management-with-ansible
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704769500131/d010fcdb-9b3c-493f-9608-c450b57a99a1.png

---

### **Introduction**

In today's ever-evolving IT landscape, automation has emerged as a pivotal force for orchestrating complex tasks seamlessly. Ansible, a powerful open-source automation tool, offers a straightforward yet versatile solution. This blog post takes you on a creative journey to master Ansible on AWS, from installation to orchestrating tasks across multiple instances.

## What's this Ansible?

Ansible is an open-source automation tool that simplifies IT tasks such as configuration management, application deployment, intraservice orchestration, and provisioning. It is designed to be easy to use, scalable, and agentless, relying on SSH and other standard protocols for communication with managed nodes.

**Key Features:**

1. **Agentless Architecture:** Ansible operates without the need for agents on managed nodes, reducing potential security vulnerabilities and simplifying setup.
    
2. **Declarative Language (YAML):** Ansible uses YAML (Yet Another Markup Language) for its playbooks, allowing users to define configurations and tasks in a human-readable, declarative format.
    
3. **Idempotency:** Ansible ensures idempotency, meaning that running a playbook multiple times produces the same result regardless of the initial state, preventing unintended side effects.
    
4. **Modularity and Extensibility:** Ansible is highly modular, with a vast collection of built-in modules. Users can also create custom modules to extend functionality and integrate with diverse technologies.
    
5. **Orchestration:** Ansible provides powerful orchestration capabilities, allowing users to coordinate complex tasks and workflows across multiple systems.
    
6. **Parallel Execution:** Ansible can execute tasks in parallel across multiple nodes, optimizing performance and reducing the time needed for automation tasks.
    
7. **Dynamic Inventory:** Ansible can dynamically discover and manage the inventory of hosts, making it easy to scale automation to a large number of systems.
    
8. **Integration with Cloud Providers:** Ansible seamlessly integrates with major cloud providers, allowing users to automate the provisioning and management of resources in cloud environments.
    

# Task-01

* Installation of Ansible on AWS EC2 (Master Node)
    

1. **Add Ansible PPA**: To install Ansible on your EC2 instance, you'll first need to add the Ansible PPA (Personal Package Archive) to your system. This ensures that you get the latest stable version of Ansible.
    
    ```plaintext
     sudo apt-add-repository ppa:ansible/ansible
    ```
    
2. **Update Package List**: Next, update the package list to include the newly added Ansible PPA.
    
    ```plaintext
     sudo apt update
    ```
    
3. **Install Ansible**: Finally, install Ansible using the following command:
    
    ```plaintext
     sudo apt install ansible
    ```
    

With these steps completed, Ansible is now installed and ready to be used on your master node.

1. **Verify the Installation**
    
    ```plaintext
     ansible --version
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704770332579/cbe14e3d-b8b8-415c-b689-b6d7b14461de.png align="center")
    

# Task-02

read more about Hosts file `sudo nano /etc/ansible/hosts ansible-inventory --list -y`

In Ansible, the **"hosts"** file is a configuration file that defines the inventory of target hosts or servers that Ansible can manage.

It is a text file that lists the hostnames or IP addresses of the target systems on which Ansible will perform tasks or execute playbooks.

It allows you to organize and group hosts into different categories, such as development, production, or specific functional roles like web servers or database servers.

The host file is located at `/etc/ansible/hosts` by default, but you can specify a different path using the `-i` option when executing Ansible commands or playbooks.

1. **Read the Hosts File**: You can view and edit the Ansible hosts file using a text editor like Vim:
    
    ```plaintext
     sudo vim /etc/ansible/hosts
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704770400484/4f29d86f-555f-4190-b2f0-1af94e557cf2.png align="center")
    
    The host file typically has the following structure:
    
    ```plaintext
     [group_name]
     hostname1
     hostname2
     hostname3
    
     [another_group_name]
     hostname4
     hostname5
    ```
    
    In this example, **"group\_name"** and **"another\_group\_name"** represent groups of hosts, and the hostnames listed underneath each group are the individual target systems.
    
    You can define multiple groups and include hosts in different groups based on your infrastructure setup.
    
2. **View Host Inventory**: To view the current host inventory configured in Ansible, you can use the following command:
    
    ```plaintext
     ansible-inventory --list -y
    ```
    
    This command will display a YAML-formatted list of hosts and their attributes, including the hostnames, IP addresses, and any other defined variables or group memberships.
    

# Task-03

* Setup 2 more EC2 instances with same Private keys as the previous instance (Node)
    
* Copy the private key to master server where Ansible is setup
    
* Try a ping command using ansible to the Nodes.
    

In this task, we'll set up two additional EC2 instances, which will act as nodes. These nodes will be managed by Ansible from the master node. Follow these steps:

1. **Create EC2 Instances**: Set up two new EC2 instances on AWS using the same private keys as the previous instance (the master node). Ensure they are running and accessible via SSH
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704770912781/d676d504-4769-4198-ad70-ecc219ffe590.png align="center")
    
2. **Copy Private Key**: Copy the private key file used to access the master node to your local machine (if it's not already there). You'll need this key to authenticate with the new nodes.
    
    ```plaintext
     cd .ssh #on master server
     vim ansible_key #Open ansible-key.pem file and Copy its content from local to paste
     cat ansible_key #verify copy has done or not
     chmod 600 ansible_key
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704772731600/353437fb-e0fd-4f63-a8da-b41a7e7f8eb4.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704772955230/3de46eb7-ffb4-4e16-a7ec-54a491c7ece6.png align="center")
    
      
    **Ping Nodes**: To verify that Ansible can communicate with the new nodes, use the Ansible ping module. Replace `<node_ip>` with the IP address of one of your new EC2 instances and `<private_key_path>` with the path to the copied private key file.
    
    ***So let's first configure host file as per commands mentioned in the Task#02***
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704773798844/34734ffe-7945-4ca5-812f-c0caa4c29d94.png align="center")
    
    You can modify this behavior by setting the **ansible\_python\_interpreter inventory** variable for a specific host, which will instruct Ansible to replace the Python interpreter with the provided value instead.
    
    Inventory Once you've added the hosts to the file, You can use the **"ansible-inventory"** command to verify the roster of hosts that Ansible is capable of overseeing.
    
    Now, we will attempt to determine whether the connection has been successfully established by employing the Ping Command.
    
    If everything is set up correctly, Ansible will return a **"pong"** response, indicating that it can communicate with the nodes.
    
    ```plaintext
     ansible all -m ping
     #OR
     ansible all -m ping -u ubuntu
     #OR
     ansible all -m ping -i <path of hosts> --key-file=~<private_key_path>
    ```
    

**Congratulations!** You've successfully installed Ansible on your master node, configured the hosts file, set up additional EC2 instances as nodes, and verified Ansible's connectivity with those nodes.