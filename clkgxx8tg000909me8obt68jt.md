---
title: "#Day5:Advanced Linux Shell Scripting for DevOps Engineers with User management"
datePublished: Mon Jul 24 2023 14:05:29 GMT+0000 (Coordinated Universal Time)
cuid: clkgxx8tg000909me8obt68jt
slug: day5advanced-linux-shell-scripting-for-devops-engineers-with-user-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690195048232/d6d73df7-b7bc-4b9d-a913-083337a8d5d3.jpeg
tags: linux, devops, shell-scripting, cronjob, 90daysofdevops

---

Hello fellow DevOps enthusiasts! Today, we embark on a new adventure in the world of Bash Scripting and Backups! 🚀

### 1.📁 **Creating Dynamic Directories with a Bash Script!** 📂

In this fun and straightforward blog post, we will learn how to use a bash script to create a series of directories with dynamic names. 🚀

💻 **Let's Get Started!**

To begin, open your favorite text editor or terminal, and let's create the [`createDirectories.sh`](http://createDirectories.sh) script. Make sure you have the appropriate permissions to execute the script.

```plaintext
bashCopy code#!/bin/bash

# Check if the script is executed with three arguments
if [ $# -ne 3 ]; then
  echo "Usage: $0 <directory_name> <start_number> <end_number>"
  exit 1
fi

directory_name=$1
start_number=$2
end_number=$3

# Function to create directories
create_directories() {
  for ((i=start_number; i<=end_number; i++)); do
    dir_name="${directory_name}_${i}"
    mkdir -p "$dir_name"
    echo "Created directory: $dir_name"
  done
}

# Call the function
create_directories
```

🔍 **Understanding the Script**

Let's break down the script step-by-step:

1. We start by checking if the script is executed with exactly three arguments using the `if` statement. If not, we display a helpful usage message and exit the script.
    
2. Next, we store the provided arguments into variables `directory_name`, `start_number`, and `end_number`.
    
3. We define a function called `create_directories()`, which will be responsible for creating the directories.
    
4. Inside the function, we use a `for` loop to iterate through the range of numbers from `start_number` to `end_number`.
    
5. For each number in the range, we construct the dynamic directory name by appending the number to the `directory_name`.
    
6. We then use the `mkdir -p` command to create the directory with the constructed name.
    
7. Finally, we print a message indicating the successful creation of each directory.
    

🏃‍♀️ **Time to Run the Script!**

Save the script and make it executable with the following command:

```plaintext
bashCopy codechmod +x createDirectories.sh
```

Now, let's try running the script with our desired arguments:

```plaintext
bashCopy code./createDirectories.sh my_directory 1 5
```

🎉 **Celebrate Your Success!**

📂 `my_directory_1` ✅  
📂 `my_directory_2` ✅  
📂 `my_directory_3` ✅  
📂 `my_directory_4` ✅  
📂 `my_directory_5` ✅

### 2.📂 **Creating a Magical Backup Script for Your Work** 🧙‍♂️

As you dive into your daily tasks, whether you're a developer, a designer, or a data enthusiast, you create something magical with your work. But in this mystical realm of technology, unexpected mishaps can happen! That's where backups come to the rescue! 💾

Backups are like a spell of protection, safeguarding your precious work from unforeseen challenges. Just like a wizard's cloak, they provide a sense of security, knowing that your efforts are safe and sound. So let's weave a magical backup script together! 🌟

Let's conjure a simple backup script using bash. Below is a code snippet for a magical backup script:

```plaintext
bashCopy code#!/bin/bash

# Directory to store backups
backup_dir="/path/to/backups"

# Source directory to be backed up
source_dir="/path/to/your/work"

# Create a backup directory if it doesn't exist
mkdir -p "$backup_dir"

# Create a timestamp for the backup filename
timestamp=$(date +%Y%m%d%H%M%S)

# Backup filename
backup_filename="backup_$timestamp.tar.gz"

# Perform the backup using tar
tar -czvf "$backup_dir/$backup_filename" "$source_dir"

# Display the magic message
echo "Backup complete! Your work is now safe in the mystical realm of backups! 🌌"
```

In this enchanting script, you have the power to customize it according to your needs:

* Replace `/path/to/backups` with the desired location to store your backups.
    
* Replace `/path/to/your/work` with the directory you want to back up.
    
* The script will create a tar.gz archive of your work and save it in the backup directory with a unique timestamp.
    

💫 **Casting the Spell - Running the Backup Script** 💫

Prepare to be mesmerized as you unleash the magic of your backup script! Simply follow these steps:

1. Save the script to a file named `backup_script.sh`.
    
2. Make the script executable with the command: `chmod +x backup_script.sh`.
    
3. To perform the backup, execute the script: `./backup_script.sh`.
    

### 3.🕰️ **Mastering Cron and Crontab - Scheduling Magic**🧙‍♂️

🕰️ **What is Cron?** 🕰️

In the realm of Linux, Cron is like the magical scheduler that can run tasks automatically without you lifting a finger! It's like having a loyal assistant, ensuring that your desired tasks are performed at specific times or intervals. 🌟

📅 **Meet Crontab - Your Spell Book!** 📅

