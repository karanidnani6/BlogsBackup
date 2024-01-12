---
title: "Day 77 Grafana Alerting"
datePublished: Fri Jan 12 2024 10:04:32 GMT+0000 (Coordinated Universal Time)
cuid: clrah1vrv000w0al42um5fvcc
slug: day-77-grafana-alerting
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705053635317/d3966a5b-8a77-4b48-9b51-26d2007a4bd0.png

---

### Grafana Alerting

Grafana Alerting allows you to learn about problems in your systems moments after they occur. Create, manage, and take action on your alerts in a single, consolidated view, and improve your team’s ability to identify and resolve issues quickly.

Grafana Alerting is available for Grafana OSS, Grafana Enterprise, or Grafana Cloud. With Mimir and Loki alert rules you can run alert expressions closer to your data and at massive scale, all managed by the Grafana UI you are already familiar with.

### **Task: Setting Up Alerts in Grafana**

Grafana Alerting enables you to quickly identify and address issues within your systems as soon as they arise. Efficiently manage and respond to alerts in a consolidated view, enhancing your team's ability to swiftly pinpoint and resolve problems.

Before proceeding make sure to set up Grafana and the data source in your system.

**Verify Loki Data Source Configuration**

Before creating alerts, ensure that the Loki data source is added and configured correctly. Navigate to the "Settings" or "Data Sources" section in Grafana and confirm that Loki is configured to provide metrics.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703857164627/11686c26-3167-42a7-b38c-5afc049f7122.png?auto=compress,format&format=webp align="left")

**Access the Alerting Section**

On the left-hand side menu, locate and click on the "Alerting" section. This is where you can manage and create new alerts.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703857410093/acc55e98-5748-431d-93c9-5005ccf0e3c0.png?auto=compress,format&format=webp align="left")

**Click on "Create Alert"**

Within the Alerting section, click on the "Create Alert" button to initiate the process of setting up a new alert rule.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703857166777/1662d0b4-ab26-40e2-a6b6-2841a98c9784.png?auto=compress,format&format=webp align="left")

**Define Alert Conditions**

In the alert creation form, give your alert a descriptive name, such as "DNS Failures Alert." Now, it's time to define the conditions that trigger the alert. In our example, we used a query to monitor DNS failures:

```plaintext
sum(rate(cortex_dns_failures_total{name="memberlist"}[5m])) by (name)
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703857171670/d524e805-3dd7-4440-a63c-3b6777d16daa.png?auto=compress,format&format=webp align="left")

Set a threshold value that, when exceeded, will trigger the alert.

**Configure Additional Settings**

Adjust the evaluation interval, which determines how frequently Grafana evaluates the alert conditions. Also, specify the duration for which the condition needs to persist for the alert to be triggered.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703857174073/6b023a14-e073-47ee-a09f-6df270d897b8.png?auto=compress,format&format=webp align="left")

**Set Up Annotations and Notification Channels**

You can add relevant annotations to provide context to the alert. Configure notification channels, such as email or Slack, where you want to receive alerts.

**Preview and Save**

Preview the alert to ensure it aligns with your monitoring requirements. Once satisfied, click "Save" to save the alert configuration.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703857177707/b6494d9a-b5b9-435e-ae4d-2ffe9835fab5.png?auto=compress,format&format=webp align="left")

**Trigger the Alert for Testing**

Testing involves deliberately creating a scenario that triggers the alert condition. For instance, intentionally misconfigure DNS to simulate failures.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703857179346/4359a0bb-716d-4473-b2bc-4685dccf45e4.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703857182677/b7def9ba-7434-4ad6-a389-7e5d1e1e480f.png?auto=compress,format&format=webp align="left")

**Monitor and Review**

Wait for the evaluation interval to pass and monitor the "Alerting" section for the status of your DNS Failures alert. Check the configured notification channels to verify that alerts are being sent.

By following these steps, you can create and test alerts in Grafana, ensuring that your monitoring system is robust and responsive to critical events in your infrastructure.