![](../graphics/microsoftlogo.png)

# Unlocking AI Potential for the Data Professional with Azure OpenAI

#### <i>A Microsoft Course from the SQL Server team</i>

<p style="border-bottom: 1px solid lightgrey;"></p>

<img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/textbubble.png"> <h2>00 Pre-Requisites</h2>

The "Unlocking AI Potential for the Data Professional with Azure OpenAI" workshop is taught using the following components, which you will install and configure in the sections that follow. 

*(Note: For this class <b>you do not need to install anything.  You will not be executing labs within this class.  The documentation and notebooks provided in this class are for further learning and exploration after the class.</b>)*

<b><u>For this workshop you will not need to download or install any software prior to class.  The format of this workshop is lecture and demo. </b></u> 

If you wish to execute the sample code after this class, you will use Microsoft Windows as the base workstation, altough Apple and Linux operating systems can be used in production. You can <a href="https://developer.microsoft.com/en-us/windows/downloads/virtual-machines" target="_blank">download a Windows 10 Workstation Image for VirtualBox, Hyper-V, VMWare, or Parallels for free here</a>. 

The other requirements are:

- **Microsoft Azure**: This workshop uses the Microsoft Azure platform to host the Kubernetes cluster (using the Azure Kubernetes Service), and optionally you can deploy a system there to act as a workstation. You can use a free Azure account, an MSDN Account, your own account, or potentially one provided for you, as long as you can create about $100.00 (U.S.) worth of assets.
- **Microsoft Azure will be required for Azure Open AI, Azure Open AI Studio, Microsoft Fabric, and Azure SQL** - A Microsoft Fabric Tenant and workspace will be required seperately to run Microsoft Fabric, a minimum of an F64 will be required to perform Copilot actions in Microsoft Fabric.


*Note that all following activities must be completed after the class, we will not be walking through labs during the class- there will not be time to perform these operations during the workshop.*

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity 1: Set up a Microsoft Azure Account</b></p>

You have multiple options for setting up Microsoft Azure account to complete this workshop. You can use a free account, a Microsoft Developer Network (MSDN) account, a personal or corporate account, or in some cases a pass may be provided by the instructor. (Note: for most classes, the MSDN account is best)

**Unless you are explicitly told you will be provided an account by the instructor in the invitation to this workshop, you must have your Microsoft Azure account and Data Science Virutal Machine set up before you arrive at class.**

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/checkbox.png"><b>Option 1 - Free Account</b></p>

The free account gives you twelve months of time, and a limited amount of resources. Set this up prior to coming to class, and ensure you can access it from the system you will bring to the class.

