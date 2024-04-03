![](graphics/microsoftlogo.png)

# Workshop: Unlocking AI Potential for the Data Professional with Azure OpenAI

#### <i>A Microsoft Course from Microsoft Engineering and the FastTrack Team</i>

<p style="border-bottom: 1px solid lightgrey;"></p>

<img style="float: left; margin: 0px 15px 15px 0px;" src="https://raw.githubusercontent.com/microsoft/sqlworkshops/master/graphics/textbubble.png"> <h2>Module 04 - Data Integrations with the Azure OpenAI Service</h2>

Welcome to this Microsoft solutions workshop on *Unlocking AI Potential for the Data Professional with Azure OpenAI*. In this workshop, you'll learn how to unleash the full potential of artificial intelligence. Whether you’re a seasoned Data Professional or just dipping your toes into the world of machine learning, this course will empower you with the knowledge to create groundbreaking solutions.

In each module you'll get more references, which you should follow up on to learn more. Also watch for links within the text - click on each one to explore that topic.

(<a href="https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/00%20-%20Pre-Requisites.md" target="_blank">Make sure you check out the <b>Pre-Requisites</b> page before you start</a>. You'll need all of the items loaded there before you can proceed with the workshop.)

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/education1.png">Topics In This Module</h2>

The following topics are covered in this module:

<dl>

  <dt><a href="#4.1" target="_blank">4.1 - Using OpenAI with Microsoft SQL Server</a><dt>
  <dt><a href="#4.2" target="_blank">4.2 - Using OpenAI with Azure SQL DB</a><dt>
  <dt><a href="#4.3" target="_blank">4.3 - Using Open AI with Microsoft Fabric</a><dt>

</dl>

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2 id="4.1"><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">4.1 Using Open AI with Microsoft SQL Server</h2>

Microsoft SQL Server Machine Learning Services is a feature within SQL Server that allows for the execution of R or Python code directly within the database server. This integration enables complex data science analyses to be performed quickly and securely, without the need to export data sets first. It supports advanced analytics directly within the SQL Server database engine, which can help you to build intelligent applications using scalable and fast machine learning algorithms.

It allows for **direct execution of R and Python scripts**, making it possible to perform data preparation, general-purpose data processing, and machine learning model training within the database. It also supports **failover cluster** and **partitioned data**, which can be used to generate multiple models from partitioned data using T-SQL and R/Python.

You also get **Java extensibility**, allowing for the use of Java code within SQL Server.

You can install the Machine Learning Services feature on SQL Server 2019 and later versions, including on Linux and in containers, and is also part of Azure SQL Managed Instance.

For practical applications, you can use Machine Learning Services to create and deploy machine learning models in stored procedures, which can then be used for predictive analytics, such as forecasting, classification, and clustering tasks. This feature is particularly useful for organizations looking to modernize their data science platforms to Azure or Azure SQL²(https://azure.microsoft.com/en-us/updates/machine-learning-services-on-azure-sql-managed-instance-now-generally-available/).

Additionally, SQL Server Machine Learning Services can be used securely, leveraging Azure services for organizations that might not otherwise do so, and it can help mitigate AI Prompt Injection attacks by chaining AI models together to create powerful ensemble models.

You can see a brief layout of the processing direction for the service here:
<br>

<img style="height: 200; box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);" src="../graphics/Module04-01.png">

<br>

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: Using Machine Learning Services and Python in SQL Server</b></p>

In this Activity, you will review a fully-reproducable Jupyter Notebook that walks through an entire OpenAI integration using SQL Server.

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Steps</b></p>

- [Open this Jupyter Notebook](https://github.com/BuckWoody/PresentationsAndBlogs/blob/master/ai_ml_dl/OpenAI-SQLML.ipynb) and review the results from the instructions and code. You can download the Notebook and enter your own credentials and other variables to run it on your system once you have [completed the pre-requisites](https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/00%20-%20Pre-Requisites.md).

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2 id="4.2"><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">4.2 - Using OpenAI with Azure SQL DB</h2>

While the Machine Learning Services feature from on-premises SQL Server is available on Microsoft Azure VM's and SQL Server Managed Instance (in limited Preview), it is not used in Microsoft Azure SQL Database service. You can, however, access Azure Cognitive Services, Azure OpenAI Services, or any other REST-based endpoint, using a Stored Procedure. 

This allows you to integrate Azure SQL Database with REST APIs, opening up the world of Azure Services to an Azure SQL Database. A single stored procedure call can access event hubs, blob storage, functions, and even AI. This feature is generally available and can be used to call Azure services, popular use cases, and how to call OpenAI right within the database to generate answers using your data.

To set up this access, follow this process:

1. **Gain Access to OpenAI in Azure**: Request access to this service.
2. **Create an OpenAI service**: This is done in the Azure Portal. Provide it with some basic information like resource group, name, and location.
3. **Select Your Model Deployments**: Once the resource is created, click the Model Deployments option on the left side of the page, then click Manage Deployments to open OpenAI Studio in the browser.
4. **Deploy The Model**: In Azure AI Studio, click on the Deployments tab on the left if not already selected then click Create new deployment.
5. **Ask a question**: While in Azure AI Studio, click the Chat tab on the left side of the screen. Use the text field on the bottom to ask a question, then click the paper airplane icon to submit it as a test.
6. **View Code**: On the top of the chat session tile click the View Code button. In the Sample Code modal window, look at the bottom at the Endpoint and Key values. Copy these values.
7. **Access OpenAI REST Endpoints**: Using the External REST Endpoint Invocation stored procedure, you can now ask your OpenAI service a question from within an Azure SQL Database using data from a table.

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: Review process and code for REST Endpoints</b></p>

In this exercise you will review a complete walkthrough of using REST API's with Azure SQL Database. This also shows the same use-case shown for on-premises SQL Server. 

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Steps</b></p>

- [Open this resource](https://devblogs.microsoft.com/azure-sql/using-openai-rest-endpoints-with-azure-sql-database/) and review the results from the instructions and code. You can download the code and enter your own credentials and other variables to run it on your system once you have [completed the pre-requisites](https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/00%20-%20Pre-Requisites.md).


<p style="border-bottom: 1px solid lightgrey;"></p>

<h2 id="4.3"><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">4.3 - Using Open AI with Microsoft Fabric</h2>

Microsoft Fabric has multiple AI constructs. It contains various CoPilots to assist in development, management and troubleshooting, and also has multiple code inputs for AI and Azure OpenAI access for your code. These generally involve using the Python SDK inside Synapse and other Spark-access locations. 

<br>

<img style="height: 200; box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);" src="https://learn.microsoft.com/en-us/fabric/data-science/media/tutorial-data-science-prepare-system/switch-to-data-science.png">

<br>

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: Review process and code for using AI and OpenAI with Microsoft Fabric</b></p>

In this exercise you will review a complete walkthrough of using REST API's with Microsoft Fabric. 

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Steps</b></p>

- [Open this resource](https://learn.microsoft.com/en-us/fabric/data-science/open-ai) and review the results from the instructions and code. You can download the code and enter your own credentials and other variables to run it on your system once you have [completed the pre-requisites](https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/00%20-%20Pre-Requisites.md).


<p style="border-bottom: 1px solid lightgrey;"></p>

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/owl.png"><b>For Further Study</b></p>
<ul>
    <li><a href="url" target="_blank">TODO: Enter courses, books, posts, whatever the student needs to extend their study</a></li>
</ul>

Congratulations! You have completed this Module.<a href="https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/05%20-%20DataAI%20Projects%20Best%20Practices.md"> Click this link to continue to the next Module in the Workshop</a>.
