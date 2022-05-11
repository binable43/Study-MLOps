# Week 3 : RNNs (Recurrent Neural Networks)

## Sequence Problems
### Sequence Problems
- Time series forecasting (시계열 예측)
  - the input is sequence and the output is single value
- Sentiment classification
- Translation
  - input and output are both sequence
- Speech recognition and generation
- Text or music generation
- Question Answering
  - the input is text and the output is a subset of text

<br>

### Types of sequence problems
1) one to many (single input & sequence output)
2) many to one (sequence input & single output)
3) many to many (sequence input & sequence output)

![스크린샷 2022-05-10 오후 11 49 45](https://user-images.githubusercontent.com/81629116/167657342-2b1878ab-cb1d-4263-a51f-793af075cbd3.png)

<br>

### Why not use feedforward networks?
- feedforward networks (순방향 신경망) : 노드 간의 연결이 순환을 형성하지 않는다
- many to many problem이라고 가정    
![스크린샷 2022-05-10 오후 11 53 46](https://user-images.githubusercontent.com/81629116/167658266-c0125768-efcf-4736-aa8f-1a5047002e7a.png)

<br>

**> Problem 1 : variable length inputs**   
임의의 길이를 가진 input을 잘 처리하지 못한다는 단점이 있다. 이를 해결하기 위해 max length에 맞춰서 empty value를 padding하는 방법이 있다.   
![스크린샷 2022-05-10 오후 11 55 07](https://user-images.githubusercontent.com/81629116/167658649-1c3a4d02-3c00-4a6d-807a-d8b6b0ee6f00.png)

<br>

**> Problem 2 : memory scaling**   
만일 sequence의 max length를 늘리게 되면 multiply해야 하는 matrix의 크기도 함께 커진다 -> undesirable scaling   
![스크린샷 2022-05-10 오후 11 55 12](https://user-images.githubusercontent.com/81629116/167658660-d58ba1bc-8f5c-406c-9205-b6b572b891c5.png)


<br>

**> Problem 3 : overkill**   
sequence에서 pattern을 파악하려고 할 때 특정 input은 특정 output과 상관관계가 있을 것이다.    
이 때 model은 이러한 상관관계를 위한 weight을 학습해야 한다 -> data ineffieicnt   
![스크린샷 2022-05-10 오후 11 55 18](https://user-images.githubusercontent.com/81629116/167658672-3bf95293-53bf-4067-9aa2-ff64ad357cea.png)


<br>
<br>

## RNNs
### Main Idea   
- every position in the sequence에 대해 독립적인 weights을 곱하는 single massive matrix 대신 stateful computation을 사용
- model의 output은 current time step in the sequence에서의 input에 따라 달라진다
- each time step에서 input에 따라 해당 time step에 대한 output과 next hidden state을 출력

<br>

### RNN 과정 
1. starting hidden state인 h0가 존재.   
2. 첫번째 input x1을 받은 model이 h0와 x1을 계산하여 첫번째 output y1와 second hidden state h1을 생성한다. 
3. 각각의 subsequent time step에서 2와 동일한 계산 과정을 거친다. 

![스크린샷 2022-05-11 오전 12 39 11](https://user-images.githubusercontent.com/81629116/167667784-11fde374-5034-49d4-b000-0234fea5a98b.png)

<br>

### RNN in Code
```python
class RNN:
  #...
  def compute_next_h(self, x):
    # Simple hidden state computation
    h = np.tahn(self.W_hh.dot(self.h) + self.W_xh.dot(x))
    return h
   
  # this function gets called every single time the model sees a new input
  def step(self, x):
    # update (next) hidden state
    self.h = self.compute_next_h(x)
    # compute the output vector
    y = self.W_hy.dot(self.h)
    return y
```

**> A look at compute_next_h function** 
- 2개의 input : property of this class (previous hidden state h_t-1) & input of time step x_t
- 2개를 더해서 activation function(tahn)으로 wrap up   

![스크린샷 2022-05-11 오전 12 49 03](https://user-images.githubusercontent.com/81629116/167669848-d188ae7b-c7a3-472b-8da8-0fd7eba12f59.png)


<br>
<br>

### RNN models
![스크린샷 2022-05-11 오전 1 02 06](https://user-images.githubusercontent.com/81629116/167672486-901aa46c-f567-4b8d-8b3d-9ffd613345e7.png)

<br>

![스크린샷 2022-05-11 오전 1 02 16](https://user-images.githubusercontent.com/81629116/167672507-d1362609-ebca-4526-b553-f131e9af7f9f.png)

<br>

![스크린샷 2022-05-11 오전 1 02 26](https://user-images.githubusercontent.com/81629116/167672527-6c7bc679-ad55-4dd6-a548-e2344fdc2a6c.png)


<br>
<br>

## Vanishing gradients and LSTMs
### RNN Desiderata 
- Goal : handle long sequences
- Connect events from the past to outcomes in the future
  - i.e., Long-term dependencies
  - e.g., remember the name of a character from the first sentence

### Vanilla RNNs : The reality
- Can't handle more than 10-20 timesteps
- Longer-term dependencies get lost
- WHY? **Vanishing Gradients**
  - sigmoid, tanh ; input 커질수록 derivative 값이 0에 수렴 -> 기울기 소실이 발생
  - ReLU : exploding gradients (gradients tend to get too big)


### LSTMs
```python
class LSTM(RNN):
  # ...
  def compute_next_h(self, x):
    h = lstm(x, self.h)
    # or gru(x, self.h), etc.
    return h
  # ...
```



<br>
<br>

## Case study : Machine Translation
### Key Questions for applications
- What problem are they trying to solve?
- What model architecture was used?
- What loss function was used?
- What dataset was it trained on?
- How did they do training?
- What tricks were needed for inference in depolyment?

<br>

### Google's Neural Machine Translation System (GNMT)
- Google’s Neural Machine Translation System: Bridging the Gap between Human and Machine Translation (Wu et al., 2016)
- Summary of GNMT approach
  - Stacked LSTM encoder-decoder architecture with residual connections
  - Attention enables longer-term connections
  - To encode future information in the source sentence use a bidirectional LSTM
  - Train using standard cross-entropy on a large dataset
  - Speed up inference with quantization of weights


<br>
<br>

## CTC loss

- The Goal
- The Idea
- CTC Loss

<br>
<br>

## Pros and Cons
### Pros
- Encoder/Decoder LSTM architectures can model arbitray (one-to-many, many-to-one, many-to-many) sequence problems
- Many successes in NLP and other applications

<br>

### Cons
- Recurrent network training is not as parallelizable as FC or CNN, due to the need to go in sequence
- Therefore much slower!
- Also can be finicky to train


<br>
<br>

## A preview of non-recurrent sequence models
- Convolutional approach to sequence data modeling
- Next lecture, all-fully-connected Transformer models

### WaveNet
- Inference
  - Primary drawback of WaveNet: although training is parallel, inference is serial
  - Followup paper introduced fast, parallel synthesis version of WaveNet: Parallel WaveNet

- Summary of WaveNet approach
  - Another way of dealing with long-term dependencies is to do away with recurrent networks altogether
  - Instead, you can use a form of 1d convolutions called causal convolutions
  - To increase the receptive field of causal convolutions, can used dilated causal convolutions
  - In addition to long-term dependencies, main advantage of WaveNet is fast parallel training
  - Tradeoff is slow inference time, which can be mitigated through the parallel WaveNet approach


<br>
<br>

## Reference
- [Full Stack Deep Learning - Spring 2021](https://fullstackdeeplearning.com/spring2021/)
- [Understanding LSTM Networks](http://colah.github.io/posts/2015-08-Understanding-LSTMs/)
