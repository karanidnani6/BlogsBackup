---
title: "Day 59: Ansible Project"
datePublished: Wed Jan 10 2024 06:14:53 GMT+0000 (Coordinated Universal Time)
cuid: clr7dyuig000009kxaga6b07c
slug: day-59-ansible-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704866699670/f1fc6506-630b-4746-977d-2a6a43a35d11.jpeg

---

Ansible playbooks are amazing, as you learned yesterday. What if you deploy a simple web app using ansible, sounds like a good project, right?

# Task-01

* create 3 EC2 instances . make sure all three are created with same key pair
    
* Install Ansible in host server
    
* copy the private key from local to Host server (Ansible\_host) at (/home/ubuntu/.ssh)
    
* access the inventory file using sudo vim /etc/ansible/hosts
    
* Create a playbook to install Nginx
    
* deploy a sample webpage using the ansible playbook
    

**Create 3 EC2 instances. make sure all three are created with the same key pair.**

To set up three EC2 instances, go to the EC2 service and initiate their launch.

After successfully creating the trio of EC2 instances, identify one as the Ansible control node (ansible\_host) and the remaining two as managed nodes (ansible\_server).

Install Ansible on the control node:

Establish an SSH connection to your EC2 instance.

Add the Ansible PPA repository with the command:

```plaintext
sudo apt-add-repository ppa:ansible/ansible
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754044387/6109ed18-3aff-4094-a24a-7841f6d59ace.png?auto=compress,format&format=webp align="left")

Update the package using the following commands:

```plaintext
sudo apt-get update
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754049214/0a7b7e10-7f15-4baa-87c7-524a66fa75a8.png?auto=compress,format&format=webp align="left")

Install Ansible:

```plaintext
sudo apt-get install ansible
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754053220/54012a2b-8108-449c-9fb4-b77dc6adced0.png?auto=compress,format&format=webp align="left")

Upon completion of the installation, verify the Ansible version:

```plaintext
ansible --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754057936/563db6fd-09a6-4e70-87f5-f8aa2d011d5b.png?auto=compress,format&format=webp align="left")

Transfer the private key from your local machine to the Ansible control node (ansible\_host) at the location (/home/ubuntu/.ssh).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754060883/6ae784af-eb46-4e8b-a8a2-541bdf5c920f.png?auto=compress,format&format=webp align="left")

To proceed with the configuration, move the private key to the Ansible control node (ansible\_host) by creating a new file at /home/ubuntu/.ssh and pasting the private key into that file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754064125/aaea3ee5-aad4-435b-8fe4-a82af233474e.png?auto=compress,format&format=webp align="left")

Grant appropriate permissions to the private key file using the chmod command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754067162/73ba07e4-9e70-4dde-8bce-61f3cd257b24.png?auto=compress,format&format=webp align="left")

Access the inventory file using:

```plaintext
sudo vim /etc/ansible/hosts
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754070469/c53946a6-4955-46ac-a514-49f4323fa593.png?auto=compress,format&format=webp align="left")

Create an inventory file at the default location (/etc/ansible/hosts), which contains a list of hosts or servers. Add the IP addresses of the servers and specify the location of the private key file for authentication.

Craft a playbook to install Nginx:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754092618/9aa4d166-7319-40cd-9b8a-36b3e584659c.png?auto=compress,format&format=webp align="left")

Specify the playbook's name (Install nginx) and the target hosts (servers). Include become: yes to execute tasks with root privileges. The first task updates the apt cache on the managed nodes using the apt module. The second task installs the latest Nginx version using the same module. The third task starts the Nginx service using the service module, specifying the service name (nginx) and setting the state parameter to started.

Execute the playbook using the ansible-playbook command:

```plaintext
ansible-playbook file-name.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754096931/a5001bf4-d4bc-4c93-bdd9-1703b9bab4be.png?auto=compress,format&format=webp align="left")

Inspect the Nginx status on the two EC2 instances.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754101292/39a14433-e6ec-4926-b29b-8959a4240949.png?auto=compress,format&format=webp align="left")

Deploy a sample webpage using the Ansible playbook:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754106853/03b81d36-dc57-45a3-9b09-865dcc58fad3.png?auto=compress,format&format=webp align="left")

Create a new file, index.html, in the playbook directory and add sample content.

Update an Ansible playbook file, install\_nginx.yml, in the playbook directory:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754110262/43334926-6234-426a-95f7-5c3a7eb033a9.png?auto=compress,format&format=webp align="left")

This playbook copies the index.html file to the default Nginx web server document root directory at /var/www/html/.

Execute the playbook.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754114075/1b43802e-3260-4477-a6dc-0ab4dd49519e.png?auto=compress,format&format=webp align="left")

Once the playbook completes execution, open a web browser and enter the public IP address of one of the EC2 instances running Nginx.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702754119202/38d222c6-3a43-4b61-891c-9c8374798f95.png?auto=compress,format&format=webp align="left")