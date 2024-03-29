![](graphics/microsoftlogo.png)

# Workshop: Unlocking AI Potential for the Data Professional with Azure OpenAI

#### <i>A Microsoft Course from Microsoft Engineering and the FastTrack Team</i>

<p style="border-bottom: 1px solid lightgrey;"></p>

<img style="float: left; margin: 0px 15px 15px 0px;" src="https://raw.githubusercontent.com/microsoft/sqlworkshops/master/graphics/textbubble.png"> <h2>Module 03 - Coding fundamentals with Azure OpenAI</h2>

Welcome to this Microsoft solutions workshop on *Unlocking AI Potential for the Data Professional with Azure OpenAI*. In this workshop, you'll learn how to unleash the full potential of artificial intelligence. Whether you’re a seasoned Data Professional or just dipping your toes into the world of machine learning, this course will empower you with the knowledge to create groundbreaking solutions.

In each module you'll get more references, which you should follow up on to learn more. Also watch for links within the text - click on each one to explore that topic.

(<a href="https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/00%20-%20Pre-Requisites.md" target="_blank">Make sure you check out the <b>Pre-Requisites</b> page before you start</a>. You'll need all of the items loaded there before you can proceed with the workshop.)


<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/education1.png">Topics In This Module</h2>

The following topics are covered in this module:

<dl>

  <dt><a href="#3.1" target="_blank">3.1 - Environment Setup</a><dt>
  <dt><a href="#3.2" target="_blank">3.2 - Basic Chat</a><dt>
  <dt><a href="#3.3" target="_blank">3.3 - Tokens</a><dt>
  <dt><a href="#3.4" target="_blank">3.4 - Prompts & Completions</a><dt>
  <dt><a href="#3.5" target="_blank">3.5 - Techniques</a><dt>
  <dt><a href="#3.6" target="_blank">3.6 - Embeddings & Vector DBs</a><dt>
  <dt><a href="#3.7" target="_blank">3.7 - REST, SDKs & Orchestration</a><dt>

</dl>



<p align="center">
  <img src="../graphics/buildingblocks.png" alt="AOIA Building Blocks">
</p>

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">3.1 TODO: Environment Setup</h2>

TODO: How do you hook into Azure Open AI


<p align="center">
  <img src="../graphics/environmentsetup.png">
</p>

To programmatically interact with OpenAI in Azure, several necessary services need to be deployed within the Azure environment. First, the deployment of Azure OpenAI and Azure Cognitive Search services is essential to run samples effectively. Azure OpenAI provides access to advanced natural language processing capabilities, enabling developers to integrate state-of-the-art AI models into their applications seamlessly. Meanwhile, Azure Cognitive Search allows for the indexing and querying of structured and unstructured data, facilitating efficient search and retrieval of information.

Additionally, it's crucial to store all necessary service endpoints, service API keys, and Azure OpenAI deployment names in a centralized configuration file, such as '../Module03/.env'. This file serves as a centralized repository of authentication credentials and connection details, ensuring consistency and security across all notebooks within the repository. By centralizing these configurations, developers can easily connect and authenticate against the deployed Azure services from any notebook within the repository, streamlining the development and deployment process.

<br>

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: Azure OpenAI Enviornment Setup Action</b></p>

In this section you will review a Jupyter Notebook that uses a Python Kernel to run code illustrating the necessary Azure Services you need to deploy to start interacting and working with a LLM/GPT Model in Azure Open AI. You can also download this Notebook to your local system and modify it for your learning journey.

TODO: Activity Description and tasks

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Steps</b></p>

- [Open this Jupyter Notebook](https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/notebooks/Notebook%20-%20Module%203.ipynb) and review the results from the instructions and code. You can download the Notebook and enter your own credentials and other variables to run it on your system once you have [completed the pre-requisites](https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/00%20-%20Pre-Requisites.md).


<p style="border-bottom: 1px solid lightgrey;"></p><br>

<!-- Basic Chat -->
<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">3.2 TODO: Basic Chat</h2>

TODO: Topic Description

https://platform.openai.com/docs/quickstart?context=python


<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: TODO: Run the Basic Chat Notebook</b></p>

TODO: Activity Description and tasks

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Description</b></p>

TODO: Enter activity description with checkbox

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Steps</b></p>

TODO: Enter activity steps description with checkbox

<p style="border-bottom: 1px solid lightgrey;"></p><br>

<!-- Tokens -->
<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">3.3 TODO: Tokens</h2>

<br>

  * What is a token?
  * Why Does It Matter?
  * Token Limits in Models
  * Token in Throttling

<br>
The OpenAI natural language models don't operate on words or characters as units of text, but instead use something in-between: tokens. By definition tokens are text "chunks" that represent commonly occurring sequences of characters in the large language training dataset.
<br><br>
OpenAI's large language models (sometimes referred to as GPT's) process text using tokens, which are common sequences of characters found in a set of text. The models learn to understand the statistical relationships between these tokens, and excel at producing the next token in a sequence of tokens.
<br><br>

