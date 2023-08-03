---
title: "#Day14: Python Data Types and Data Structures for DevOps 🐍💻"
datePublished: Thu Aug 03 2023 07:51:11 GMT+0000 (Coordinated Universal Time)
cuid: clkuuyert000109l47mwege35
slug: day14-python-data-types-and-data-structures-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691042422634/3ac02621-4cac-46cb-bafa-34684c25dab1.webp
tags: python, data-structures, 90daysofdevops

---

Welcome back, fellow DevOps enthusiasts! Today, let's dive into the fascinating world of Python data types and data structures. 🚀

### **Data Types: Understanding the Foundation 👨‍💻**

In Python, data types are like the building blocks of our code. They classify and categorize data, determining what operations can be performed on them. Since Python treats everything as an object, data types are essentially classes, and variables become instances of these classes. Here are some fundamental data types in Python:

* **Numeric**: Integers, complex numbers, and floats for your mathematical adventures.
    
* **Sequential**: Strings, lists, and tuples to handle ordered collections.
    
* **Boolean**: For those true or false situations.
    
* **Set**: Unordered collections with no duplicates.
    
* **Dictionaries**: Your ultimate key-value buddies for efficient data storage.
    

To check the data type of a variable, you can use the "type()" function. For example:

```plaintext
your_variable = 100
print(type(your_variable)) # Output: <class 'int'>
```

### **Data Structures: Organizing the Chaos 🗄️**

Data structures are like organizational tools for your data. They help you access and manage data more efficiently, which is a crucial skill in the world of DevOps. Python makes learning about these structures a breeze compared to other languages. Let's explore a couple of them:

* **Lists**: Python Lists are similar to arrays in other languages, representing an ordered collection of data. They are flexible as the items in a list do not need to be of the same type.
    
* **Tuples**: Python Tuples are also collections of Python objects, like lists, but they are immutable. Once created, the elements in a tuple cannot be added or removed. Just like lists, a tuple can contain elements of various types.
    
* **Dictionary**: The powerhouse of key-value pairs. It's like a map, and accessing values is super optimized.languages.Python dictionaries resemble hash tables in other languages and have a time complexity of O(1). They are unordered collections of data values, used to store key-value pairs. Unlike other data types that hold only a single value as an element, dictionaries hold the key-value pairs, making them more optimized.
    

### 📝 Tasks 📝

### 1️⃣ Diff/erence between List, Tuple, and Set:

Lists are ordered and mutable, meaning you can change their elements. Tuples are ordered but immutable, while sets are unordered and mutable. Sets do not allow duplicate elements.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691048227024/c1fef41b-65d3-4d2f-9731-840e0fab98c0.png align="center")

### 2️⃣ Creating and using the Dictionary:

Let's create the fav\_tools dictionary and use dictionary methods to print your favorite tool just by using the keys of the Dictionary.

```python
fav_tools = {
    1: "Linux",
    2: "Git",
    3: "Docker",
    4: "Kubernetes",
    5: "Terraform",
    6: "Ansible",
    7: "Chef"
}

# Printing your favorite tool (e.g., key=3)
print(fav_tools[3]) # Output: Docker
```

### 3️⃣ Creating a List of cloud service providers:

Let's create a list of cloud\_providers containing "AWS", "GCP", and "Azure".

```python
cloud_providers = ["AWS", "GCP", "Azure"]
```

### 4️⃣ Adding Digital Ocean to the list and sorting it alphabetically:

```python
# Adding "Digital Ocean" to the list
cloud_providers.append("Digital Ocean")

# Sorting the list alphabetically
cloud_providers.sort()

print(cloud_providers) # Output: ['AWS', 'Azure', 'Digital Ocean', 'GCP']
```

Now you're all set to play around with Python data types and data structures! Happy coding! 🚀