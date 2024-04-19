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

### How are Tokens Used?
Given an input prompt, the natural language models generate completions one token at a time. However, the generated token is not deterministic. At each step, the model outputs a list of all possible tokens with associated weights. The API samples one token from this list, with heavily-weighted tokens more likely to be selected than the others.

<p align="center">
  <img src="../graphics/llmtokensusage.png">
</p>

It then adds that token to the prompt and repeats the process until the "max token count" limit (context window) is met for the completion - or until the model generates a special "stop token", which halts further token generation. (This blog post by Beatriz Stollnitz explains the process in detail.)

This is how the model generates completions of one or more words, and why those completions can change from invocation to invocation.

### Why Does it Matter?

To understand why tokenization matters, we need to think about two aspects of deployed models: *token limits* and *token pricing*.

**Token Limits.** Every model has a context window defined as the maximum number of tokens it can process for a single request. For instance, older gpt-3.5-turbo models have a 4K token limit (context) for each request. The token limit is shared between prompt and completion. Because the completion gets added to the prompt in order to generate the next token, it becomes necessary to fit both within the total context window for a single request.

**Token Pricing.** Like with any API, model deployment usage incurs costs based on the model type and version. Currently, model pricing is tied to number of tokens used, with different price points possible for each model type or version.

One limitation to keep in mind is that for a text generation model the prompt and the generated output combined must be no more than the model's maximum context length. For embeddings models (which do not output tokens), the input must be shorter than the model's maximum context length. The maximum context lengths for each text generation and embeddings model can be found in the model index.

The table below shows the context window (max tokens) and the model pricing (billed in 1K increments) for Azure OpenAI Models.

<p align="center">
  <img src="../graphics/aoia-pricing-tokens.png">
</p>

Note how newer models like gpt-4-32k have much larger token limits: up to 32,768 tokens. This not only allows for longer completions but also much larger prompts. This is particularly useful for prompt engineering, as we'll see later.

Keep in mind that usage cost is correspondingly higher. Prompt engineering techniques can also help improve cost efficiency by crafting prompts that minimize token usage costs without sacrificing quality of responses.

### OpenAI Tokenizer Tool

