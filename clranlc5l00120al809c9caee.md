---
title: "Day - 78 (Grafana Cloud)"
datePublished: Fri Jan 12 2024 13:07:37 GMT+0000 (Coordinated Universal Time)
cuid: clranlc5l00120al809c9caee
slug: day-78-grafana-cloud
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705058173858/47dc7c7e-6b1c-41c7-92a9-c864ed7e44d6.jpeg

---

For effective monitoring in DevOps using Grafana, follow these steps:

Begin by visiting "[**Grafana.com**](http://grafana.com/)" through a Google search and proceed to create a free account, making the process easy and convenient. I recommend using Google for registration.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704279343609/7107898c-6710-4518-81b3-9ce4e440312b.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704279356514/33662b32-4a97-44c4-ac20-ee405a64f152.png?auto=compress,format&format=webp align="left")

Once your account is set up, select your Team URL and Deployment Region, and then click on "Finish Setup."

Grafana will work in the background to create an instance for you.

At this stage, focus on the initial step of "Creating a Dashboard."

Choose the "Linux Dashboard" from the various available options.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704279403372/88b6300b-4c68-40a1-aa9b-df49b0712e9a.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704304287020/7cf08fae-b7d4-4473-931c-1ccf74391a50.png?auto=compress,format&format=webp align="left")

Specify your OS as Debian, Architecture as Amd64, and provide the Hostname as the Public IP of your EC2 instance. Click on "Install Integration."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704304306702/2c566bc2-16b8-49b1-85e8-3b85584dbcf8.png?auto=compress,format&format=webp align="left")

Post "Install Integration," a custom installation will be generated, along with an API key connecting Grafana Cloud and your EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704304336141/10ccb6c5-1eb8-41f8-802e-3dc6f1a72071.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704304351264/e687883e-627d-4b07-9831-b68c93f29104.png?auto=compress,format&format=webp align="left")

Copy the API key, SSH into your server, and paste the key to initiate the installation.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704304378778/f48924b2-e026-4088-8a23-f3bfd0f30233.png?auto=compress,format&format=webp align="left")

Configure the grafana config yaml file as given in the instructions below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704304671686/b3bd3e04-efff-4956-8b69-e93617b9b005.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704304674000/d31a007a-858c-4cbe-9505-c43c93a9eadf.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704304683199/68dd14ee-0aae-45c3-b151-8c54776dedd6.png?auto=compress,format&format=webp align="left")

The yaml file will look like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704304709008/a0738fd9-77b0-4768-8513-fb13c3f15596.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704304712197/080c0cea-60bb-4b8c-baaa-62788ea75606.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704304715811/ecd8241f-34d8-4605-b3bc-df41a842d14a.png?auto=compress,format&format=webp align="left")

Execute the command `sudo systemctl restart grafana-agent.service` to restart the Grafana agent.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704304396978/e03714c1-cc20-4d35-895f-d5cb2f471c2b.png?auto=compress,format&format=webp align="left")

Verify the agent's status to ensure it is running smoothly.

Return to the Grafana Dashboard and click on "Test Integration." You can also install pre-installed dashboards.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704304917802/fbbab5c4-660e-482b-894a-a85c277331dc.png?auto=compress,format&format=webp align="left")

Proceed to "View Dashboard."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704305017169/852c121b-cebc-412f-b615-9d9c42e42be7.png?auto=compress,format&format=webp align="left")

Navigate to the desired choice to access server monitoring data on Grafana.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704305076276/f9fd2caf-ef0e-4b05-827e-2575f1d9578e.png?auto=compress,format&format=webp align="left")

Now let's set up Data Source that is CloudWatch.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704306775686/2eb0e0a1-2114-456d-9e64-92cf52a11b8a.png?auto=compress,format&format=webp align="left")

Go to Connections&gt; Add new Connection and search for CloudWatch.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704306776904/9dbf2ec2-8c3d-45a1-8e8d-b7a5e1d8565c.png?auto=compress,format&format=webp align="left")

Configure the Connection Details by inserting IAM UserName and Access Key.  
Make sure the IAM user which you are adding has access to this.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704306779981/5c52ba23-e543-4312-881c-311c0932f542.png?auto=compress,format&format=webp align="left")

Now, Click on Save and Test if it is successfully Configured.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704306782964/4ff9cf1a-ee70-43ba-84a4-6f7303bcf014.png?auto=compress,format&format=webp align="left")

You can check the Dashboards that can be accessed using it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704306787401/22688ccc-c86d-4678-aa05-21a8f171ba58.png?auto=compress,format&format=webp align="left")

Search for the Billing Usage and go to that Dashboard.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704306791676/17ff87a2-5d0e-48f4-9b7e-255c0c7a0f06.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704306796409/13e21386-96c3-49ea-96c2-8e8928cb90c2.png?auto=compress,format&format=webp align="left")

To establish alert rules, go to the Alerts & IRM section in the console and click on "Alert Rules."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704308261913/f4f11a3e-e27f-482e-9f5e-fa0b7ce7f369.png?auto=compress,format&format=webp align="left")

Choose the CloudWatch option and proceed to create a new alert.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704308266720/c3f10e40-cb29-4bbf-9ea3-a6ff00d89ce6.png?auto=compress,format&format=webp align="left")

Adjust the alert rule settings to specifically configure the AWS Billing alert.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704308271607/a30e3bfd-77fb-4df1-8b52-146cc87c6477.png?auto=compress,format&format=webp align="left")

This configuration enables us to receive notifications whenever there is a surge in AWS resource usage billing.

In the same way, we can monitor other resources.