Crontab is where the magic happens! It's like a spell book that holds the secrets of scheduling your tasks. With Crontab, you can submit, edit, or delete entries that tell Cron what and when to do certain tasks. 📚

⚡ **Casting Your First Spell with Crontab** ⚡

The incantations (commands) of Crontab are simple yet powerful! Let's learn how to use Crontab to schedule a mystical task:

1. Open your spell book (Crontab) with the command: `crontab -e`.
    
2. Now, you'll see lines of text that look like magical runes. Each line represents a scheduled task. The format is like this:
    
    ```plaintext
    sqlCopy codeminute hour day month day_of_week command_to_execute
    ```
    
3. Choose your desired timing, and write the spell (command) you want to schedule. For example, to run a script named `my_script.sh` every day at midnight, use:
    
    ```plaintext
    javascriptCopy code0 0 * * * /path/to/my_script.sh
    ```
    
4. Save your spell book and close it. Your magical task is now scheduled!
    

💫 **Embrace the Magic - Understanding the Runes** 💫

The runes in the Crontab are like the keys to unlock the magic of scheduling. Here's a quick explanation of each part:

* **Minute**: The minute when the task should be executed (0-59).
    
* **Hour**: The hour when the task should be executed (0-23).
    
* **Day**: The day of the month when the task should be executed (1-31).
    
* **Month**: The month when the task should be executed (1-12).
    
* **Day of Week**: The day of the week when the task should be executed (0-6, where 0 is Sunday).
    

You can use wildcards (\*) for any field to indicate "every" or use specific numbers to define precise timings. The possibilities are endless! 🔮

🔍 **Unveiling More Secrets of Crontab** 🔍

Crontab has even more magical tricks up its sleeve! You can list your existing spells with `crontab -l`, edit them with `crontab -e`, or remove them with `crontab -r`. The more you explore, the more powerful your scheduling magic becomes! 🌈

To automate the backup script using Cron, you need to add a Cron job that runs the backup script at your desired schedule. In this example, we'll schedule the backup to run every day at midnight.

Assuming you have already created the backup script named `backup_script.sh` and it's located in the `/path/to/backup_script.sh` directory, follow these steps to automate it with Cron:

1. Open your terminal or SSH into your server.
    
2. Open your Crontab file for editing using the following command:
    

```plaintext
bashCopy codecrontab -e
```

1. If it's your first time using Crontab, you may be prompted to select an editor. Choose your preferred editor (e.g., nano, vim).
    
2. Add the following line at the end of the Crontab file to schedule the backup script to run every day at midnight (0 minutes, 0 hours):
    

```plaintext
bashCopy code0 0 * * * /path/to/backup_script.sh
```

1. Save the file and close the editor. In nano, you can do this by pressing `Ctrl+O` to save and `Ctrl+X` to exit.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690281119620/59712421-139f-4646-814c-5b01ce577818.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690281151253/a1f65dae-f486-48ba-b5ab-e260810d0fec.png align="center")

Cron will now execute your backup script at the specified time automatically, ensuring your work is backed up every day at midnight without any manual intervention.

### 4.🧑‍💻 **User Management in Linux - Embracing the Power of Users** 🚀

In the mystical world of Linux, users are like the enchanted entities that can manipulate files, run spells (commands), and wield the power of the operating system. Each user holds a unique identity with a special User ID (UID) that sets them apart in the grand scheme of things. Today, we'll embark on a quest to learn about user management in Linux and how we can harness the power of users for our digital adventures! 🏰

👤 **Meet the Users - Entities with Unique Identities** 👤

In our digital realm, users are like the inhabitants of a vast kingdom, each with their own identity and role to play. From the mighty "root" user, symbolized by the golden crown 👑 and granted the power to rule over all, to the system users with IDs 1 to 999, who serve important functions behind the scenes. Then come the local users, with IDs starting from 1000 onwards, who navigate the kingdom's digital landscape. Each user has distinct privileges and capabilities, ensuring a harmonious coexistence in the realm of Linux. 🏰

1. ### Create 2 users and just display their Usernames
    

create two users named "Karan" and "Vicky" and then display their usernames:

1. Open your terminal or SSH into your Linux system.
    
2. To create the first user, use the `adduser` command followed by the desired username. Let's create a user named "Karan":
    

```plaintext
bashCopy codesudo adduser Karan
```

1. When prompted, set a password for the new user "Karan" and provide any additional information if required.
    
2. Repeat the same steps to create the second user, but with the username "Vicky":
    

```plaintext
bashCopy codesudo adduser Vicky
```

1. Again, set a password and provide any necessary information for the second user "Vicky".
    
2. Now that you have created both users, you can display their usernames using the `id` command followed by the `-un` option:
    

```plaintext
bashCopy code# Display the username of Karan
id -un Karan

# Display the username of Vicky
id -un Vicky
```

The terminal will show the usernames of both users, "Karan" and "Vicky," confirming their successful creation. 🧙‍♂️🧙‍♀️

You now have two magical users, "Karan" and "Vicky," ready to explore the mystical realm of your Linux system! 🌟

So, let's venture forth, embrace the magic of shell scripting, and continue our pursuit of excellence in the fascinating world of DevOps! Happy scripting, fellow sorcerers! 🧙‍♂️🔮