Want to get a better sense of how tokenization works on real text? Use [OpenAI Tokenizer](https://platform.openai.com/tokenizer) - a free online tool that visualizes the tokenization and displays the total token count for the given text data.

https://platform.openai.com/tokenizer

[Learn More:](https://help.openai.com/articles/4936856-what-are-tokens-and-how-to-count-them)

### Try The Example
Visit the site and click "show example" to see it in action as shown below. Each color-coded segment represents a single token, with the total token count displayed below (57 tokens).

Note how "1234567890" and "underlying" have the same string lengths - but the former counts for 4 tokens while the latter counts for 

1. Also observe how punctuation (":",".") take up 1 token each, cutting into prompt token limits.

<p align="center">
  <img src="../graphics/tokenizer-example.png">
</p>

### Try The Exercises

> [! YOUR TURN]  
> Visit https://platform.openai.com/tokenizer. Clear the tool before each exercise. Enter the exercise text into the Tokenizer and observe the output - it should update interactively.

**Exercise 1:** As a common word, "apple" requires only one token.

    apple

**Exercise 2:** The word "blueberries" requires two tokens: "blue" and "berries".

    blueberries

**Exercise 3:** Proper names generally require multiple tokens (unless common)

    Skarsgård

It's this token representation that allows AI models to generate words that are not in any dictionary, but without having to generate text on a letter-by-letter basis (which could easily result in gibberish).

Build your intuition by trying out other words or phrases.

<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: TODO: Run the Tokenization Section of the Notebook</b></p>

TODO: Activity Description and tasks

<p style="border-bottom: 1px solid lightgrey;"></p><br>

<!-- Prompts & Completions -->
<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">3.4 TODO: Prompts & Completions</h2>

<br>

  * What is a Prompt?
  * Prompt Engineering

### Prompt components

While it is considered a new field, rich literature is already available, including articles, blogs, research papers, repos, etc., about prompt engineering techniques.

A common technique is to construct prompts from a well-defined set of components, as shown in the following diagram.

<p align="center">
  <img src="../graphics/prompt_comp.png">
</p>

### Instructions and other static context
Static context description refers to providing fixed information to the LLM. This information can include content and format instructions, database schema information, or any other contextual information that is relevant to the task. Here are some widely-used approaches that demonstrate using static context examples in prompt engineering:

### Establish conversational or functional style with a system message
A system message can be used to inform the LLM about the context. The context may be the type of conversation it is engaging in, or the function it is supposed to perform. It helps the LLM generate more appropriate responses. For example, if the LLM is expected to perform a customer service function, the prompt could include a system message such as:


    You are a friendly AI agent who can provide assistance to the customer regarding their recent order.

Similarly, if the LLM is engaging in a casual conversation, the prompt could include a message such as

    Let's have a friendly chat about your favorite hobbies.

### Use input text to guide completion formatting

By formatting input text in a specific way, we can guide the LLMs towards generating more relevant responses. For example, if the LLM is trained to generate recipe instructions, the input text could be formatted as "First, [action], then [action], and finally [action]." This formatting guides the LLM towards generating instructions in a sequential manner. Similarly, if the LLM is trained to generate summaries of news articles, the input text could be formatted as "The article talks about [topic]. It discusses [point 1], [point 2], and [point 3]." This formatting guides the LLM towards generating a summary that covers the main points of the article. Here we can see the importance of using the correct comment character for the language that you want to generate.

Prompt: /* Create a javascript dictionary with 5 cities and their location */ Completion:

    var cities = {
    'Los Angeles': [34.0522, -118.2437],
    'New York': [40.7128, -74.0059],
    'San Francisco': [37.7749, -122.4194],
    'Chicago': [41.8781, -87.6298],
    'Houston': [29.7604, -95.3698]
    };

### Add supporting information
Adding supporting information to the prompt can provide more context for the LLM, which can improve the accuracy of its responses. For example, if the prompt asks the LLM to generate a response to a specific question, providing additional information can help the LLM generate a more relevant response. A good example of this is:

    Please explain transformer language model to a 15-year-old student.

Similarly, the LLM generates a more accurate and persuasive description when provided with additional information if asked to generate a product description. A good example is:

        Write a witty product description in a conversational style so young adult shoppers understand
        what this product does and how it benefits them.

        Use the following product details to summarize your description:

        Title: {{shopify.title}}
        Type: {{shopify.type}}
        Vendor: {{shopify.vendor}}
        Tags: {{shopify.tags}}



<br>
<p><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/point1.png"><b>Activity: TODO: Run the Prompts & Completions Notebook</b></p>

<p style="border-bottom: 1px solid lightgrey;"></p><br>

<!-- Techniques -->
<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="../graphics/pencil2.png">3.5 TODO: Techniques</h2>


This section discusses prompt engineering techniques that can help LLMs solve certain problems more effectively.

<p align="center">
  <img src="../graphics/in_context.png">
</p>

### Zero-shot learning

LLMs are trained on such large amounts of data they may be be able to perform some tasks with very little prompting. Try the example below and change the sentence to see what outcomes you find.

      Classify the text into neutral, negative or positive.
      Text: My calendar today looks ok
      Sentiment:

### Few-shot learning

If zero-shot learning is failing for your examples and more complex tasks, few shot prompting can provide examples that can better steer the model to the desired outcomes. Examples show the model cleanly how we want it to operate. Try the example below to see the outcome. Can you think of other examples that could leverage few-shot learning?

        Headline: Twins' Correa to use opt-out, test free agency
        Topic: Baseball
        Headline: Qatar World Cup to have zones for sobering up
        Topic: Soccer
        Headline: Yates: Fantasy football intel for Week 6
        Topic: Football
        Headline: Coach confident injury won't derail Warriors
        Topic:

### Chain of thought prompting

In this technique, the LLM is responsible for breaking the task down into smaller steps. The LLM uses its knowledge of the world and its ability to reason. The LLM then generates a chain of thoughts that leads to the solution of the task.

Refresh the Playground page to reset the System Message to its default value, and then enter the user prompt below to see 'Chain of thought prompting' in action:

        Who was the first person to walk on the moon? Take a step-by-step approach in your response, cite sources, and give reasoning before sharing a final answer in the below format: ANSWER is: <name>
        
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
