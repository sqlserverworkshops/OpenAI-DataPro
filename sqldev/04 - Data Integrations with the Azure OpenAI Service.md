![](../graphics/microsoftlogo.png)

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

For practical applications, you can use Machine Learning Services to create and deploy machine learning models in stored procedures, which can then be used for predictive analytics, such as forecasting, classification, and clustering tasks. This feature is particularly useful for organizations looking to modernize their data science platforms to Azure or Azure SQL. 
 For more information see the followig link <a href="https://azure.microsoft.com/en-us/updates/machine-learning-services-on-azure-sql-managed-instance-now-generally-available/">Machine Learning Services on Azure SQL Managed Instance now generally available</a>.

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

Microsoft Fabric offers Data Science experiences to empower users to complete end-to-end data science workflows for the purpose of data enrichment and business insights. You can complete a wide range of activities across the entire data science process, all the way from data exploration, preparation and cleansing to experimentation, modeling, model scoring and serving of predictive insights to BI reports.

<br>

<img style="height: 200; box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);" src="https://learn.microsoft.com/en-us/fabric/data-science/media/data-science-overview/data-science-home-page.png">

<br>

The Azure OpenAI service can be used to solve a large number of natural language tasks through prompting the completion API. To make it easier to scale your prompting workflows from a few examples to large datasets of examples.

There are various ways to integrate Azure Open AI into Microsoft Fabirc Notebooks.  Some of the libraries used to invoke and utilize models are the <a href="https://learn.microsoft.com/en-us/semantic-kernel/overview/">Semantic Kernel </a>, the distributed machine learning library <a href="https://microsoft.github.io/SynapseML/">SynapseML</a>, or Open Source models such as <a href="https://python.langchain.com/docs/get_started/introduction/">LangChain</a>.

It is importiant to understand the difference between the he Semantic Kernel, Langchain, and SynapseML and when you would utilize each.

### SynapseML
SynapseML (previously known as MMLSpark), is an open-source library that simplifies the creation of massively scalable machine learning (ML) pipelines. SynapseML provides simple, composable, and distributed APIs for a wide variety of different machine learning tasks such as text analytics, vision, anomaly detection, and many others. SynapseML is built on the Apache Spark distributed computing framework and shares the same API as the SparkML/MLLib library, allowing you to seamlessly embed SynapseML models into existing Apache Spark workflows.

We would use this specifically to enrich and extract insights out of an existing dataset.

### Semantic Kernel
Semantic Kernel is an open-source SDK that lets you easily build agents that can call your existing code. As a highly extensible SDK, you can use Semantic Kernel with models from OpenAI, Azure OpenAI, Hugging Face, and more. By combining your existing C#, Python, and Java code with these models, you can build agents that answer questions and automate processes.

Retrieval Augmented Generation (RAG) is a powerful technique that combines the capabilities of large language models and information retrieval to generate text. It enables the generation of more accurate and informative responses by retrieving relevant information from a document collection. Rapid experimentation is crucial for the successful implementation of RAG systems.

We would use the Semantic Kernel to build an interactive, RAG pattern copilot like, system.  For mor on RAG development see this <a href="https://learn.microsoft.com/en-us/ai/playbook/solutions/generative-ai/rag-experiment-accelerator">link on Using experimentation to accelerate RAG development</a>.

### LangChain
LangChain is an open source framework for building applications based on large language models (LLMs). LLMs are large deep-learning models pre-trained on large amounts of data that can generate responses to user queries—for example, answering questions or creating images from text-based prompts.

Similar to the Semantic Kernel we would utilize LangChain to create intereactive user systems.  LangChain is trained on a pre-trained on open internet dataset.



<i>*Additional services such as Azure AI, formerly known  as Azure Cognitive Service, and their models <a href="https://blog.fabric.microsoft.com/en-in/blog/prebuilt-azure-ai-services-in-fabric-2?ft=All">can also be used in Microsoft Fabric as well.</a></i>


Once we provision an Azure Open AI model and we have our deployment name, API Key, and our Azure Open AI endpoint we can begin the process of calling our Azure Open AI model.  For more on how to provision an Azure Open AI Model and get your API Key see this video, <a href="https://youtu.be/80PNo4tS5sU">How to Provision an Azure Open AI model to use in Microsoft Fabric!</a>

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: Review process and code for using the Semantic Kernel to create a Custom Copilot</b></p>

In this exercise you will review a complete walkthrough of how to utilize the Semantic Kernel to create a custom Copilot using Prompt Engineering in Microsoft Fabric Notebooks. 

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Steps</b></p>

- [Open this resource](https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/notebooks/04%20Promt%20Engineering%20SemanticKernelChatWithYourData%202%20models%20trial%20and%20error%20for%20Github.ipynb) and review the results from the instructions and code. You can download the code and enter your own credentials and other variables to run it on your Microsoft Fabric Capacity once you have [completed the pre-requisites](https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/00%20-%20Pre-Requisites.md).

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: Review process and code for using AI and OpenAI with Microsoft Fabric</b></p>

In this exercise you will review a complete walkthrough of how to utilize Copilot in Microsoft Fabric Notebooks. 

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Steps</b></p>

- [Open this resource](https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/notebooks/Notebook%20-%20Module%204%20Microsoft%20Fabric%20Copilot.ipynb) and review the results from the instructions and code. You can download the code and enter your own credentials and other variables to run it on your Microsoft Fabric Capacity once you have [completed the pre-requisites](https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/00%20-%20Pre-Requisites.md).


<p style="border-bottom: 1px solid lightgrey;"></p>

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/owl.png"><b>For Further Study</b></p>
<ul>
    <li><a href="https://blog.fabric.microsoft.com/en-US/blog/chat-your-data-in-microsoft-fabric-with-semantic-kernel/" target="_blank">Chat your data in Microsoft Fabric with Semantic Kernel</a></li>
     <li><a href="https://youtu.be/0jOEUeOykzQ" target="_blank">How to Chat with Your Data in Microsoft Fabric with Semantic Kernel using Azure OpenAI ChatGPT!</a></li>
     <li><a href="https://youtu.be/GOq5gOdKEVs" target="_blank">Microsoft Fabric Copilot for Notebooks & Data Science! Magic commands to write, execute, & FIX code!</a></li>
    <li><a href="https://www.youtube.com/watch?v=HzdZ0n0lpFw" target="_blank">Data Science in Microsoft Fabric – Model scoring with PREDICT</a></li>
    <li><a href="https://blog.fabric.microsoft.com/en-us/blog/fabric-change-the-game-unleashing-the-power-of-microsoft-fabric-and-openai-for-dataset-search/" target="_blank">Fabric Change the Game: Unleashing the Power of Microsoft Fabric and OpenAI for Dataset Search</a></li>
    <li><a href="https://learn.microsoft.com/en-us/fabric/data-science/open-ai" target="_blank">Azure OpenAI for big data</a></li>
</ul>

Congratulations! You have completed this Module.<a href="https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/05%20-%20DataAI%20Projects%20Best%20Practices.md"> Click this link to continue to the next Module in the Workshop</a>.
