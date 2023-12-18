---
title: "#Day46:Set up CloudWatch alarms and SNS topic in AWS"
datePublished: Mon Dec 18 2023 04:47:43 GMT+0000 (Coordinated Universal Time)
cuid: clqafq5ls000408jm2awwg6oh
slug: day46set-up-cloudwatch-alarms-and-sns-topic-in-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699598949004/e6789f3f-3543-4f7f-a3c1-caf281205733.png
tags: aws, cloudwatch, 90daysofdevops

---

Hey Cloud Enthusiasts! 👋 Today, let's embark on a journey into the world of AWS monitoring using two powerful services: Amazon CloudWatch and Simple Notification Service (SNS). 🌐✨

### Amazon CloudWatch: Keeping an Eye on Your AWS Resources

Amazon CloudWatch is your trusty companion for real-time monitoring of AWS resources and applications. 🕵️‍♂️ It allows you to collect and track metrics, providing valuable insights into the performance of your AWS environment. 🚀

Whether it's keeping tabs on your EC2 instances, tracking the health of your databases, or monitoring custom application metrics, CloudWatch has got you covered! 📈💻

### Amazon SNS: Your Notifier in the Cloud 📲🔔

Enter Amazon Simple Notification Service (SNS), the go-to solution for seamless notification delivery within AWS since 2010. 🎉 SNS facilitates the low-cost, high-speed delivery of messages, especially tailored for mobile users. 📢📱

### Let's Get Hands-On: Setting Up a CloudWatch Alarm 🚨💼

Now, let's roll up our sleeves and create a CloudWatch alarm that monitors our billing and shoots us an email when it hits $2. 💸📧

**Step 1: Sign In to the AWS Management Console**

To embark on your journey of cost management and resource monitoring, start by signing in to the AWS Management Console.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695478109552/f12a5d02-25c0-4076-ab75-a9383430a657.png?auto=compress,format&format=webp align="left")

**Step 2: Access Billing Dashboard**

Once you're in the console, navigate to the Billing Dashboard by selecting it from the navigation bar

**Step 3: Configure Alert Preferences**

Within the Billing Dashboard, choose **"Billing preferences"** from the navigation bar. Here, you can configure your **"Alert preferences"** to receive notifications regarding your AWS billing.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702871830831/b884a708-7a19-4265-b7b1-37068abc4f0d.png align="center")

**Step 4: Create a Billing Alarm**

Now, let's create a billing alarm to keep a close eye on your AWS spending:

1. Go to the AWS Management Console and navigate to the **CloudWatch service**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702871915572/cd120204-7065-4d71-958a-10f721f847a0.png align="center")
    
2. In the navigation pane, select **"Alarms"** and click the **"Create Alarm"** button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702871991047/9e27201e-f689-4ad7-b0c5-82b8ae5bd396.png align="center")
    
3. In the **"Create Alarm Wizard"** under the **"Select metrics"** section, scroll down and choose **"Billing."**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695478282598/608e7320-94a5-483f-8ca9-6dd0ccd1c02f.png?auto=compress,format&format=webp align="left")
    
4. Select **"Total Estimated Charge"** and click **"Select metric."**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702874174418/65798ea0-d65b-4d17-8ae9-39132b86d31a.png align="center")
    
5. Under **"Conditions"** set the threshold to the desired amount, such as **"$2"**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702874246492/d962cbff-81c4-4011-8a37-9fd3217536bf.png align="center")
    
6. Configure the actions to send an email notification when the alarm state is triggered. You can either **create a new SNS topic** or **choose an existing one** and set up email notifications in Amazon SNS.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702874663751/6ae5cb7c-f422-4dfc-9069-9f5e58ccce75.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702874641696/b712e2b4-f3e4-4357-90c8-d21c64174eef.png align="center")
    
7. Confirm the subscription to enable the CloudWatch service.
    
8. Provide a name for the alarm and add a description if needed.
    
9. Click the **"Create Alarm"** button to create the billing alarm.
    

**Step 5: Deleting the Billing Alarm**

Managing your alarms is just as important as creating them. Here's how to delete a billing alarm:

1. In the **"Actions"** dropdown menu, choose **"Delete."**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702874757654/0f7308de-ca64-4dc3-b369-081d93440cca.png align="center")
    
2. Confirm the deletion when prompted.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702874782870/5bac6c78-de63-423c-a17b-752e0dea2fca.png align="center")