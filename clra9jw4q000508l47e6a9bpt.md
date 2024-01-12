---
title: "Day 73 -Setup grafana in your local environment on AWS EC2."
datePublished: Fri Jan 12 2024 06:34:35 GMT+0000 (Coordinated Universal Time)
cuid: clra9jw4q000508l47e6a9bpt
slug: day-73-setup-grafana-in-your-local-environment-on-aws-ec2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705040265134/5fd5b73e-9f3a-48e7-859f-dd45bd50391a.jpeg

---

Task:

Setup grafana in your local environment on AWS EC2.

Proceed to the AWS console and initiate the launch of an EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705040738897/0707ff15-436b-4454-8913-7e859dd9d609.png align="center")

In the security group of your EC2 instance, open port 3000 to authorize external entry for Grafana.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705040807436/5909e8e0-dce0-4475-8b1f-ae8308acbdf0.png align="center")

Once the instance is active, establish an SSH connection to access it.

Follow the provided Grafana instructions for system installation. Download the GPG keys and include them in the list of trusted keys:

```plaintext
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add
```

Next, incorporate the Grafana repository:

```plaintext
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705040938355/4ffe13f0-5737-4c81-8d98-d9cc5b5734e4.png align="center")

Upon successful addition, update the system:

```plaintext
sudo apt update
```

Install Grafana:

```plaintext
sudo apt install grafana
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705041004760/347cfc62-ed51-4234-86bb-151c9352eee0.png align="center")

Initiate Grafana using the command:

```plaintext
sudo systemctl start grafana-server
```

To enable automatic startup on boot, configure Grafana with:

```plaintext
sudo systemctl enable grafana-server
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705041051288/12953534-4d01-4502-853a-ad53777dd402.png align="center")

Verify the status of Grafana by executing:

```plaintext
sudo systemctl status grafana-server
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705041074406/51182139-eb9d-4fb5-927b-46c313220b46.png align="center")

Access Grafana through the web interface by entering the IP address or domain name of your EC2 instance in a web browser, followed by the default Grafana port (3000). For instance:

```plaintext
http://<EC2-instance-IP-address>:3000
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705041214415/918fad45-2046-4ffc-9387-ab295be7a611.png align="center")

Now, log in to Grafana using the default credentials (admin/admin) and begin creating your initial dashboards.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705041266143/10775373-cb31-40bb-8162-697a15e5cd44.png align="center")