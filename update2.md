---
layout: default
title: Project Progress Updates Ⅱ
description: This is the pages contain information about the project update 2
---

# Project Progress Updates Ⅱ
[Back to the Home Page](./index)

## Update Overview

During this update phase, we mainly focus on building Emotion Extractor model.
We've achieved the following milestones:

### 1. Data Process
Data is the core to good machine learning models. In the data process stage, we have done lots of works including:

- **clean corpus**
- **remove stopwords in english**
- **remove duplicate rows**
- **Remove the outlier based on the text length**
- **Remove too short sentence in both dataset**
- **Resampling the dataset to get balanced distribution**
- **Convert to HF dataset & Split to train-dev-test set**
- **Tokenize**

The detailed procedure for data processing can be found in [here](./update2_data_process).

### 2. Model Selection
After the data process, we analysed different models for our task. Since there is language gaps between different languages, to better extract the emotion
from different inputs, we finally choosed one model for English and one model for Chinese:

- **Model For Chinese Sentiment Dataset:**: Erlangshen-DeBERTa-v2-320M-Chinese.
- **Model For English Sentiment Dataset:**: ernie-2.0-large-en.

The information about the two models and other models that we have tried or analysed can be found in [here](./update2_model_selection).

### 3. Training & Evaluation
After the model selection stage, we need to choose one model with top performance. Consequently, the two models we finally chose are the ones that
have the best performance in this training and evaluation stage. We adjust the models using hyperparameter tuning and optuna.

Hyperparameter Tuning & what is optuna
 - **1. learning_rate**
 - **2. num_train_epochs**
 - **3. per_device_train_batch_size**
 - **4. lr_scheduler_type**

For the evaluation metric, we have chosen accuracy and f1.
With the above training and evaluation procedures, we finally chose our best model Erlangshen-DeBERTa-v2-320M-Chinese for Chinese and ernie-2.0-large-en for English. The information about the training and evaluation can be found in [here](./update2_train_eval)

### 4. Inference & Demo
To demonstrate the model and make it easy for later usage, we have transferred the pipeline into Huggingface API which will be convenient to use.
We also came up with a demo using gradio to better illustrate our work.


#### Reference(APA style)

