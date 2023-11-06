---
title: "#Day45:Deploying a WordPress Website on AWS"
datePublished: Mon Nov 06 2023 12:30:04 GMT+0000 (Coordinated Universal Time)
cuid: clomvqzbf000709la3zkgaydv
slug: day45deploying-a-wordpress-website-on-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699251868434/439130e6-74ba-43d4-b7cd-f16cf979d3b2.jpeg
tags: 90daysofdevops

---

Welcome back to our ongoing journey through Amazon Web Services (AWS)! In the digital realm, WordPress stands tall as the go-to platform for creating websites and blogs. In today's guide, we'll dive into the process of deploying a WordPress website on AWS. If you've been following along, you'll remember that in our previous installment (Day 44), we set up an Amazon RDS (Relational Database Service) for MySQL. Now, let's take the next step and deploy our WordPress site.

**Day 45: Deploying a WordPress Website on AWS**

Over 30% of all websites on the internet use WordPress as their content management system (CMS). It is a versatile platform used for running blogs, e-commerce sites, message boards, and more. In this guide, we'll walk through the process of setting up a WordPress blog site on Amazon Web Services (AWS). If you followed along with Day 44, you've already set up an RDS for MySQL database, which will be an essential component in this process.

**Task 01: Create an RDS Instance for WordPress**

To get started with setting up your WordPress site on AWS, follow these steps:

**Step 1: Create an Amazon RDS for MySQL Database**

1. Log in to your AWS Management Console.
    
2. Navigate to the AWS RDS service.
    
3. Click on "Create Database" and select "MySQL" as your database engine.
    
4. Follow the on-screen instructions to configure your RDS instance. You'll need to set the DB instance identifier, master username, and password. Make sure to choose the appropriate instance class, storage, and other settings based on your needs.
    
5. Ensure that your RDS instance is publicly accessible, as your WordPress EC2 instance will need to connect to it.
    
6. Review and create the RDS instance, and AWS will handle the provisioning process.
    
7. Once the RDS instance is available, note down the endpoint URL, database name, master username, and password. You will need these details when configuring your WordPress application.
    

**Task 02: Setting Up the WordPress Server**

With the RDS for MySQL database ready, let's proceed to set up the Amazon EC2 instance and deploy your WordPress site.

**Step 1: Launch an Amazon EC2 Instance**

1. In the AWS Management Console, navigate to the EC2 service.
    
2. Click on "Launch Instances" to create a new virtual machine (EC2 instance).
    
3. Select an Amazon Machine Image (AMI) based on your preference (e.g., Amazon Linux 2, Ubuntu, etc.).
    
4. Choose an instance type based on your site's expected traffic and resource requirements.
    
5. Configure the instance by setting the number of instances, networking options, and more.
    
6. In the "Add Storage" section, specify the storage volume size. You can expand the storage size as your website grows.
    
7. Add tags and configure security groups and key pairs to secure your instance.
    
8. Review your instance details and launch the EC2 instance.
    
9. Select or create a new key pair to securely access your instance.
    
10. Finally, launch your instance. You'll be provided with an SSH key to access the instance.
    

**Step 2: Install and Configure WordPress**

Now that your EC2 instance is up and running, follow these steps to install and configure WordPress:

1. Connect to your EC2 instance using SSH and the key pair you downloaded.
    
    ```bash
    ssh -i your-key-pair.pem ec2-user@your-ec2-instance-ip
    ```
    
2. Update the instance and install necessary packages:
    
    ```bash
    sudo yum update -y
    sudo yum install -y httpd mysql php php-mysqlnd
    ```
    
