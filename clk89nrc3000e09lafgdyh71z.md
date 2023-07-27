---
title: "#Day 3:  - Basic Linux Commands"
datePublished: Tue Jul 18 2023 12:24:07 GMT+0000 (Coordinated Universal Time)
cuid: clk89nrc3000e09lafgdyh71z
slug: day-3-basic-linux-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689675341526/8709d4b8-be34-49fb-8598-0dea8955813f.jpeg
tags: linux, jenkins, devops-journey, 90daysofdevops, trainwithshubham

---

### **Exploring Essential Linux Commands with Fruits and Colors!** 🍏📂🌈

*Welcome to Day 3 of our 90 Days of DevOps journey!* Today, we'll dive into the world of Linux commands and explore some fundamental operations that every DevOps engineer should be familiar with. But wait, we won't be limited to boring examples! We'll use fruits and colors to make it more engaging. Let's get started!

### **1\. Viewing the Contents of a File 📄**

To check what's written inside a file, we can use the `cat` command. For instance, to view the contents of a file named "fruits.txt," you can run the following command:

```shell
cat fruits.txt
```

### **2\. Changing Access Permissions of Files 🔐**

In Linux, we can modify the access permissions of files using the `chmod` command. This command allows us to control who can read, write, or execute a file. To change the access permissions of a file named "file.txt" to read and write for the owner, and only read for others, you can use the following command:

```shell
chmod 644 file.txt
```

### **3\. Checking Command History ⏲️**

To see the list of commands you've executed so far, you can make use of the `history` command. It displays a numbered list of recently executed commands. To view your command history, simply type:

```shell
history
```

**4\. Removing a Directory/Folder 🗑️** To delete a directory (folder) and its contents in Linux, we can employ the `rm` command with the `-r` option. This command recursively removes all files and subdirectories within the specified directory. For instance, to remove a directory named "myfolder," you can use the following command:

```shell
rm -r myfolder
```

**5\. Creating and Viewing the Content of a File 📝** To create a new file named "fruits.txt" and view its content, we can use the `touch` and `cat` commands together. First, create the file using:

```shell
touch fruits.txt
```

Next, open the file and add some content to it using a text editor of your choice. Finally, to view the content of "fruits.txt," run:

```shell
cat fruits.txt
```

**6\. Adding Content to devops.txt 📝** To add content to a file named "devops.txt," where each item is on a separate line, we can use a text editor or the `echo` command. For example, to add fruits in separate lines, run the following commands one by one:

```shell
echo "Apple" >> devops.txt
echo "Mango" >> devops.txt
echo "Banana" >> devops.txt
echo "Cherry" >> devops.txt
echo "Kiwi" >> devops.txt
echo "Orange" >> devops.txt
echo "Guava" >> devops.txt
```

**7\. Showing Only the Top Three Fruits from the File 👆** To display only the top three fruits from the "devops.txt" file, we can use the `head` command. The `-n` option specifies the number of lines to show. In this case, we want to show the top three fruits, so the command would be:

```shell
head -n 3 devops.txt
```

**8\. Showing Only the Bottom Three Fruits from the File 👇** To exhibit only the bottom three fruits from the "devops.txt" file, we can utilize the `tail` command. Similar to `head`, the `-n` option is used to specify the number of lines to display. For instance, to show the bottom three fruits, execute:

```shell
tail -n 3 devops.txt
```

**9\. Creating Another File named Colors.txt and Viewing its Content 🎨** To create a new file named "Colors.txt" and view its content, follow these commands:

```shell
touch Colors.txt
```

Next, open the file and add some content, such as colors, using your preferred text editor. To view the content of the "Colors.txt" file, use the `cat` command:

```shell
cat Colors.txt
```

**10\. Finding the Difference Between fruits.txt and Colors.txt Files 🍎🎨** To find the difference between the "fruits.txt" and "Colors.txt" files, we can use the `diff` command. This command compares the contents of two files and highlights the dissimilarities. For instance, to compare the two files, run:

```shell
diff fruits.txt Colors.txt
```

That's it for today! We hope you enjoyed exploring these essential Linux commands while playing with fruits and colors. Stay tuned for more exciting DevOps topics in our 90 Days of DevOps journey! 🚀🌐