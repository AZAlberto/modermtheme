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
Leveraging Langchain, ChromaDB, OpenAI embeddings, and the Sentence Transformer framework, we've established a vector store. This pivotal component contains mental health support knowledge and facilitates information retrieval based on user queries.

>Test cases for the vector store are elaborated in the concluding section.


## Dataset
### Mental Health Knowledge Database

The Mental Health Knowledge Database is an aggregation of textbooks, articles, and research papers focused on mental health support. Acquired from diverse sources, including academic databases, online libraries, and scholarly publications, this dataset encompasses a broad spectrum of topics within mental health support, such as mental health nursing, clinical psychology, and mental health education. This database serves as the foundation for constructing the vector store, a critical component facilitating information retrieval in our project.


### Mental Health Q&A Conversation Dataset

The Mental Health Q&A Conversation Dataset comprises dialogues between mental health professionals and patients in both English and Chinese. Given the time-intensive and costly nature of data collection, the majority of this dataset is sourced from previous similar projects. It encompasses conversations on diverse topics pertinent to mental health support, including depression, anxiety, and stress. This dataset is instrumental in fine-tuning the LLM to adeptly handle multi-turn conversations—a crucial capability in our project's generative process.


### Emotion Detection Dataset

The Emotion Detection Dataset comprises user-generated text data annotated with emotion labels. Sourced primarily from the Kaggle platform through various competitions or dataset collections, it includes text data labeled with emotions like happy, sad, angry, and neutral. This dataset is utilized to train the emotion detection model, enabling the LLM to gain a nuanced understanding of the user's emotional state throughout conversations.

> The detailed description of each dataset and some EDA can be find in the following [page](./update1_dataset).

## Vector Store Test Cases