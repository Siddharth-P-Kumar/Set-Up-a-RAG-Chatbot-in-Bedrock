<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up a RAG Chatbot in Bedrock

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-rag-bedrock)

**Author:** siddharthpk nextwork  
**Email:** siddharthpknextwork@gmail.com

---

## Set Up a RAG Chatbot in Bedrock

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/ai-rag-bedrock_d5e8f1g2)

---

## Introducing Today's Project!

RAG (Retrieval Augmented Generation) is an AI technique that allows an AI model to be trained on my own documents, making it an expert on my specific information. In this project, I will demonstrate RAG by building an AI chatbot that can answer questions based on my personal documents using Amazon Bedrock.

### Tools and concepts

Services I used were Amazon Bedrock, Amazon S3, and Amazon OpenSearch Serverless. Key concepts I learnt include Retrieval Augmented Generation (RAG), setting up a Knowledge Base, using different AI models like Titan Text Embeddings V2 and Llama 3.3 70B Instruct, understanding embeddings and vector stores, and how to manage source chunks and custom prompts to improve chatbot responses.

### Project reflection

This project took me approximately 2 hours. The most challenging part was understanding why syncing S3 to the Knowledge Base was necessary after initial S3 bucket connection. It was most rewarding to observe improved chatbot responses after adjusting RAG source chunks and the generation prompt.

I chose to do this project today because I am keenly interested in advanced AI topics, particularly Retrieval Augmented Generation (RAG), and this project offered a hands-on way to build a functional RAG chatbot using Amazon Bedrock. Something that would make learning with NextWork even better is more interactive elements or advanced troubleshooting guides within the project steps.

---

## Understanding Amazon Bedrock

Amazon Bedrock is like an AI model marketplace where I can search for and use different models from top companies in one place. I'm using Bedrock in this project to train AI models on my own information, which is called RAG, to create a custom chatbot that responds based on my specific data.

My Knowledge Base is connected to S3 because Amazon S3 is where I store all the documents and information that my chatbot will learn from. S3 is a highly scalable and secure object storage service provided by AWS, perfect for holding the training materials for my chatbot.

In an S3 bucket, I uploaded the documents that my chatbot will learn from. My S3 bucket is in the same region as my Knowledge Base because Amazon Bedrock features, including the AI models and API capabilities, are region-specific. Keeping both in the same region ensures compatibility and optimal performance, as some advanced AI models might only be available in specific data centers, like Ohio (us-east-2).

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/ai-rag-bedrock_b5c8d1e2)

---

## My Knowledge Base Setup

My Knowledge Base uses a vector store, which means it stores the numerical representations (embeddings) of my documents. This allows the AI to understand the meaning of the text, not just the words themselves. When I query my Knowledge Base, OpenSearch will retrieve the most relevant chunks of text by matching the pattern of my question with similar patterns in my stored documents.

Embeddings convert my documents into numerical patterns that capture their meaning, allowing computers to understand them. I'm using Titan Text Embeddings v2 because it's Amazon's model, offering speed, accuracy, and good integration with other AWS services for my Knowledge Base.

Chunking breaks a large text into smaller, manageable paragraphs. This helps your chatbot process information efficiently because AI models have a limit on the amount of text they can handle at once. By default, your documents will be chunked into 300 tokens, which is like 300 words or punctuation marks.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/ai-rag-bedrock_p9r2s5t8)

---

## AI Models

AI models are the brains of my chatbot, transforming raw text from my Knowledge Base into human-like responses. Without them, my chatbot would only output unrefined chunks of text from my documents, making it difficult to understand.

To get access to AI models in Bedrock, I had to navigate to the Model Catalog and explicitly select Titan Text Embeddings V2, Llama 3.1 8B Instruct, and Llama 3.3 70B Instruct. AWS needs explicit access because some models are expensive, they need to ensure capacity, and some have specific rules and conditions.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/ai-rag-bedrock_model-access-proof)

---

## Syncing the Knowledge Base

Even though I connected my S3 bucket when creating the Knowledge Base, I still need to sync because connecting only sets up the infrastructure. The data hasn't actually moved from S3 into my Knowledge Base yet. Syncing ingests, processes (chunks and embeds), and stores my data.

The sync process involves three steps:
Ingesting - Bedrock will retrieve the data from the data source (S3).
Processing - Bedrock will chunk (split into smaller pieces) and embed (convert into numbers) the data.
Storing - Bedrock will store the processed data in the vector store (OpenSearch Serverless).

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/ai-rag-bedrock_sync-screenshot)

---

## Testing My Chatbot

To test my chatbot, the first message I sent was Hello. I used the AI model Llama 3.3 70B Instruct.

When I asked about topics unrelated to my data, my chatbot either stated it couldn't answer or provided a generic response not based on my specific documents. This proves that my chatbot is effectively using its Knowledge Base for relevant queries and avoids generating information when the data isn't available.

You can change the response generation setting to a more capable AI model like Llama 3.3 70B Instruct. When I tested this, my chatbot responded with a proper greeting, demonstrating its improved ability to handle conversational norms.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/ai-rag-bedrock_d5e8f1g2)

---

## Upgrading My Chatbot

In a project extension, I looked into increasing the number of source chunks, which are the individual pieces of information retrieved from the Knowledge Base to answer a query. This will improve my chatbot's responses by providing it with more detailed and contextual information to draw from, leading to more comprehensive and accurate answers.

I also added a custom prompt that tells my chatbot to focus on providing more detailed and contextual answers based on the retrieved information.

After adjusting the source chunks and the generation prompt, my chatbot's response became more detailed and contextual, providing more comprehensive answers based on the expanded information it could access and the specific instructions from the custom prompt.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/ai-rag-bedrock_improved-response)

---

---
