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

### Types of sequence problems
1) one to many (single input & sequence output)
2) many to one (sequence input & single output)
3) many to many (sequence input & sequence output)

![스크린샷 2022-05-10 오후 11 49 45](https://user-images.githubusercontent.com/81629116/167657342-2b1878ab-cb1d-4263-a51f-793af075cbd3.png)


## Why not use feedforward networks?
- feedforward networks (순방향 신경망) : 노드 간의 연결이 순환을 형성하지 않는다
- many to many problem이라고 가정    
![스크린샷 2022-05-10 오후 11 53 46](https://user-images.githubusercontent.com/81629116/167658266-c0125768-efcf-4736-aa8f-1a5047002e7a.png)

<br>

**> Problem 1 : variable length inputs**    
![스크린샷 2022-05-10 오후 11 55 07](https://user-images.githubusercontent.com/81629116/167658649-1c3a4d02-3c00-4a6d-807a-d8b6b0ee6f00.png)

<br>

**> Problem 2 : memory scaling**   
![스크린샷 2022-05-10 오후 11 55 12](https://user-images.githubusercontent.com/81629116/167658660-d58ba1bc-8f5c-406c-9205-b6b572b891c5.png)


<br>

**> Problem 3 : overkill**  
![스크린샷 2022-05-10 오후 11 55 18](https://user-images.githubusercontent.com/81629116/167658672-3bf95293-53bf-4067-9aa2-ff64ad357cea.png)



<br>
<br>

## RNNs



<br>
<br>

## Vanishing gradients and LSTMs

<br>
<br>

## Case study : Machine Translation

<br>
<br>

## CTC loss

<br>
<br>

## Pros and Cons

<br>
<br>

## A preview of non-recurrent sequence models

<br>
<br>

## Reference
- [Full Stack Deep Learning - Spring 2021](https://fullstackdeeplearning.com/spring2021/)
