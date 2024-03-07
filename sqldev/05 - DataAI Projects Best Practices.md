![](graphics/microsoftlogo.png)

# Workshop: Unlocking AI Potential for the Data Professional with Azure OpenAI

#### <i>A Microsoft Course from Microsoft Engineering and the FastTrack Team</i>

<p style="border-bottom: 1px solid lightgrey;"></p>

<img style="float: left; margin: 0px 15px 15px 0px;" src="https://raw.githubusercontent.com/microsoft/sqlworkshops/master/graphics/textbubble.png"> <h2>Module 05 - Data/AI Projects Best Practices</h2>

Welcome to this Microsoft solutions workshop on *Unlocking AI Potential for the Data Professional with Azure OpenAI*. In this workshop, you'll learn how to unleash the full potential of artificial intelligence. Whether you’re a seasoned Data Professional or just dipping your toes into the world of machine learning, this course will empower you with the knowledge to create groundbreaking solutions.

In each module you'll get more references, which you should follow up on to learn more. Also watch for links within the text - click on each one to explore that topic.

(<a href="https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/00%20-%20Pre-Requisites.md" target="_blank">Make sure you check out the <b>Pre-Requisites</b> page before you start</a>. You'll need all of the items loaded there before you can proceed with the workshop.)

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/education1.png">Topics In This Module</h2>

The following topics are covered in this module:

<dl>

  <dt><a href="#5.1" target="_blank">5.1 - Security for Generative AI (GenAI) Applications</a><dt>
  <dt><a href="#5.2" target="_blank">5.2 - Responsible AI</a><dt>
  <dt><a href="#5.3" target="_blank">5.3 - A Process for Implementing AI</a><dt>

</dl>

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">5.1 Security for Generative AI (GenAI) Applications</h2>

It's important to recall that the foundation of AI security is proper IT platform security. Regardless of the actions you take for your environment, every access point is important. For Microsoft OpenAI, you should start with a sound understanding of the general security setup for Microsoft Azure: 

<br>
<img src="../graphics/Module05-01.png">
<br>

As LLMs become more easily available and integrated into our work and personal lives, the promise of the technology is tempered by the potential for it to be misused. And the potential for misuse becomes even more significant when you realize LLMs can be combined with other powerful software components and agents to orchestrate a pipeline of actions. OR combined with proprietary and personal data to introduce new avenues for data disclosure and leakage. Following the Microsoft Azure security, these additional controls are shown in this architecture diagram:  

<br>
<img src="../graphics/Module05-02.png">
<br>

The intention for this Module is not to reiterate security guidance that is generally available for more traditional or cloud software applications but to focus on guidance specific to *GenAI* applications and the unique characteristics and challenges of LLMs.  

## Threats & Risks
The security threats and risks with traditional software applications are familiar and understood. *GenAI* and LLMs introduce new and unique security risks including:  
* **AI responses are based on statistical probabilities** or the best chance for correct output. LLMs generate convincing human-like responses by predicting what words come next in a phrase. While they can be great at helping with tasks like summarizing a document or explaining complicated concepts or boosting creativity, there can be issues like responses being inaccurate, incomplete, inappropriate, or completely fabricated. You may be familiar with one well known example where ChatGPT provided non-existent legal citations that lawyers presented in court: [Here's what happens when your lawyer uses ChatGPT](https://www.nytimes.com/2023/05/27/nyregion/avianca-airline-lawsuit-chatgpt.html).
* *GenAI* is **by design a non-deterministic technology** which means that given identical inputs, responses and output may differ.  
* *GenAI* applications **can be extended with agents, plugins, and even external APIs that can significantly expand the attack surface** for a *GenAI* application. For instance, an LLM may implicitly trust a plugin or 3rd party component that is malicious.  
* Another challenge with GenAI is that it **currently it is not possible to enforce an isolation boundary between the data and the control planes**. This means that LLMs are not always able to differentiate between data being submitted as content or an adversarial instruction submitted as content. Think about a SQL databases: instructions are supplied through query language and validated with a parser before data is queried, manipulated, or provided as output.  With a SQL injection attack, a malicious instruction can piggyback on an ambiguously phrased language construct but it can be mitigated with a parameterized query. *GenAI*/LLMs do not have that boundary between syntax (control plane) and data so other mechanisms are needed.  

The diagram below is from [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-2023-v1_1.pdf) and depicts the potential security risks for a hypothetical LLM app:  

![GenAI Security](../../media/images/OWASP-Security-Risks-LLM-Apps.png) 

## Security Strategies  
Infrastructure plays an indispensable role in helping create a secure landscape for *GenAI* applications, particularly cloud environments. Below are strategies tht can help ensure the security of a *GenAI* environment:    
* **Threat Modeling** Include *GenAI* apps in your threat modeling practice. Understand that *GenAI* can extend attack surface with access to underlying or referenced data sources, access to model API keys, workflow orchestration, and agents and plugins. Learn more about what can go wrong with [The AI Attack Surface Map v1.0](https://danielmiessler.com/p/the-ai-attack-surface-map-v1-0/).
* **Architecture strategies** help ensure  a secure, scalable, and available environment. 
  * [Baseline OpenAI end-to-end chat reference architecture](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/architecture/baseline-openai-e2e-chat): a baseline architecture for building and deploying enterprise chat apps that use Azure OpenAI.
  * [OpenAI end-to-end baseline reference implementation](https://github.com/azure-Samples/openai-end-to-end-baseline): Author and run a chat app in a single region with Azure ML and OpenAI. 
* **Network strategies** help ensure that the cloud infrastructure is properly segmented and that access is controlled and monitored.  Consider network segmentation, using secure protocols, enforcing Secure APIs and endpoints.  For GenAI specific recommendations see: [Cognitive Services Landing Zone in-a-box](https://github.com/Azure/AI-in-a-Box/blob/main/ai-services/ai-landing-zone/README.md)
* **Access and Identity strategies** to enforce user verification and provide a barrier to malicious access. When possible, use managed identities and RBAC to authenticate and authorize access and avoid use of *GenAI* service API keys for access. Another consideration to keep in mind is that access patterns like role or row level access to indexes may not be natively supported. See:  
  * [Authentication & Authorization in GenAI Apps with Entra ID & Search](https://techcommunity.microsoft.com/t5/fasttrack-for-azure/authentication-and-authorization-in-generative-ai-applications/ba-p/4022277)
  * [Azure AI Search - Restricting access to indexes](https://learn.microsoft.com/en-us/azure/search/search-security-overview#restricting-access-to-documents)
* **Application strategies** help ensure the application is configured securely and vulnerabilities are identified and addressed:
    * Use App front end services to manage access and throughput. See: [Azure OpenAI Service Load Balancing with Azure API Management](https://learn.microsoft.com/en-us/samples/azure-samples/azure-openai-apim-load-balancing/azure-openai-service-load-balancing-with-azure-api-management/) and [Smart load balancing for OpenAI endpoints and Azure API Management](https://techcommunity.microsoft.com/t5/fasttrack-for-azure/smart-load-balancing-for-openai-endpoints-and-azure-api/ba-p/3991616)
    * Ensure related services are deployed securely (AI Search, Cosmos DB, etc)
    * Secure and validate training data and ingestion pipelines  
* **Governance strategies** help ensure the infrastructure is being used is meeting security and compliance requirements and that policies and procedures are in place to manage risk and accountability: 
  * Become familiar with Responsible AI principles and frameworks and integrate them early in the development of your application.  More here: [Responsible AI](./responsible-ai)
  * Leverage platform capabilities for logging, auditing, and monitoring *GenAI* apps.  See: [Implement logging and monitoring for Azure OpenAI models](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/openai/architecture/log-monitor-azure-openai). 
  
## Adversarial Prompting

#### Attacks
An adversarial prompt attack is when a prompt is used to manipulate an LLM in order to generate a malicious or unintended response. A sneaky user can tamper with words or sentence structure to exploit nuances or sentiment in language models. You may be familiar with some types of prompt attacks:   
* [Prompt injection](https://www.promptingguide.ai/risks/adversarial#prompt-injection): prompt input, output, or instructions are manipulated to lead to unintended behavior.  
* [Prompt leaking](https://www.promptingguide.ai/risks/adversarial#prompt-leaking): is intended to cause the model to leak confidential or proprietary information.   
* [Jailbreaking](https://www.promptingguide.ai/risks/adversarial#jailbreaking): is a technique to bypass model safety mechanisms to generate illegal or unethical content. 
* [DAN](https://www.promptingguide.ai/risks/adversarial#dan): is an acronym for **D**o **A**nything **N**ow and is another technique intended to circumvent model safety guardrails and force it to comply with requests that generate unfiltered responses.
* [Multi-prompt](https://www.lakera.ai/blog/guide-to-prompt-injection): a series of prompts are used to extract private or sensitive information.
* Multi-language: although LLMs are trained in multiple languages, performance is superior for English. This technique involves submitting a request in languages other than English to cause the model to overlook or bypass security checks.
* Obfuscation (token smuggling): a technique to present data in an unexpected format to avoid detection.  

*Note*: Details about these and other adversarial techniques can be found here:    
* [Prompt Engineering Guide](https://www.promptingguide.ai/)
* [The EL15 Guide to Prompt Injection: Techniques, Prevention Methods & Tools](https://www.lakera.ai/blog/guide-to-prompt-injection)

#### Mitigations
As a mitigation strategy for adversarial prompt attacks, consider advanced [prompt engineering techniques](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/advanced-prompt-engineering). There is a growing list of specific techniques that can be used that include enriching prompts with specific instructions, formatting, and providing examples of the kind of output content that is intended.  Below are some techniques to consider:  
  * **Defensive Instructions**: Guide model response with explicit instructions. Structure the [system message](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/advanced-prompt-engineering?pivots=programming-language-chat-completions#system-message) with context and instructions. See also: [Add defense in the instruction](https://github.com/dair-ai/Prompt-Engineering-Guide/blob/main/guides/prompts-adversarial.md#add-defense-in-the-instruction).
  * **Determine intent**: Use techniques like [few-shot learning](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/advanced-prompt-engineering?pivots=programming-language-chat-completions#few-shot-learning) to provide content to the model and help set intent. 
  * **Monitor for degradation in output quality**: a decline in output quality can be an indication that a prompt has been tampered with. Monitor the model for output quality using metrics to measure and evaluate the prompt or human-in-the-loop to evaluate feedback or adversarial test cases to confirm prompt resilience. [Azure Machine Learning prompt flow](https://learn.microsoft.com/en-us/azure/machine-learning/prompt-flow/overview-what-is-prompt-flow?view=azureml-api-2) has built-in evaluation flows that enable users to assess the quality and effectiveness of prompts. 
  
  * **Use other models or dedicated services to process requests**. [Azure AI Content Safety](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/) is an azure service that provides [content filtering](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/content-filter?tabs=warning%2Cpython). AI models are used to detect and classify categories of harm from AI-generated content.  Content filters are more contextually aware than blocklists and can provide broad coverage without the manual creation of rules or lists. 
  * **Use inbound/outbound block/allow lists or filters or rules**. When there is a need to screen for items specific to a use case, blocklists can be helpful and can be implemented as part of the AI Content Safety service. See: [Use a blocklist in Azure OpenAI](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/use-blocklists).
  * Use the native power of models to **steer zero- or few-shot prompting** strategies. See [promptbase](https://github.com/microsoft/promptbase) for a growing collection of resources, best practices, and sample scripts.  

See [Exploring Adversarial Prompting and Mitigations in AI-Infused Applications](https://www.linkedin.com/pulse/exploring-adversarial-prompting-mitigations-alex-morales-3sqne/) for more specifics on these types of attacks and defense tactics. 
  
You can see more about privacy and compliance in the Microsoft Azure OpenAI service here: 

<br>
<img src="../graphics/Module05-03.png">
<br>

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: TODO: Activity Name</b></p>

TODO: Activity Description and tasks

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Steps</b></p>

- [Open this Jupyter Notebook](https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/notebooks/Notebook%20-%20Module%205.ipynb) and review the results from the instructions and code. You can download the Notebook and enter your own credentials and other variables to run it on your system once you have [completed the pre-requisites](https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/00%20-%20Pre-Requisites.md).

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">4.2 Responsible AI</h2>

# Guidance: Responsible AI (RAI)
![Responsible AI (RAI)](../../media/images/banner-rai.png)

## Introduction
There is a lot to be excited about with recent advances in AI and LLM technology, but every day there are examples in the media about where and how it has gone wrong. As AI is integrated into more of our daily work and personal lives it can cause minor inconveniences, such as mistakenly canceled appointments, to more serious issues, such as potential job displacement and privacy compromises — and may even compound already existing social or economic inequities. All of us who design, develop, and deploy AI have a responsibility to confront the risks that the technology introduces.

**If your team makes use of AI APIs or AI systems or designs, develops, or deploys AI, please consider joining us in the commitment to innovate responsibly.**  This page contains recommendations and guidance for how to get started.  

## Get Started
RAI sounds promising.  Who wouldn't want their product to be responsible or trustworthy?  But there can be challenges:
* AI systems are complex and require a diversity of teams, skills, and tools
* Potential harms and risks of AI systems are different from those of traditional software systems
* Leadership support is crucial for a sustainable RAI practice
  
The recommendations that follow are based on lessons learned from rolling out a responsible AI practice across one of the organizations within Microsoft. As you review the recommendations, keep in mind they should be *adapted to fit your organization, circumstances, and product plans*. 

The approach used was grounded in principles, standards, practices that were used internally and are published here:   
* **[Microsoft AI principles](https://www.microsoft.com/en-us/ai/principles-and-approach)** of fairness, reliability and safety, privacy and security, Inclusiveness, Transparency, and Accountability. However your organization defines and prioritizes the principles, they become the foundation for RAI standards and practices. 
* **[Microsoft Responsible AI Standard, v2](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE5cmFl)**: The RAI standard is the first step in putting the principles into practice.  It answers the question... *How are we going to execute on a responsible AI practice...?*. For each principle, the standard sets out concrete steps and outcomes. 
* **[Microsoft Responsible AI Impact Assessment Template](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE5cmFk)** and **[Impact Assessment Guide](https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Guide.pdf)** provides documentation and guidance for how a team can capture and document the benefits, potential harms and mitigations for an AI system.  
* **RAI tools and guidance** such as the Responsible AI Maturity Model, HAX Toolkit, RAI Toolbox, and more (link [here](https://aka.ms/rai)).
  
## Complete an impact assessment
A *Responsible AI impact assessment* is the process a product team follows to identify and assess the potential risks and harms of an AI system.  It is a new process, and some organizations may be reluctant to consider it, giving reasons such as:
* *It is still too early in AI lifecycle to do impact assessments. RAI is mostly academic*.
* *AI is so new. How can we expect product teams to know about potential risks and harms?*
* *Discussions around RAI will only devolve into messy disagreements and take time away from design/development/deployment timelines.*

An RAI impact assessment is the primary method for guiding a team through the process of examining an AI system and aligning it to responsible AI principles and standards. The questions it examines include: *What are the use cases for the AI system? Who are the stakeholders? How do we monitor and measure AI? Who might be harmed and how? How do we prevent these harms?*

The purpose of a good RAI impact assessment is to identify the potential risks and harms of an AI system and introduce mitigations to reduce negative consequences. The templates and guidance introduced above can help a team put responsible AI principles to work.  Consider adjustments to better align with your organizational requirements and product team processes. 

Plan to update an impact assessment on an ongoing basis as use cases change, new functionality or technology is introduced, or even as the statistical property of the training data changes over time (data drift).  

## Strategies to help
The pace of AI is moving quickly and a variety of methods are needed to help measure and advance the responsible design, development, and deployment of AI systems. 

#### Adopt a layered mitigation approach for RAI
  At Microsoft, we recommend a layered mitigation approach that combines technical, operational, and governance measures to reduce the potential harms of LLMs. A layered approach applies different measures at different stages of development and deployment as documented in the article [Deploy large language models responsibly with Azure AI](https://techcommunity.microsoft.com/t5/ai-machine-learning-blog/deploy-large-language-models-responsibly-with-azure-ai/ba-p/3876792) and depicted below:
![Responsible AI (RAI)](../../media/images/Rai-mitigation-layers.png)
See [Harms mitigation strategies with Azure AI](https://learn.microsoft.com/en-us/azure/ai-studio/concepts/evaluation-improvement-strategies) for a walk-through of the mitigation layers.  
 
#### Get started with RAI metrics 
  Measuring RAI involves both *technical attributes*, like accuracy and security, and *socio-technical attributes* such as fairness, representational harms, or safety and reliability. A starter set of metrics could include platform, usage, and operational level metrics like:
    * *resource consumption* (GPU, CPU, memory utilization, response times), 
    * *response/request tracking* (number of unique/active users, requests, prompts, token usage), and
    * *operational metrics* (quota, capacity, latency, throttling). See [Monitoring Azure OpenAI Service](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/monitoring).

  Add to this a layer of metrics to measure the potential for RAI harms identified through the impact assessment process. Consider measuring the number of input prompts blocked, number of responses blocked, number of jailbreak attempts, or metrics related to quality of generated output such as groundedness, relevance, and similarity. 

  #### Tools to support RAI
  Tools can be a particular challenge because the RAI tools landscape is relatively new and rapidly evolving. While there are libraries and building blocks, the overall landscape can seem fragmented, making it difficult to establish an end-to-end workflow. Some of the challenges include: 
* There is no single tool that can holistically assess potential AI harms.
* Tools often do not map directly to an RAI principle or standard, such as *fairness* or *transparency*, making it difficult to determine an appropriate tool.  
* Components and libraries built to support distinct aspects of RAI practice often require additional effort to use them in a complementary way.
  
Tools to support an RAI practice for *GenAI* applications focus on model selection, prompt engineering, and model output. Recommendations include:
  *  **[Azure AI Content Safety](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/)**: An azure service that provides [content filtering](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/content-filter?tabs=warning%2Cpython). AI models are used to detect and classify categories of harm from AI-generated content.  Content filters are more contextually aware than blocklists and can provide broad coverage without the manual creation of rules or lists. 
  *  **Blocklists**: When there is a need to screen for items specific to a use case, blocklists can be helpful and can be implemented as part of the AI Content Safety service. See: [Use a blocklist in Azure OpenAI](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/use-blocklists).
  *  **Meta-prompt best practices**: To mitigate harms, apply recommended prompt engineering practices. See: [Introduction to prompt engineering](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/prompt-engineering) and [Prompt engineering techniques](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/advanced-prompt-engineering).
  *  **Prompt template recommendations**: Example templates to help write effective system messages to guide AI system behavior: See [System message framework and template recommendations for Large Language Models (LLMs)](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/system-message?source=recommendations).
  *  **Prompt flow**: [Azure Machine Learning prompt flow](https://learn.microsoft.com/en-us/azure/machine-learning/prompt-flow/overview-what-is-prompt-flow?view=azureml-api-2) is a development tool designed to streamline the entire development cycle of AI applications.  Specific to RAI are the built-in evaluation flows that enable users to assess the quality and effectiveness of prompts. 
  
 ## Resources & References
Here are additional RAI resources: 
* [Microsoft AI principles](https://www.microsoft.com/en-us/ai/principles-and-approach) 
* [Microsoft Responsible AI Standard, v2](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE5cmFl) 
* [Microsoft Responsible AI Impact Assessment Template](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE5cmFk)
* [Responsible AI tools and guidance](https://aka.ms/rai) and [HAX Toolkit](https://www.microsoft.com/en-us/haxtoolkit/)
* Video: [An introduction to responsible AI (RAI) process](https://learn.microsoft.com/en-us/shows/learn-live/fasttrack-for-azure-season-3-ep07-an-introduction-to-responsible-ai-rai-process)
* Medium articles: [Responsible AI in action, Part 1: Get started](https://medium.com/data-science-at-microsoft/responsible-ai-in-action-part-1-get-started-ee50bebbdff3?source=friends_link&sk=3a9ad40230116d9fc4c66fdf7ab56de2), and [Responsible AI in action, Part 2: Complete an impact assessment](https://medium.com/data-science-at-microsoft/responsible-ai-in-action-part-2-complete-an-impact-assessment-9b792409e8db?source=friends_link&sk=6e68eb938a2be1d776748cc55a89b663) and [Responsible AI in action, Part 3: Tools to help](https://medium.com/data-science-at-microsoft/responsible-ai-in-action-part-3-tools-to-help-969e45cac11b?source=friends_link&sk=69bfea1ae66e2b7272d58e28a49cafe4)
 


<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: TODO: Activity Name</b></p>

TODO: Activity Description and tasks

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Description</b></p>

TODO: Enter activity description with checkbox

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Steps</b></p>

TODO: Enter activity steps description with checkbox

<p style="border-bottom: 1px solid lightgrey;"></p>

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/owl.png"><b>For Further Study</b></p>
<ul>
    <li><a href="url" target="_blank">TODO: Enter courses, books, posts, whatever the student needs to extend their study</a></li>
</ul>

    ## Resources & References
* [OWASP Top 10 for LLM applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/) and the [downloadable whitepaper](https://www.llmtop10.com/assets/downloads/OWASP-Top-10-for-LLM-Applications-v1_1.pdf)
* [OWASP LLM AI Security & Governance Checklist](https://owasp.org/www-project-top-10-for-large-language-model-applications/llm-top-10-governance-doc/LLM_AI_Security_and_Governance_Checklist.pdf)
* [Security Best Practices for GenAI Applications in Azure](https://techcommunity.microsoft.com/t5/azure-architecture-blog/security-best-practices-for-genai-applications-openai-in-azure/ba-p/4027885)
* [Steering at the Frontier: Extending the Power of Prompting](https://www.microsoft.com/en-us/research/blog/steering-at-the-frontier-extending-the-power-of-prompting/)
* [Planning red teaming for large language models (LLMs) and their applications](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/red-teaming)


Congratulations! You have completed this Workshop.You can now extrapolate what you have learned to your development environments.</a>.