3. Start and enable the Apache web server:
    
    ```bash
    sudo systemctl start httpd
    sudo systemctl enable httpd
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699273214771/526b7608-2b00-44c4-a8d9-4df07584e1c2.png align="center")
    
4. Install and start the MySQL client:
    
    ```bash
    sudo yum install -y mysql
    ```
    
5. Download and install WordPress:
    
    ```bash
    sudo wget https://wordpress.org/latest.tar.gz
    sudo tar -xzvf latest.tar.gz
    sudo mv wordpress/* /var/www/html/
    ```
    
6. Create a WordPress configuration file:
    
    ```bash
    sudo cp /var/www/html/wp-config-sample.php /var/www/html/wp-config.php
    ```
    
7. Edit the configuration file and add your RDS database details:
    
    ```bash
    sudo nano /var/www/html/wp-config.php
    ```
    
    Replace the database information with your RDS details.
    
    ```plaintext
    // ** MySQL settings - You can get this info from your web host ** //
    /** The name of the database for WordPress */
    define( 'DB_NAME', 'database_name_here' );
    
    /** MySQL database username */
    define( 'DB_USER', 'username_here' );
    
    /** MySQL database password */
    define( 'DB_PASSWORD', 'password_here' );
    
    /** MySQL hostname */
    define( 'DB_HOST', 'localhost' );
    ```
    
8. **Now let's edit the** `Authentication Unique Keys` **and** `Salts`**. Copy the below API code and paste it into the** `wp-config.php` **file.**
    
    ```plaintext
    define('AUTH_KEY',         '--+$RG=aXK;hfS|J*01xZ-><c|Y>fB;-=S_@gX[sb_,CY~u w3u:Gj[g!e^]BIv7');
    define('SECURE_AUTH_KEY',  'lXl[2P;hQ_5+WhU|SV-d.Ab+z]SUj`MU?BaA7k+X&+<{|?&-*oAG;W@q-o<gBY|X');
    define('LOGGED_IN_KEY',    'd8Q6NJ1a{rE RZ>hr}xlrQVk~063^+d;}4)G2bDt@a^JPp#/$i53J%E<M5] Oc@V');
    define('NONCE_KEY',        'H)};6-21jHe~HjJ<JUL3%PnRzj1k3!A^-tg|?G!v%J:w8}6:1YZ*p[zWgHM6HC?K');
    define('AUTH_SALT',        'VG(~Fr?a)mR^^Q59Ojx,`-,#=7nCr;v^[B!!1Ug7CSH0mx:Cgg,;=di+/<y3Cj^q');
    define('SECURE_AUTH_SALT', ':ztC0[+%SD1U0PIIFmUeb}Wc|KbKh(Er9>pV[d2H$v(4#V6P-*tv;#:2#PQFwKX1');
    define('LOGGED_IN_SALT',   '#&cU];~F|Acv=evUgEY5;mXcKaRx2r|B+TkQ}+:-zBXPotif{[Zm>Bd_(iYb%+Vr');
    define('NONCE_SALT',       'Z%%#u|]4OdA2nQvey/XmSR,i_?:XxJ- T>%i**=oHeB-/|+I[L6.0l%Yo
    ```
    
9. **Now let's Deploy the WordPress site, but before that, we need to install some dependencies.**
    
    ```plaintext
    sudo apt install php libapache2-mod-php php-mysql -y
    ```
    
10. **Now , Copy the extracted WordPress files to the Apache web server document root using the command**
    
    ```plaintext
    cd ..
    sudo cp -r wordpress/* /var/www/html/
    ```
    
11. Restart the Apache web server:
    
    ```bash
    sudo systemctl restart httpd
    ```
    

**Step 3: Access Your WordPress Site**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699273729425/82280926-ece5-4d25-8f94-bef655728e49.png align="center")

With WordPress installed and configured, you can now access your site by visiting your EC2 instance's public IP address in a web browser. Complete the WordPress setup process, and you'll have your own WordPress website up and running on AWS.

Congratulations! You've successfully deployed a WordPress website on AWS, utilizing an Amazon RDS for MySQL database for data storage. This is a fundamental step in creating a dynamic and scalable web presence using AWS services.