# Week 5 : ML Project

## Why do so many projects fail?

- ML is still reserch - you shouldn’t aim for 100% succss rate
- But many are doomed to fail:
    - Technically infeasible or poorly scoped
    - Never make the leap to production
    - Unclear success criteria
    - Poor team management

<br>

## Module Overview

- Lifechcle
- Prioritizing Projects
- Archetypes
- Metrics
    - 최적화하는 과정에서 뽑아보는 single number
- Baselines
    - model이 well performing하고 있는지 확인하기 위해

<br>
<br>

## 1. Lifecycle

- How to think about all of the activities in an ML project    
<img width="740" alt="1" src="https://user-images.githubusercontent.com/81629116/170257398-66a7bec8-3c00-408c-91e3-6d76e116c615.png">

<img width="740" alt="2" src="https://user-images.githubusercontent.com/81629116/170257400-2bb77375-3513-4ae7-a6da-784e251c99f4.png">

<img width="741" alt="3" src="https://user-images.githubusercontent.com/81629116/170257407-8aed1e24-646b-481c-8f4f-726b42e84934.png">

<img width="742" alt="4" src="https://user-images.githubusercontent.com/81629116/170257424-5c63fb6f-0f73-49dc-b447-6c4019a00e5e.png">

<img width="741" alt="5" src="https://user-images.githubusercontent.com/81629116/170257430-19b4261e-7acd-4de9-872f-5a407d06940e.png">

<img width="740" alt="6" src="https://user-images.githubusercontent.com/81629116/170257437-60240e84-6b6f-4c88-a7ea-84bd8bc2bedf.png">

<img width="742" alt="7" src="https://user-images.githubusercontent.com/81629116/170257443-e9c4ef31-63b4-4b6b-9b02-fda240657262.png">

<img width="743" alt="8" src="https://user-images.githubusercontent.com/81629116/170257454-061689ea-bf11-4d59-9f2b-8aea70c455dd.png">

<img width="741" alt="9" src="https://user-images.githubusercontent.com/81629116/170257475-8ac329b1-e1e3-4503-90bb-c092669648a0.png">

<img width="741" alt="10" src="https://user-images.githubusercontent.com/81629116/170257486-dce39255-ef75-4508-9893-16a1cedbe0a0.png">

<img width="739" alt="11" src="https://user-images.githubusercontent.com/81629116/170257494-20468bbe-101b-484c-9e46-62ccbb470e68.png">

<br>

### What else do you need to know?

- Understand state of the art in your domain
    - Understand what’s possible
    - Know what to try next
- most promising research areas

<br>
<br>

## 2. Prioritizing Project

- Assessing the feasibility and impact of your projects

### Key Points

A) High-impact ML problems

- Friction in your product
- Complex parts of your pipeline
- Places where cheap prediction is valuable
- What else are people doing?

B) Cost of ML project is driven by data avilability. Also consider accuracy requirements and intrinsic difficulty of the problem


<br>

### General framework for prioritizing

<img width="556" alt="12" src="https://user-images.githubusercontent.com/81629116/170257905-5cb1183b-0241-45cd-8601-cd3eaaef84a4.png">

<br>

### Mental models for high-impact ML projects

- Where can you take advantage of cheap prediction?
- Where is there friction in your product?
- Where can you automate complicated manual processes?
- What are other people doing?

<br>

### What does ML make economically feasible?

<img width="568" alt="13" src="https://user-images.githubusercontent.com/81629116/170257945-94818b6c-26fd-49d2-bfc2-f23018b3e13a.png">


### Assessing feasibility of ML projects

<img width="738" alt="14" src="https://user-images.githubusercontent.com/81629116/170257967-7806a3ed-c137-4223-9263-804879f2ed4d.png">


### What is still hard in ML?

- Unsupervised learning
- Reinforcement learning

→ Both are showing promise in limited domains where tons of data and compute are available

<br>

### How to run a ML feasibility assessment

1) Are you sure you need ML at all?

2) Put in the work up-front to define success criteria with all of the stakeholders

3) Consider the ethics of using ML

4) Do a literature review

5) Try to rapidly build a labeled benchmark dataset

6) Build a “minimal” viable product (e.g., manual rules)

7) Are you sure you need ML at all?

<br>
<br>

## 3. Archetypes

- The main categories of ML projects, and the implications for project management
<img width="489" alt="15" src="https://user-images.githubusercontent.com/81629116/170258035-b60b576f-24c8-4184-96ac-39270116937f.png">

<img width="535" alt="16" src="https://user-images.githubusercontent.com/81629116/170258053-716f4ad2-49ea-444e-98f5-ae3e1c6af4c9.png">

<br>
<br>

## 4. Metrics

- How to pick a single number to optimize

### Key points

A. The real world is messy ; you usually care about lots of metrics

B. However, ML systems work best when optimizing a single number

C. As a result, you need to pick a formula for combining metrics

D. This formula can and will change

<br>

### How to combine metrics

- Simple average / weighted average
- Threshold n-1 metrics, evaluate the nth
- More complex / domain-specific formula

<br>
<br>

## 5. Baselines

- How to know if your model is performing well

### Key points

A. Baselilnes give you a lower bound on expected model perfrormance

B. The tighter the lower bound, the more useful the baseline(e.g, published results, carefully tuned pipelines, & human baselines are better)

<br>

### Where to look for baselines

<img width="662" alt="17" src="https://user-images.githubusercontent.com/81629116/170258126-ecd7a125-0259-4dc8-9239-6989997e6003.png">

<br>
<br>

## Conclusion

<img width="549" alt="18" src="https://user-images.githubusercontent.com/81629116/170258146-d6ef8ab1-cf6c-494e-8263-39067c681432.png">


### Where to go to learn more

- Andrew Ng’s “Machine Learning Yearning”
- Andrej Karpathy’s “Software 2.0”
- Agrawal’s “The Economics of AI”
- Chip Huyen’s “Introdution to Machine Learning Systems Design”
- Apple’s “Human Interface Guidelines for Machine Learning”
- Google’s “Rules of Machine Learning”

<br>
<br>

## Reference
- [Full Stack Deep Learning - Spring 2021](https://fullstackdeeplearning.com/spring2021/)

