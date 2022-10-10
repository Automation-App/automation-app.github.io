---
layout: default
title: Microsoft Azure Setup
parent: Initial Setup
nav_order: 1
permalink: /setup/azure/
---

To manage Runbooks in Azure this app needs contributor access to the Automation Accounts that you wish to use. You can also give contributor access to the app on a subscription or resource group level. This way the app will have access to all Automation Accounts in each subscription or resource group. In the following guide we will give access to a specific Automation Account only. Please consult your Azure administrator to ensure that the access is setup to best fit your environment.
When you are ready, go to portal.azure.com and login with your azure credentials.
To complete this guide, you need to have sufficient rights in your Azure platform. You can complete this guide if you are Global Administrator of your Azure Tenant or if App Registration has been enabled in you Azure Tenant and you have sufficient access to the subscription in which the Azure Automation account resides.
To check if "App Registration" is activated. Click on "Azure Active Directory" in the menu to the left and then select "User Settings". Ensure that the option "Users can register applications" is set to yes

 

Now we are ready to configure Azure. Go to "Azure Active Directory" in the menu to the left. Then click on "App registrations". This will give you a list of registered Apps. If ServiceNow is already on this list, simply click on it to open it. If not, you can add it by clicking the little "+ New registration" at the top left of the list.

 

Under "Name" you enter "ServiceNow" or something that makes sense to you. Under the account type select "Accounts in this organizational directory only". Under "Redirect URI" add the link to your instance followed by "/login.do". Ex. https://myinstance.service-now.com/login.do. Then click the "Register" button at the bottom.
TIP: If you have configured single sign on for your ServiceNow instance using Azure Active Directory, there should already be a registered App that you can use.
Once the Application is created you will see a page that looks like below. If the menu to the right is not visible, click the "Settings" button in the upper left corner.

 

Copy and store the "Application (client) ID" and "Directory (tenant) ID" as you will need this later to configure ServiceNow. Then click the "Certificates & Secrets" under "Manage".

 

Click on the "New client secret" button to generate a new client secret.
 

Enter something meaningful in the "Description" field and select an expiration date. For ease of use I selected "Never". Then click "Add".

 

Once you click "add" a key will be generated. This is the only time that you will be able to see this key, so make sure that you copy it and store it somewhere safe together with the "Application (client) ID" and "Directory (tenant) ID" that you copied earlier.
Now we need give the app access to your Automation accounts. To do this select "Automation Accounts" from the main menu to the left. If you already have an Automation Account, click open it by clicking on the name of the Automation Account in the list. If you do not already have an Automation Account, you can create a new one by clicking the "+ Add" button at the top of the list.

 

If you create a new Automation Account, give the Automation Account a Name and select the Subscription. Select an existing Resource Group or create a new one. Select the location and choose if you would like to create an Azure Run As account. Click "Create" once everything is filled out.
Notice: It may take a few seconds before the Automation Account is created. Click "Refresh" on the list until you see the Automation Account and then click on the name to open the Automation Account.

 

Click on "Access control (IAM)" in the menu to the left.

 

Click on "+ Add" button at the top of the page and select "Add role assignment".

 

Select "Contributor" under "Role". Next search for the ServiceNow application that we previously created and select it. Then click "Save".
We are now done setting up Azure and are ready to configure ServiceNow. Ensure that you have recorded the following information:
* Application (client) ID
* Directoy (tenant) ID
* Client secret
