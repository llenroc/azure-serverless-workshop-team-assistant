# GitHub Issue Bot 

In this part of the workshop you will extend our bot with the capability to create issue in GitHub. 
We will build logic app with 3 steps. We will use Request / Response Step Connector for invoking the Logic App. Then we will pass the HTTP payload to GitHub Connector and create an issue. 
The last and final step will be to post issue’s link to the Slack channel. Please refer to the diagram below showing the steps in logic app.

![Architecture](Content/Images/1-Architecutre.png)

## Features

This project  provides the following features:

* Create GitHub Issue 
* Post link to the issue back to Slack

## Getting Started

### Prerequisites

1.	You need to have GitHub account, if you don’t please create one here https://github.com

2.	Access to Slack account, please verify it here – https://slack.com

3.	Access to Azure Subscription, please check here https://portal.azure.com


### Walkthrough 

- Login to Azure Portal and Create new Logic App

  - If you don’t see it on your left menu you can search for it via More Services on the bottom
  
  ![Azure Menu](Content/Images/2-AzureLogicApps.png)
  
  - Then type Logic Apps in the Search Bar 
  
  ![Logic App Search](Content/Images/3-AzureMenu.png)
  
  - Press Add button
  
  ![Add Logic App](Content/Images/4-AzureCreateLogicApp.png)
  
  - And fill the required data and press the create button at the bottom
  
  ![Logic App Parameters](Content/Images/5-LogicAppParameters.png)
  
- Next, we will configure the Logic App. In the Logic Apps Designer please select “Blank Logic App” from the Templates section
  
  ![Logic App Parameters](Content/Images/6-LogicAppBlankTemplate.png)
  
  - In the Connector Search select Request / Response Connector
  
   ![Logic App Request](Content/Images/7-LogicAppRequest.png)
   
   - Press “Use sample payload to generate schema” button
   
   ![Logic App Request Body](Content/Images/8-LogicAppRequestBody.png)
   
   - And paste the following JSON
   
      ```javascript
      {
        "title": "My new issue",
        "text": "My new issue description"
      }
      ```
    
    - The contron should look like the picture below. Next press Done 
    
   ![JSON object](Content/Images/9-LogicAppJsonObject.png)
   
    - The result will look like 
   
   ![JSON schema](Content/Images/10-JsonSchema.png)
   
    - Then press “New Step” button, select “Add an action” and select GitHub Connector with Action – “Create an issue”
   
    ![Github step](Content/Images/11-GitHub.png)
   
     - Next, please select Sign In and input your GitHub account credentials and fill the required data that will be used for creating the GitHub issue
   
    ![Github data](Content/Images/12-GitHubFields.png)
   
     - For title and body will pick dynamic content fields - title and text    
     
     ![Github dynamic data](Content/Images/13-GitHubDyniamicValues.png)
     
     - Press “New step” and select Slack with Action – “Post message”
     
     ![Slack post message](Content/Images/14-Slack.png)
     
     - Press Sign In and provide your Slack credentials and confirm the requested permissions 
     
     - Select the channel you want to use and format the message following similar pattern as shown below. We will use dynamic content “Id” field to retrieve issue id for creating the link. Use the link to your repo in the beggining of the expression.
     
     ![Slack dynamic  data](Content/Images/15-SlackDyniamicValues.png)
     
     - Save your work and now you are ready to test. Go to the Request / Response connector step and copy the URL
      ![URL capturing](Content/Images/16-URL.png)
      
      - If you want to your logic app immediatelly, go to Postman or similar app and POST to the provided URL. Do not forget to set Content-Type header to “application/json”
       ![Postman testing 1](Content/Images/17-Postman1.png)
       
      - For the body use the JSON schema we defined several steps ago 
       ![Postman testing 2](Content/Images/18-Postman2.png)
       
      - You should receive the message in Slack as follows
        ![Slack post](Content/Images/19-SlackPost.png)
        
      - You can go to your Logic App home screen and see the history of execution and troubleshoot 
       ![Logic app executions](Content/Images/20-LogicAppsRuns.png)
       
     
 Congratulations! You competed the module! 
 
 You have just added GitHub issue creation as a new capability of our always improving bot!
 
 Thank you!
   
   

