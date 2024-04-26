![](graphics/microsoftlogo.png)

# Workshop: Unlocking AI Potential for the Data Professional with Azure OpenAI

#### <i>A Microsoft Course from Microsoft Engineering and the FastTrack Team</i>

<p style="border-bottom: 1px solid lightgrey;"></p>

<img style="float: left; margin: 0px 15px 15px 0px;" src="https://raw.githubusercontent.com/microsoft/sqlworkshops/master/graphics/textbubble.png"> <h2>Module 02 - Implementing AI Studio</h2>

Welcome to this Microsoft solutions workshop on *Unlocking AI Potential for the Data Professional with Azure OpenAI*. In this workshop, you'll learn how to unleash the full potential of artificial intelligence. Whether you’re a seasoned Data Professional or just dipping your toes into the world of machine learning, this course will empower you with the knowledge to create groundbreaking solutions.

In each module you'll get more references, which you should follow up on to learn more. Also watch for links within the text - click on each one to explore that topic.

(<a href="https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/00%20-%20Pre-Requisites.md" target="_blank">Make sure you check out the <b>Pre-Requisites</b> page before you start</a>. You'll need all of the items loaded there before you can proceed with the workshop.)

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/education1.png">Topics In This Module</h2>

The following topics are covered in this module:

<dl>

  <dt><a href="https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/02%20-%20Implementing%20AI%20Studio.md#21---what-is-azure-ai-studio" target="_blank">2.1 - What is Azure AI Studio<dt>
  <dt><a href="https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/02%20-%20Implementing%20AI%20Studio.md#22---getting-around-in-azure-ai-studio" target="_blank">2.2 - Getting around in Azure AI Studio<dt>
  <dt><a href="https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/02%20-%20Implementing%20AI%20Studio.md#23---governance-and-administration" target="_blank">2.3 - Governance and Administration<dt>
  <dt><a href="https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/02%20-%20Implementing%20AI%20Studio.md#24---accesing-the-studio" target="_blank">2.4 - Accesing the studio<dt>

</dl>

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">2.1 - What is Azure AI Studio</h2>

<br>

Azure AI Studio is a unified platform designed for developers to build, evaluate, and deploy generative AI applications. 

<br>

<img style="height: 400; box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);" src="https://learn.microsoft.com/en-us/azure/ai-studio/media/explore/ai-studio-home.png">

Here are some key features of Azure AI Studio :

- All-in-one AI platform: Azure AI Studio serves as a one-stop-shop for exploring, building, testing, and deploying generative AI solutions and custom copilots.
- Enterprise-grade platform: It provides an enterprise-grade platform where developers can interact with a project code-first via the Azure AI SDK and Azure AI CLI.
- Collaborative environment: Azure AI Studio fosters collaboration with shared files and connections to pretrained models, data, and compute.
- Scalability: The platform facilitates scalability for transforming proof of concepts into full-fledged production with ease.
- Continuous monitoring and refinement: It supports long-term success through continuous monitoring and refinement.

Azure AI Studio is grounded in responsible AI practices and empowers developers of all abilities and preferences to innovate with AI and shape the future.
It's currently in public preview.

<br>

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">2.2 - Getting around in Azure AI Studio</h2>

<br> 

With Azure AI Studio, you can evaluate large language model (LLM) responses and orchestrate prompt application components with prompt flow for better performance. The platform facilitates scalability for transforming proof of concepts into full-fledged production with ease. Continuous monitoring and refinement support long-term success.

To navigate Azure AI Studio, you can use four tabs: Home, Explore, Build, and Manage1. Let’s take a quick look at what each tab offers.

### Home
The **Home** tab in Azure AI Studio serves as the starting point for your data science projects. Here, you'll find an organized overview of your ongoing work, including projects, datasets, and experiments. Take advantage of this central hub to efficiently manage your AI development endeavors.

<img style="height: 400; box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);" src="https://learn.microsoft.com/en-us/azure/ai-studio/media/explore/ai-studio-tab-home.png">

### Explore
This is where you can find a model, service, or solution to start working on. The goal is that you can find, and try, all of Azure AI from here. Explore is stateless, so when you want to save settings and assets such as data you create a project and continue on the Build page.

- Explore has a growing suite of tools, patterns, and guidance on how to build with AI so that enterprise can scale PoCs with a paved path to full production.
- Guidance about how to select the right models and tools based on your use case.
- Test AI solutions with your app code and data and receive guidance on standardized methods to evaluate the model, prompt, and overall application pipeline.
- The try-out and model catalog cards provide an easy way to spin up a new project or add to an existing project.

<br>
<img style="height: 400; box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);" src="https://learn.microsoft.com/en-us/azure/ai-studio/media/explore/ai-studio-tab-explore.png">
</br>

### Build

The Build experience within Azure AI Studio empowers AI developers and machine learning professionals to construct and tailor AI solutions and models. Developers have the flexibility to seamlessly switch between the visual studio environment and code-based development, ensuring efficient and effective AI development workflows.

- Simplified development of large language model (LLM) solutions and copilots with end-to-end app templates and prompt samples for common use cases.
- Orchestration framework to handle the complex mapping of functions and code between LLMs, tools, custom code, prompts, data, search indexes, and more.
- Evaluate, deploy, and continuously monitor your AI application and app performance.

<br>
<img style="height: 400; box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);" src="https://learn.microsoft.com/en-us/azure/ai-studio/media/explore/ai-studio-tab-build.png">
</br>

### Manage

Developers have the capability to manage settings related to connections and compute within Azure AI Studio. On the other hand, administrators primarily utilize this section to oversee access control, monitor usage, and handle billing aspects. It’s a division of responsibilities that ensures efficient management of the platform.

- Centralized backend infrastructure to reduce complexity for developers.
- A single Azure AI hub resource for enterprise configuration, unified data story, and built-in governance.

<br>
<img style="height: 400; box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);" src="https://learn.microsoft.com/en-us/azure/ai-studio/media/explore/ai-studio-tab-manage.png">

</br>

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Self Guided Activity: Review Azure AI Studio deep dive demo video</b></p>

Review Azure AI Studio deep dive demo video
 <p><a href="https://learn.microsoft.com/en-us/azure/ai-studio/what-is-ai-studio?tabs=manage#azure-ai-studio-enterprise-chat-solution-demo"><img src="https://img.youtube.com/vi/Qes7p5w8Tz8/1.jpg" height = 200></a> 


<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Description</b></p>

Azure AI Studio ushers in a new era of generative AI development. It empowers developers to explore, build, test, and deploy their AI innovations at scale – moving faster from idea to impact. Whether creating custom copilots, enhancing search, improving call centers, developing bots and bespoke applications, or a combination of these, Azure AI Studio provides the necessary support. The unified platform is tailor-made for AI developers to integrate pre-built services and models, prompt orchestration and evaluation, content safety, and responsible AI tools for privacy, security, and compliance, helping developers navigate the complexities of generative AI with confidence.

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Steps</b></p>

Time permitting review end to end demo of Azure AI Studio deep dive. 

<p style="border-bottom: 1px solid lightgrey;"></p>

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">2.3 - Governance and Administration</h2>
<br></br>

Azure AI Studio provides flexibility, cost transparency, and responsible AI practices while enabling you to build and deploy powerful AI solutions.

### Pricing and Billing 

**Preview Phase**:
   - During the preview phase, there's **no extra charge** for using Azure AI Studio.
   - When deploying solutions, **Azure AI services**, **Azure Machine Learning**, and other Azure resources used within Azure AI Studio will be billed at their existing rates.
   - Keep in mind that pricing is subject to change when Azure AI Studio becomes generally available².

**Cost Estimation and Planning**:
   - **Azure Pricing Calculator**: Before adding any resources to Azure AI Studio, use the Azure pricing calculator to estimate costs. It helps you plan for Azure AI Studio costs.
   - As you add Azure resources, review the estimated costs. Remember that costs for Azure AI services are only a portion of the monthly costs in your Azure bill. You're billed for all Azure services and resources used in your Azure subscription, including third-party services¹.

**Billing Models**:
   - **Pay-as-you-go**: With pay-as-you-go pricing, you're billed according to the Azure AI services offering you use, based on its billing information.
   - **Commitment Tiers**: Commitment tier pricing allows you to commit to using several service features for a fixed fee, ensuring predictable total costs based on your workload needs¹.

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">2.4 - Accesing the studio</h2>
<br></br>

### Limited access to Azure OpenAI Service
As part of Microsoft's commitment to responsible AI, we are designing and releasing Azure OpenAI Service with the intention of protecting the rights of individuals and society and fostering transparent human-computer interaction. For this reason, we currently limit the access and use of Azure OpenAI, including limiting access to the ability to modify content filters and/or abuse monitoring.

Azure OpenAI requires registration and is currently only available to approved enterprise customers and partners.

### Registering
You can explore Azure AI Studio without signing in, but for full functionality an Azure account is needed and apply for access to Azure OpenAI Service by completing the form at https://aka.ms/oai/access. You receive a follow-up email when your subscription has been added.

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: Explore Azure AI Studio.</b></p>

For this exercise you will chose the link in the steps below. Follow the instructions 

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Steps</b></p>

- If you have an Azure subscription with access to the Azure OpenAI service, you can explore Azure AI Studio for yourself.
- https://learn.microsoft.com/en-us/training/modules/introduction-to-azure-ai-studio/5-exercise-explore-ai-studio

<p style="border-bottom: 1px solid lightgrey;"></p>

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/owl.png"><b>For Further Study</b></p>
<ul>
    <li><a href="https://www.youtube.com/watch?v=Qes7p5w8Tz8&ab_channel=MicrosoftAzure/">Azure AI Studio deep dive demo</a></li>
    <li><a href="https://learn.microsoft.com/en-us/azure/ai-studio/faq/">Azure AI frequently asked questions - Azure AI Studio</a></li>
</ul>

Congratulations! You have completed this Module.<a href="https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/03%20-%20Coding%20Fundamentals%20with%20Azure%20OpenAI.md"> Click this link to continue to the next Module in the Workshop</a>.