* A token can be a single character, fraction of a word, or an entire word.
* Many common words are represented by a single token.
* Less common words are represented by multiple tokens.

**Tokenization** is now the process by which text data (e.g., "prompt") gets deconstructed into a sequence of tokens. The model can then generate the next token in sequence for text 'completion'. We'll see concrete examples of tokenization later in this lesson.

Text generation and embeddings models process text in chunks called tokens. Tokens represent commonly occurring sequences of characters. For example, the string " tokenization" is decomposed as " token" and "ization", while a short and common word like " the" is represented as a single token. Note that in a sentence, the first token of each word typically starts with a space character. Check out the tokenizer tool to test specific strings and see how they are translated into tokens. As a rough rule of thumb, 1 token is approximately 4 characters or 0.75 words for English text.

https://platform.openai.com/tokenizer

### Why Does it Matter?

To understand why tokenization matters, we need to think about two aspects of deployed models: *token limits* and *token pricing*.

**Token Limits.** Every model has a context window defined as the maximum number of tokens it can process for a single request. For instance, older gpt-3.5-turbo models have a 4K token limit (context) for each request. The token limit is shared between prompt and completion. Because the completion gets added to the prompt in order to generate the next token, it becomes necessary to fit both within the total context window for a single request.

**Token Pricing.** Like with any API, model deployment usage incurs costs based on the model type and version. Currently, model pricing is tied to number of tokens used, with different price points possible for each model type or version.


One limitation to keep in mind is that for a text generation model the prompt and the generated output combined must be no more than the model's maximum context length. For embeddings models (which do not output tokens), the input must be shorter than the model's maximum context length. The maximum context lengths for each text generation and embeddings model can be found in the model index.


<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: TODO: Run the Tokenization Section of the Notebook</b></p>

TODO: Activity Description and tasks

<p style="border-bottom: 1px solid lightgrey;"></p><br>

<!-- Prompts & Completions -->
<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">3.4 TODO: Prompts & Completions</h2>

<br>

  * What is a Prompt?
  * What is a Completion?
  * Prompt Engineering

<br>
<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: TODO: Run the Prompts & Completions Notebook</b></p>

<p style="border-bottom: 1px solid lightgrey;"></p><br>

<!-- Techniques -->
<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">3.5 TODO: Techniques</h2>



<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: TODO: Run the Techniques Notebook</b></p>

<p style="border-bottom: 1px solid lightgrey;"></p><br>

<!-- Embeddings & Vector DBs -->
<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">3.6 TODO: Embeddings & Vector DBs</h2>

<br>
What are embeddings?

OpenAI’s text embeddings measure the relatedness of text strings. Embeddings are commonly used for:

Search (where results are ranked by relevance to a query string)
Clustering (where text strings are grouped by similarity)
Recommendations (where items with related text strings are recommended)
Anomaly detection (where outliers with little relatedness are identified)
Diversity measurement (where similarity distributions are analyzed)
Classification (where text strings are classified by their most similar label)
An embedding is a vector (list) of floating point numbers. The distance between two vectors measures their relatedness. Small distances suggest high relatedness and large distances suggest low relatedness.