- [Open this resource, and click the "Start Free" button you see there](https://azure.microsoft.com/en-us/free/)

**NOTE: You can only use the Free subscription once, and it expires in 12 months. Set up your account and create the DSVM per the instructions below, but ensure that you turn off the VM in the Portal to ensure that you do no exceed the cost limits on this account. You will turn it off and on in the classroom per the instructor's directions.**

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/checkbox.png"><b>Option 2 - Microsoft Developer Network Account (MSDN) Account</b></p>

The best way to take this workshop is to use your [Microsoft Developer Network (MSDN) benefits if you have a subscription](https://marketplace.visualstudio.com/subscriptions).

- [Open this resource and click the "Activate your monthly Azure credit" button](https://azure.microsoft.com/en-us/pricing/member-offers/credit-for-visual-studio-subscribers/)

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/checkbox.png"><b>Option 3 - Use Your Own Account</b></p>

You can also use your own account or one provided to you by your organization, but you must be able to create a resource group and create, start, and manage a Data Science Virtual Machine (DSVM) and an Azure AKS cluster. 

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/checkbox.png"><b>Option 4 - Use an account provided by your instructor</b></p>

Your workshop invitation may have instructed you that they will provide a Microsoft Azure account for you to use. If so, you will receive instructions that it will be provided.

**Unless you received explicit instructions in your workshop invitations, you much create either a free, MSDN or Personal account. You must have an account prior to the workshop.**

## Microsoft Fabric
- In order to execute workloads using Microsoft Fabric.  In order to do this you must first sign up for, or currently have, an M365 account with the proper permissions.  If you do not have an M365 account with the proper permissions you can sign up for a 90 day free trial of M365.
- Next you must have a Power BI Pro license.  If you do not have a Power BI license you can sign up for one for free 60 day trial.
- You will also require a Microsoft Fabric Capacity or a Free trial Microsoft Fabic Capacity which will run for 60 days.  
- Signing up for M365, Power BI, and Microsoft Fabric is free and does not require a credit card.
- Your Power BI Tenent must have Fabric Capacity enabled in order to create a Microsoft Fabric Workspace.  Please review, [Enable for your tenant](https://github.dev/sqlballs/MicrosoftFabricPre-Con/blob/main/fabricoverview/00%20-%20Pre-Requisites.md) and [Enable for a capacity](https://learn.microsoft.com/en-us/fabric/admin/fabric-switch#enable-for-a-capacity) for instructions in how to do this. 

> You can also create a free Azure Subscription for 1 year with a $200 credit, and then provision a Microsoft Fabric Capacity and attach it to a Power BI Workspace.

## Microsoft Fabric Required Permissions

In order to be a Microsoft Fabric Admin for your orginization, you must be in one of the following roles

- Global administrator
- Power Platform administrator
- Microsoft Fabric administrator

<p>

These roles are assigned in the Microsoft 365 Administration portal.  Microsoft 365 user admins assign users to the Fabric administrator or Power Platform administrator roles in the Microsoft 365 admin portal.
<p>

The other requirements are:

- **A M365 Subscription or orginizational account with the proper rights** - This will allow you to create a "domain" account which can be used to sign up for Power BI.
- **A Power BI License** - You must have a Power BI License in order to utilize Microsoft Fabric.
- **A Microsoft Fabric Capacity** - This could be a free trial or a provisioned Azure Capacity.
- **A Computer with an Internet Browser** - To participate in the activities in this Workshop you must have a computer and an internet browser.
- **A Working Internet Connection** - Microsoft Fabric is a SaaS, Software as a Service, platform hosted on the Internet.  You must have internet connectivity to access Microsoft Fabric.
- **Potentially: A Microsoft Azure Account**: This is only required if you do not have a free trial Microsoft Fabric Capacity. This workshop uses the Microsoft Fabric which  platform to host the Microsoft Fabric Capacity, and optionally you can deploy a Microsoft Fabric Capacity. You can use a free Azure account, an MSDN Account, your own account, or potentially one provided for you, as long as you can create about $200.00 (U.S.) worth of assets. 

*Note that all following activities must be completed prior to class - there will not be time to perform these operations during the workshop.*

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: Set up M365 account, Power BI License, Microsoft Fabric Capacity, Validate you have a computer, and Internet</b></p>

<p>

Open this link in a seperate tab or window and follow all of the instructions, [Accessing Microsoft Fabric for developers, startups and enterprises!](https://blog.fabric.microsoft.com/en-us/blog/accessing-microsoft-fabric-for-developers-startups-and-enterprises/)




<h2 id="2"><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">Verification of access to Microsoft Fabric Workspace for the Copilot Notebook</h2>


Validate that you have a Microsoft Fabric Enabled Workspace:
- Navigate to [Tutorial: Create a Microsoft Fabric workspace](https://learn.microsoft.com/en-us/fabric/data-warehouse/tutorial-create-workspace)
- Navigate to your Microsoft Fabric enabled workspace
- Click +New
- Click Show all
- Validate that you see the options available to you to create Microsoft Fabric objects such as a Lakehouse, a Data Warehouse, Pipelines, KQL Database, or an EventStream


Next, Continue to <a href="https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/01%20-%20Introduction%20and%20Overview.md" target="_blank"><i>Module 01</i></a>.
