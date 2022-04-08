# Week 1 : Fundamentals


We do a blitz review of the fundamentals of deep learning, and introduce the codebase we will be working on in labs for the remainder of the class.

## Neural Networks

- 우리 몸의 뉴런에서 영감을 받음
- 수학적으로.. perceptron
- 수상돌기에 들어가는 자극은 input으로 볼 수 있음
- b : bias. 선형 함수이기 때문에 y절편에 대한 offset(상쇄)이 필요.
- activation function : threshold를 넘을 경우 활성화, 그렇지 못할 경우 비활성화하는 함수

## activation function

- g`(z) : derivative(도함수), gradient

### Sigmoid

- input이 무엇이든 간에 output은 0~1 사이의 수로 반환
- asymptote(점근선)은 0

### Hyperbolic Tangent (tanh)

### Rectified Linear Unit (ReLU)

- 최근에 많이 사용
- 어떤 value가 input으로 들어왔을 때 0 이상이면 pass,0보다 작으면 don’t pass

## Neural Networks

- input layer-hidden layer 1, 2, 3 - output layer 로 연결
- each perceptrons는 각각의 weight와 bias를 갖고 있다 → input에 대해 어떻게 반응하는가에 대한 정보

## Universality

### universal approximaition theorem (시벤코 정리)

- 적절한 hidden unit을 가진 1개의 hidden layer Neural Network를 이용하면 어떤 함수든 근사시킬 수 있다
- 이 때 활성화 함수는 비선형 함수
- 실험
    
    [딥러닝 - Universal Approximation Theorem 실험](https://3months.tistory.com/140)
    

## Learning Problems

### Supervised Learning

- Labeled data X and Y
- Learn X → Y
- goal : make predictions

### Unsupervised Learning

- unlabeled data X
- Learn X
- goal : generage fakes, insights
- you don’t have a lable of data
- ex) predict next character, GAN

### Reinforcement Learning

- Learn how to take actions in an Environment

## Empirical Risk Minimization / Loss Functions

### Linear Rgression

- 우리가 알고 있는 x에 대하여 output y는 어떻게 나오는지 그 관계(line)를 알고 싶어한다
- `y = ax +` b 로 표현 가능
- 우리가 관찰하는 point들과 candidate line의 squared error(평균 제곱 오차)가 최소가 되도록 해야한다. 즉, squared error가 최소가 되도록 하는 a, b를 찾고자 함.
- squered error function = loss function
- Out goal : minimize the loss function

- In Regression...
    - Typical losses
        - Mean Squered Error(MSE)
        - Huber loss (=more robust to outliers)
- In Classification...
    - Typical losses
        - cross-entropy

## Gradient Descent

- Our goal is that find w, b that optimize the function.
- How to Improve One Parameter?
    - What we can do is... update each W
    - 해당 w(가중치)에 learning rate(알파)을 곱한 loss function의 gradient(기울기)를 뺀다
        <img width="293" alt="스크린샷 2022-04-08 오후 5 31 06" src="https://user-images.githubusercontent.com/81629116/162410444-752c6a10-19e1-4898-878d-89a9b7166a45.png">

        
- How to Improve All Parameter?
    - Gradient Descent (a.k.a Steepest Descent)
    - 즉, weight을 조정하는 과정

### Conditioning

- first order methods: (한번 미분한 변수로만 이루어진 식)
    - Initialization
    - Normalization
        - Batch norm, weight norm, layer norm ...
- Second order methods: (두번 미분한 변수로만 이루어진 식)
    - Exact:
        - Newton’s method
        - Natural gradient
    - Approximate second order methods:
        - Adagrad, Adam, Momentum

### Batch Gradient Descent

- it computes the gradient using the whole dataset

### Stochastic Gradient Descent

- compute each gradient step on just a subset (”batch”) of data
- it use a batch of just size one → you look at one data point, compute the loss on it and update all weights with just that loss

→ less compute per step

→ more noisy per step

- overall : faster progress per amount of compute

## Backpropagation

- 순방향으로 f를 계산한 다음에 정보를 caching하여 역방향으로 수행
- chain rule을 통해 미분값들을 연쇄적으로 곱해서 gradient 얻기
- Automatic Differentation
    - 우리가 직접 일일히 differentiation을 하지 않아도 된다!
    - Only need to program the function f(x, w)
    - Software automatically computes all derivatives
    - e.g. PyTorch, TensorFlow, Theano, Chainer, etc.
- All I have to do is just program the forward function f → pytorch will give some gradients for me!

## Architectual Considerations (deep / conv / rnn)

- computer vision : Convolutional Networks
    - spatial translation invariance
- sequence processing (e.g. NLP) : Recurrent Networks
    - temporal invariance

## CUDA

- GPU가 왜 중요한가?
    - All NN computations are just matrix multiplications, which are well parallelized onto the many cores of a GPU.
    - matrix multiplications는 gpu의 core에 parallelize하기 쉽다
   

## More Reading

- **[How the backpropagation algorithm works](http://neuralnetworksanddeeplearning.com/chap2.html)**

## Reference

- [Full Stack Deep Learning - Spring 2021](https://fullstackdeeplearning.com/spring2021/)