https://platform.openai.com/docs/guides/embeddings

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: TODO: Run the Embeddings & Vector DBs Notebook</b></p>


<p style="border-bottom: 1px solid lightgrey;"></p>

<br>

<!-- REST, SDKs & Orchestration -->
<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">3.7 TODO: REST, SDKs & Orchestration</h2>

<br>

## Calling LLM using REST API

Learn how to interact with OpenAI's Large Language Models (LLMs) via REST API. This guide will use the VS Code extension to demonstrate API calls.

## Overview

Azure OpenAI, part of Azure Cognitive Services, offers AI models and tools for building intelligent applications. Its REST API endpoints for LLMs enable integration into various applications for tasks like natural language understanding and speech-to-text.

![Overview](../graphics/01_Overview.png) *Azure OpenAI REST API interaction overview.*

The REST API provides access to cutting-edge features, often available before SDK implementations, allowing developers to leverage the latest LLM capabilities in a flexible manner.

## Prerequisites

Ensure you have the following before starting:

- **VS Code**: The editor where we'll write and execute our API calls.
- **Azure OpenAI Credentials**: Obtain your key and endpoint from the [Azure portal](https://portal.azure.com/).

Store sensitive information like API keys and endpoints in an `.env` file to keep your code secure.

| Folder | Content | Details |
| ------ | ------- | ------- |
| / | [2.A.BasicChat.ipynb](2.A.BasicChat.ipynb) | Polyglot Notebook for a chat application using REST |
| / | [2.B.BasicChat.ipynb](2.B.BasicChat.ipynb) | Notebook for calling models like whisper and ada via REST |

## Making Your First Call

To call the OpenAI endpoint, structure your HTTP requests as follows:

```
<Http Method> https://<aoai endpoint>/deployments/<deployment id>/query?api-version=<version>
```

The body or payload of each call is in JSON format. The following is an example of a call to the OpenAI endpoint:

```
@SubscriptionKey=<api-key>
@EndPoint=<end-point>
@EmbeddingModel=text-embedding-ada-002 #as an example

POST {{EndPoint}}/deployments/{{EmbeddingModel}}/embeddings?api-version=2023-05-15
Content-Type: application/json
api-key: {{SubscriptionKey}}

{
    "input": "This is a test"  
}

```

The response would look like this (the 1536 dimensional vector is truncated):

```
HTTP/1.1 200 OK
Content-Length: 33437
Content-Type: application/json
apim-request-id: afa96e36-c368-482e-98b6-f478381b707d
x-ms-region: East US
x-content-type-options: nosniff
openai-processing-ms: 29.1074
access-control-allow-origin: *
x-request-id: 838e82e7-c9aa-4f00-971a-eb90252ebae1
x-ms-client-request-id: afa96e36-c368-482e-98b6-f478381b707d
Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
Date: Sun, 10 Sep 2023 12:05:40 GMT
Connection: close

{
  "object": "list",
  "data": [
  ],
  "model": "ada",
  "usage": {
    "prompt_tokens": 4,
    "total_tokens": 4
  }
}
```


In this response, you can see information like token usage and processing time. The data section would typically contain the output vector.


<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: TODO: Run the EST, SDKs & Orchestration Notebook</b></p>

TODO: Activity Description and tasks

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Description</b></p>

TODO: Enter activity description with checkbox

<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/checkmark.png"><b>Steps</b></p>

TODO: Enter activity steps description with checkbox

<p style="border-bottom: 1px solid lightgrey;"></p><br>



<p><img style="margin: 0px 15px 15px 0px;" src="../graphics/owl.png"><b>For Further Study</b></p>
<ul>
    <li><a href="url" target="_blank">TODO: Enter courses, books, posts, whatever the student needs to extend their study</a></li>
</ul>

Congratulations! You have completed this Module.<a href="https://github.com/sqlserverworkshops/OpenAI-DataPro/blob/main/sqldev/04%20-%20Data%20Integrations%20with%20the%20Azure%20OpenAI%20Service.md"> Click this link to continue to the next Module in the Workshop</a>.
