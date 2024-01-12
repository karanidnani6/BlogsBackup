---
title: "Day 74 - Connecting EC2 with Grafana"
datePublished: Fri Jan 12 2024 08:16:12 GMT+0000 (Coordinated Universal Time)
cuid: clrad6kav000008jtg5ws7j58
slug: day-74-connecting-ec2-with-grafana
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705041442575/c42a3a6e-b18a-415e-a17a-d62b22d2da3b.jpeg

---

In the last article, we have learned How to set up Grafana in our local environment.

Now, let's proceed with creating a Grafana monitoring by integrating Loki and Promtail for efficient log aggregation and analysis. Our goal is to connect a Linux/ Windows EC2 instance with Grafana to monitor various components of the servers in real time.

### A Brief Introduction to Loki and Promtail:

Loki: A horizontally scalable log aggregation system that efficiently stores and indexes log data, serving as the central repository for fast, distributed log processing.

Promtail: A lightweight log collector operating on individual servers or containers, collecting log data from various sources. It tails log files or streams and sends the data to Loki for storage and analysis.

### Task-01: Monitoring different components of server with Grafana

**After installing Grafana on our server(For more details refer my last blog** [**here**](https://hashnode.com/post/clqlxaicv000c08l0din4fzp5):

1. * Install Docker:
        
        ```plaintext
           sudo apt-get update
           sudo apt install docker.io
           sudo usermod -aG docker $USER
           sudo reboot
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705045781618/38032cbe-3025-4749-85d6-2ea46ee7be95.png align="center")
        
        * Install Loki and Promtail using Docker.
            
2. **Download Configuration Files:**
    
    * Loki Config:
        
        ```plaintext
          mkdir grafana_configs
          cd grafana_configs
          wget https://raw.githubusercontent.com/grafana/loki/v2.8.0/cmd/loki/loki-local-config.yaml -O loki-config.yaml
        ```
        
    * Promtail Config:
        
        ```plaintext
          wget https://raw.githubusercontent.com/grafana/loki/v2.8.0/clients/cmd/promtail/promtail-docker-config.yaml -O promtail-config.yaml
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705045852504/735f955c-f3fc-45d4-87d5-b0ed9a8eb453.png align="center")
        
    * **Run Loki Docker Container:**
        

```plaintext
    sudo docker run -d --name loki -v $(pwd):/mnt/config -p 3100:3100 grafana/loki:2.8.0 --config.file=/mnt/config/loki-config.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705045910242/c2f3cf1f-ad4b-417f-baaa-9c50fafc32c1.png align="center")

This command initiates a Docker container named "loki" from the Grafana Loki image version 2.8.0. It runs the container in detached mode (`-d`), maps the current directory as a volume inside the container (`-v $(pwd):/mnt/config`), and exposes port 3100 on the host to port 3100 on the container (`-p 3100:3100`). Additionally, it specifies the Loki configuration file as `/mnt/config/loki-config.yaml` using the `--config.file` option. This configuration file holds settings for Loki, such as storage configurations and retention policies.

**Configure Security Group:**

* Edit the inbound rule to allow port 3100 in the security group of your EC2 instance.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705046002319/e54be935-dbab-4fdc-ac65-cea92de6cef4.png align="center")

**Check Loki Readiness:**

* Open a browser and visit `https://<public-ip>:3100/ready` to confirm Loki's readiness.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705046651695/9a02dcf3-08ca-4273-80ae-29bc5c31e1b7.png align="center")

To discover the specific logs or metrics present in Loki, you can obtain them using the command `/metrics`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705046678854/60342e3b-3773-4041-aab8-e16714bb830f.png align="center")

**Run Promtail Docker Container:**

```plaintext
sudo docker run -d --name promtail -v $(pwd):/mnt/config -v /var/log:/var/log --link loki grafana/promtail:2.8.0 --config.file=/mnt/config/promtail-config.yaml
```

This command launches a Docker container named "promtail" using the Grafana Promtail image version 2.8.0. The container runs in detached mode (`-d`), mounts the current directory as a volume inside the container (`-v $(pwd):/mnt/config`), and also mounts the host's `/var/log` directory to the container's `/var/log` directory (`-v /var/log:/var/log`). It establishes a network link with the previously created "loki" container using `--link loki`. Additionally, it specifies the Promtail configuration file as `/mnt/config/promtail-config.yaml` using the `--config.file` option. This configuration file contains settings for Promtail, such as log file paths and target Loki endpoints.

### Setting Up Grafana Data Source:

1. Log in to your Grafana web interface.
    
2. Navigate to "Configuration" &gt; "Data Sources" &gt; "Add data source."
    
3. Enter the Loki server URL, typically in the format http://:9090.
    
4. Choose "Loki" as the type of data source.
    

* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705046843745/f7b08543-49b4-4ad8-9145-9e6920ed05b5.png align="center")
    

Creating Grafana Dashboards:

Develop Grafana dashboards to visualize the metrics gathered from both Linux and Windows instances.

Include panels for CPU usage, memory usage, disk space, network activity, and any other metrics of interest.

Monitoring and Analysis:

Now that Loki and Promtail are configured, you can effectively monitor and analyze various components of your Linux and Windows EC2 instances.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703660389648/cf3b214f-3dfe-45e3-98ac-3c855eb2a016.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703660393280/c6764ef4-b356-4732-a058-a1230337d7c3.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703660396263/ee782651-cc90-4b2d-ae93-e1b88d52c5b6.png?auto=compress,format&format=webp align="left")