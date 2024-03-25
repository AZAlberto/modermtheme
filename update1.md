---
layout: default
title: Project Progress Updates I
description: This is the pages contain information about the project update 1
---

# Project Progress Updates I
[Back to the Home Page](./index)

## Update Overview

During this update phase, we've achieved the following milestones:

### 1. Technology Stack Familiarization
We've gained proficiency in our selected technology stack, including PyTorch, Hugging Face, Langchain,  ChromaDB, and the Large Language Model(LLM)-ChatGLM, through curated tutorials/documents:
- [PyTorch 60-Minute Blitz](https://pytorch.org/tutorials/beginner/deep_learning_60min_blitz.html)
- [Hugging Face NLP Course](https://huggingface.co/learn/nlp-course/chapter1/1)
- [Langchain QA Usage](https://python.langchain.com/docs/use_cases/question_answering/)
- [ChromaDB Usage](https://docs.trychroma.com/getting-started)
- [ChatGLM Usage](https://github.com/THUDM/ChatGLM3?tab=readme-ov-file)

### 2. Dataset Collection and Exploratory Data Analysis (EDA)
We've curated three primary datasets for our project:
- **Mental Health Knowledge Database**: Curated from relevant textbooks, articles, and research papers.
- **Mental Health Q&A Conversations**: Dialogues between professionals and patients in English and Chinese.
- **Emotion Detection Dataset**: User-generated text data annotated with emotion labels.

>Detailed dataset specifics are provided in the subsequent section.

### 3. Vector Store Construction
Leveraging Langchain, ChromaDB, OpenAI embeddings, we've established a vector store. This pivotal component contains mental health support knowledge and facilitates information retrieval based on user queries.

>Test cases for the vector store are elaborated in the concluding section.


## Dataset
> The detailed description of each dataset and some EDA can be find in the following [page](./update1_dataset).

### Mental Health Knowledge Database

The Mental Health Knowledge Database is an aggregation of textbooks, articles, and research papers focused on mental health support. Acquired from diverse sources, including academic databases, online libraries, and scholarly publications, this dataset encompasses a broad spectrum of topics within mental health support, such as mental health nursing, clinical psychology, and mental health education. This database serves as the foundation for constructing the vector store, a critical component facilitating information retrieval in our project.


### Mental Health Q&A Conversation Dataset

The Mental Health Q&A Conversation Dataset comprises dialogues between mental health professionals and patients in both English and Chinese. Given the time-intensive and costly nature of data collection, the majority of this dataset is sourced from previous similar projects. It encompasses conversations on diverse topics pertinent to mental health support, including depression, anxiety, and stress. This dataset is instrumental in fine-tuning the LLM to adeptly handle multi-turn conversations—a crucial capability in our project's generative process.


### Emotion Detection Dataset

The Emotion Detection Dataset comprises user-generated text data annotated with emotion labels. Sourced primarily from the Kaggle platform through various competitions or dataset collections, it includes text data labeled with emotions like happy, sad, angry, and neutral. This dataset is utilized to train the emotion detection model, enabling the LLM to gain a nuanced understanding of the user's emotional state throughout conversations.



## Vector Store Construction

This project's vector store are build based on the Mental Health Knowledge Database. At the beginning, we start with the embedding model from the Sentence Transformer framework. However, we found that the embeddings generated by the Sentence Transformer model are not optimal for our use case. That is the performance of finding the most relevant context compare with the user query from the vector store is not satisfactory. There are two options to improve the performance: 1) fine-tune the Sentence Transformer model on our dataset, 2) use the embeddings from the LLM (OpenAI Embedding model) and build a vector store based on the embeddings. We choose the second option because training on our dataset means we need manually pair the similar sentence together which is very time consuming ( consider this is not the main focus of this project) and the result is not guaranteed to be better than the LLM embeddings. On the other hand, OpenAI embedding models are pre-trained on a large corpus of text data and it is more likely to capture the semantic meaning of the sentence. The OpenAI embedding models are trained on multiple languages so we can ues it for our English and Chinese dataset instead of build two embedding models. Moreover, the price is very cheap,  the model we use 'text-embedding-3-small' only cost 0.02 USD per million tokens while achieve 62.3% performance on the MTEB (Muennighoff et al,2022) evalution.

### Reference(APA style)
Muennighoff, N., Tazi, N., Magne, L., & Reimers, N. (2022). MTEB: Massive Text Embedding Benchmark. arXiv preprint arXiv:2210.07316.