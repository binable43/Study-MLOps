# Week 4 : Transfer Learning and Transformers

## 1. Transfer Learning in Computer Vision
### Background
- ResNet-50이 좋은 성능을 보인다 but 신경망이 너무 크고 과적합 우려
- Solution : ImageNet의 데이터(1만장의 image)를 NN으로 학습 -> fine-tuning

### Transfer Learning (전이학습)
- ImageNet으로 모델 학습 -> 마지막 layer를 추가하거나 대체
- 더 적은 데이터로 빠르고 정확하게 학습이 가능하다
- Tensorflow, Pytorch

<br>
<br>

## 2. Embeddings and Language Models
- Input data
  - in NLP : sequence of words
  - in Deep Learning : vectors

- word를 vector로 변환하려면?
  - **one-hot encoding**

### One-hot encoding
- embedding : 문자를 기계가 이해할 수 있는 숫자로 바꾼 결과 
- Solution 1 : Learn as part of the task
- Solution 2 : Learn a Language Model

<br>
<br>

## 3. "NLP's ImageNet Moment" : ELMO/ULMFit
### Beyond Embeddings
- Word2Vec and GloVe embeddings became popular in ~2013-14
- But these representations are shallow:
  - only first layer would have benefit of seeing all of Wikipedia
  - rest of the model -- LSTMs, etc -- would be trained only on the task dataset (much smaller)

<br>

- Elmo (2018)
  - Bidirectional stacked LSTM
  - SQuAD dataset
  - SNLI dataset
  - GLUE dataset
- ULMFit
  - similar to ELMO
 
<br>
<br>

## 4. Transformers
- Paper : [**Attention is all you need(2017)**](https://arxiv.org/abs/1706.03762)

<br>

### Attention in detail
**Basic self-attention**
- Not a learned weights, but a function of x_i, x_j

**Attention Function**
- Query, Key, Value

**Transformer**
- self-attention layer - Layer normalization - Dense layer

<br>

### BERT, GPT-2, DistillBERT, T5
**GPT/GPT-2**
- Generative Pre-trained Transformer

**BERT**
- Bidirectional Encoder Representation from Transformers

**T5**
- Text-to-Text Transfer Transformer

**GPT-3**

**DistillBERT**
- a smaller model is trained to reproduce the output of a larger model

<br>
<br>

## Reference
- [Full Stack Deep Learning - Spring 2021](https://fullstackdeeplearning.com/spring2021/)
