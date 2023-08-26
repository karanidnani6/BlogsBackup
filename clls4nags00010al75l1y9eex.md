---
title: "#Day24:Complete Jenkins CI/CD Project"
datePublished: Sat Aug 26 2023 14:38:53 GMT+0000 (Coordinated Universal Time)
cuid: clls4nags00010al75l1y9eex
slug: day24complete-jenkins-cicd-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693026554483/cdbaf5f6-c0e3-4c3a-82c3-90b72d37ad91.png
tags: 90daysofdevops, jenkins-pipeline

---

### GitHub integration

GitHub integration in Jenkins allows you to connect your Jenkins automation server with your GitHub repositories, enabling you to automate various aspects of your software development workflow. This integration can streamline processes such as continuous integration, automated testing, and deployment.

### Git webhooks

Git webhooks are a way for a Git repository to notify external systems, such as Continuous Integration (CI) servers, chat platforms, or other services, about events that occur within the repository. Webhooks allow you to automate processes and trigger actions in response to these events. In the context of version control systems like Git (and platforms like GitHub, GitLab, or Bitbucket), webhooks are often used to trigger automated build, test, and deployment processes.

Here's how git webhooks generally work:

1. **Setting Up a Webhook:**
    
    * In your Git repository (e.g., on GitHub), you can configure a webhook by providing a URL that points to the external service you want to notify.
        
    * This URL is often a route on your CI server or another application that can process the incoming webhook payloads.
        
2. **Event Triggers:**
    
    * When certain events occur in the repository, such as pushing new code, creating a pull request, or merging code, the webhook is triggered.
        
    * The webhook sends an HTTP POST request to the provided URL with a payload containing information about the event.
        
3. **Payload Processing:**
    
    * The external service (e.g., CI server) receives the HTTP POST request with the payload.
        
    * The payload contains data about the event, such as the type of event, details about the commit(s), pull request information, and more.
        
4. **Automation and Actions:**
    
    * Based on the information in the payload, the external service can perform various actions.
        
    * Common actions include triggering a build process, running automated tests, generating reports, deploying code, and updating status indicators on the repository or pull request.
        
5. **Feedback and Status:**
    
    * After processing the payload and performing actions, the external service might send feedback back to the Git repository.
        
    * This feedback could include status updates, comments, or indicators showing whether the automated processes succeeded or encountered issues.
        

Common use cases for Git webhooks include:

* **Continuous Integration (CI):** Triggering automated builds and tests whenever new code is pushed to the repository.
    
* **Pull Request (PR) Validation:** Running tests and checks on code changes submitted through pull requests to ensure they meet quality standards before merging.
    
* **Deployment:** Automatically deploying code to staging or production environments after successful tests.
    
* **Notifications:** Sending notifications to chat platforms or email services to inform developers or teams about specific events in the repository.
    
* **Issue Tracking:** Automatically linking commits and branches to relevant issues in issue tracking systems.
    

It's important to ensure that your webhook handlers are secure and can handle potential issues gracefully, as webhooks often involve external communication and automation that can impact your development workflow. Additionally, each Git platform (GitHub, GitLab, Bitbucket, etc.) might have slightly different implementations and options for configuring webhooks, so refer to their respective documentation for precise setup instructions.

# Task-01

* Fork [this](https://github.com/LondheShubham153/node-todo-cicd.git) repository:
    
* Create a connection to your Jenkins job and your GitHub Repository via GitHub Integration.
    
* Read About [GitHub WebHooks](https://betterprogramming.pub/how-too-add-github-webhook-to-a-jenkins-pipeline-62b0be84e006) and make sure you have CICD setup
    

Step:1

we had already created ci-cd in #Day23 task you can refer my previous blog . From step 2 we can integrate through webhook

Step:2

Now to integrate github and Jenkins we need to create Github Webhooks.

Under Build Triggers: Select GitHub hook trigger for Gitscm Polling.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693049192845/adb2c12b-824b-4315-b164-c7461391646b.png align="center")

step 3: **Webhooks create the hyperlink between GitHub & Jenkins.**

**Any changes made to the GitHub repo will be automatically identified by Jenkins and will be pushed to the webhook URL.**

**To create Webhook**: Go to **Settings** of your forked GitHub repo.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693049324972/44c55258-b875-4575-b3bd-a9c420dd84a3.png align="center")

  
step 4: click on **Add Webhook**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691976163901/c78f70e4-e9cc-44b9-b6ea-e18371e6b2c8.png?auto=compress,format&format=webp align="left")

step 5: Now webhooks url syntax: [**jenkins**](http://jenkins/) **public ip:8080/github-webhook/**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693055104740/c696c038-513b-4842-a92b-4cf9f6da0549.png align="center")

step 6: After setting up the webhooks do not forget to **refresh the page** unless the **webhook URL is ticked** as shown below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693057435880/042697be-1b02-4d80-bf16-ecff84a4c756.png align="center")

step 7: Now come back to the Jenkins dashboard, click on **Build steps** &gt; Execute Shell &gt; type the command that will be executed after the job is built & save.

step 8: Now I will make **slight changes to the code** by adding a comment at the beginning of the docker file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693058486157/e6071797-93ae-4f86-b21e-6cc3aac32a68.png align="center")

step 9: **Commit** the changes made.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693058572753/22022a67-0194-43f7-840f-bf57460601c7.png align="center")

step 10: Exactly after few seconds of the commit made onto the code, the Job in the Jenkins dashboard starts to build automatically.

tep 18: And the job is successful.

step 19: You can click on the **Console Output** to view the output.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693059675735/499a6153-53fc-41ab-abc2-b676bfd953cb.png align="center")

# **Task-02**

* In the Execute shell run the application using Docker compose
    
* You will have to make a Docker Compose file for this Project
    
* Run the project and give yourself a treat:)
    

For Task2 follow the same as the above steps, but **change the execute shell command as below :**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691993716952/4cebd9a6-dc99-47c7-a7ee-9e433b5344c5.png?auto=compress,format&format=webp align="left")