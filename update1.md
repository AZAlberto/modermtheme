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


### 3. Vector Store Construction
Leveraging Langchain, ChromaDB, OpenAI embeddings, we've established a vector store. This pivotal component contains mental health support knowledge and facilitates information retrieval based on user queries.



## Dataset
> The detailed description of each dataset and some EDA can be find in the following [page](./update1_dataset).

### Mental Health Knowledge Database

The Mental Health Knowledge Database is an aggregation of textbooks, articles, and research papers focused on mental health support. Acquired from diverse sources, including academic databases, online libraries, and scholarly publications, this dataset encompasses a broad spectrum of topics within mental health support, such as mental health nursing, clinical psychology, and mental health education. This database serves as the foundation for constructing the vector store, a critical component facilitating information retrieval in our project.


### Mental Health Q&A Conversation Dataset

The Mental Health Q&A Conversation Dataset comprises dialogues between mental health professionals and patients in both English and Chinese. Given the time-intensive and costly nature of data collection, the majority of this dataset is sourced from previous similar projects. It encompasses conversations on diverse topics pertinent to mental health support, including depression, anxiety, and stress. This dataset is instrumental in fine-tuning the LLM to adeptly handle multi-turn conversations—a crucial capability in our project's generative process.


### Emotion Detection Dataset

The Emotion Detection Dataset comprises user-generated text data annotated with emotion labels. Sourced primarily from the Kaggle platform through various competitions or dataset collections, it includes text data labeled with emotions like happy, sad, angry, and neutral. This dataset is utilized to train the emotion detection model, enabling the LLM to gain a nuanced understanding of the user's emotional state throughout conversations.



## Vector Store Construction
>Test cases for the vector store are elaborated in the following [page](./update1_testcases).

In this project, the vector store is constructed leveraging the Mental Health Knowledge Database as its foundational dataset. Initially, we employed the embedding model provided by the Sentence Transformer framework. However, the embeddings produced by this model did not meet our performance expectations for retrieving the most contextually relevant information compared to user queries from the vector store.

To enhance the vector store's performance, two potential strategies were considered:

1. Fine-tuning the Sentence Transformer model using our dataset.
2. Utilizing embeddings from the Language Model (LLM) provided by OpenAI to construct the vector store.

We opted for the second approach due to several reasons. Firstly, fine-tuning the model on our dataset would necessitate manually pairing semantically similar sentences, which is both time-intensive and not the primary focus of this project. Furthermore, the efficacy of this approach is not guaranteed to surpass that of the LLM embeddings.

Conversely, OpenAI's embedding models are pre-trained on extensive text corpora, making them adept at capturing nuanced semantic meanings of sentences. These models support multiple languages, enabling us to utilize a single model for both our English and Chinese datasets, thereby eliminating the need to build separate embedding models. Additionally, the cost-effectiveness of this approach is noteworthy; the 'text-embedding-3-small' model incurs a minimal cost of 0.02 USD per million tokens while achieving a performance of 62.3% on the MTEB evaluation (Muennighoff et al., 2022).

### Test Cases

### Reference(APA style)
Muennighoff, N., Tazi, N., Magne, L., & Reimers, N. (2022). MTEB: Massive Text Embedding Benchmark. arXiv preprint arXiv:2210.07316.