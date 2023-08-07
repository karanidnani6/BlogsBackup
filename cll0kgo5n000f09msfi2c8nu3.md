---
title: "#Day15:Python Libraries for DevOps"
datePublished: Mon Aug 07 2023 07:44:05 GMT+0000 (Coordinated Universal Time)
cuid: cll0kgo5n000f09msfi2c8nu3
slug: day15python-libraries-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691117270249/54b2031d-57c1-443a-be3d-26e02690a5f5.jpeg
tags: python, libraries, 90daysofdevops

---

As a DevOps Engineer, you have the power to automate tasks and manage infrastructure like a superhero! 🦸‍♂️ One of your essential skills is working with different types of files, such as `txt`, `json`, and `yaml`. Each format serves a specific purpose and has its own unique characteristics. As a Python programmer, it's essential to understand how to work with these formats to efficiently handle data. Let's dive into each format and explore how Python can help us navigate this trio! 🚀

### **1\. txt - The Plain Text Format** 📝

The `txt` format is the simplest of all. It contains plain, human-readable text without any special formatting or structure. This format is widely used for documents, logs, and configurations.

In Python, working with `txt` files is straightforward using the built-in `open()` function. This function allows you to read and write text data.

### **2\. json - The JavaScript Object Notation** 🌐🗝️

JSON (JavaScript Object Notation) is a popular data interchange format. It's widely used for configuration files, data exchange between programs, and APIs.

In Python, the `json` library allows you to work with JSON data. It can easily convert Python dictionaries to JSON format and vice versa.

### **3\. yaml - The Human-Readable Data Serialization Format** 📝🗝️

YAML (YAML Ain't Markup Language) is a data serialization format known for its human-readable structure. It's commonly used for configuration files and data serialization.

Python provides the `pyyaml` library to work with YAML data. It can read YAML and convert it into Python dictionaries, making it easy to handle.

### **Tasks for a DevOps Engineer** 🛠️

As a DevOps Engineer, you'll often come across tasks that require your superpowers with these libraries. Let's dive into some exciting missions:

**Mission 1: Create a Dictionary and Save it to JSON** 📝

You can use the `json` library to save a Python dictionary to a JSON file. Here's how you do it:

```plaintext
import json

# Create a sample dictionary
data = {
    "aws": "ec2",
    "azure": "VM",
    "gcp": "compute engine"
}

# Save the dictionary to a JSON file
with open("services.json", "w") as json_file:
    json.dump(data, json_file, indent=4)
```

**Mission 2: Read JSON File and Print Cloud Service Providers** 🖨️

You can use the `json` library again to read the JSON file and print the cloud service providers and their corresponding services:

```plaintext
import json

# Read the JSON file
with open("services.json", "r") as json_file:
    data = json.load(json_file)

# Print the service names of every cloud service provider
for provider, service in data.items():
    print(f"{provider} : {service}")
```

The output will look like this:

```plaintext
aws : ec2
azure : VM
gcp : compute engine
```

**Mission 3: Convert YAML to JSON** 🔄

For this mission, you'll need the help of `pyyaml`. It will convert the contents of a YAML file to JSON:

```plaintext
import yaml
import json

# Read the YAML file
with open("services.yaml", "r") as yaml_file:
    data = yaml.safe_load(yaml_file)

# Convert YAML data to JSON format
json_data = json.dumps(data, indent=4)

# Print the JSON data
print(json_data)
```

### **Conclusion** 🎉

With these superhero libraries at your disposal, you can effortlessly parse and manage different file formats like a true DevOps champion! 🚀 So go ahead and unleash the power of Python libraries to conquer your DevOps missions with confidence! 💪