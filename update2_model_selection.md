---
layout: default
title: Project Progress Updates Ⅱ model selection
description: This is the pages contain information about the model selection
---

In the analysis of Chinese sentiment data sourced from Weibo, the Erlangshen-DeBERTa-v2-320M-Chinese model, as introduced by Zhang et al. (2022) and obtained from IDEA-CNLL, was employed. This model, based on DeBERTa-v2-large and pre-trained on the WuDao Corpora (180 GB version), utilized Whole Word Masking (wwm) in its Masked Language Modeling(MLM) training phase. Zhang et al. (2022) reported a training duration of approximately 7 days using their Fengsheng framework and 8 A100 (80G) GPUs.

DeBERTa, short for “Decoding-enhanced BERT with Disentangled Attention,” was originally proposed by He et al. in 2020 and tailored for Natural Language Understanding (NLU) tasks. The model’s key innovations encompass disentangled attention mechanism and Enhanced mask decoder. The former involves calculating attention scores using both content and position vectors, facilitating the consideration of content-content, content-position, and position-position relationships. The disentangled attention mechanism can be represented mathematically as:

![](./update2_model_pic.png)

Here, H_i represents content for a token at position i while P_ij denotes relative position with respect to the token at position j. Indeed, an observed phenomenon is that the attentional weight assigned to word pairs is contingent not only upon their semantic content but also on their relative positions within the context. For instance, when words like "deep" and "learning" occur adjacently, their interdependence is notably stronger compared to when they appear in separate sentences.

Alternatively, the enhanced mask decoder involves incorporating absolute position information into the BERT decoder during pre-training. This enables the model to predict masked tokens more accurately. For instance, let's take the sentence "a new store opened beside the new mall" with the words "store" and "mall" masked for prediction. In this scenario, relying solely on local context (i.e., relative positions and surrounding words) proves inadequate for the model to differentiate between "store" and "mall" in the sentence, as both words follow the word "new" with identical relative positions.

DeBERTa-v2 introduces several enhancements compared to its predecessor, including an expanded vocabulary size, an additional convolution layer alongside the first transformer layer to capture local token dependencies, sharing position projection matrix with content projection matrix in attention layer, and employing bucketing to encode relative positions. These modifications contribute to further improving DeBERTa's performance across NLU tasks, including sentiment analysis.
