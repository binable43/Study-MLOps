# Week 2A : CNNs

## Review of convolutions

### Why not use FC for images?

<img width="399" alt="스크린샷 2022-05-02 오전 11 29 14" src="https://user-images.githubusercontent.com/81629116/166395195-d48a3d96-85e1-435c-888a-4e107cd6f446.png">

- FC 작동 방식
    
    1) 32*32 image data → 1024*1 Flatten vector
    
    2) 10개의 class가 있으므로 1024*10 feature 배열 생성
    
    3) Flatten vector와 feature 배열을 곱해서 Output class 획득하고 이를 통해 Classification

<br>

- Issue 1
    - The dimensionality of the number of weights that you need to learn scales really poorly with the size of the image
    - We want neural networks that we use for computer vision to be able to **work well with larger images** as well
    
- Issue 2
    - Do we really need this **many weights** at all?
    - matrix multiplication : learning a weight a separate weight for each input pixel(image)
    - In many images there's maybe a few regions of that image that are particularly important to telling what's inside the image → overkill
    
- Issue 3
    - FC layer에 image를 넣으면 3차원 → 1차원 변형 과정에서 image의 spatial information을 잃게 됨

<br>

### Convolutional filters

<img width="415" alt="스크린샷 2022-05-02 오전 11 37 10" src="https://user-images.githubusercontent.com/81629116/166395207-53552a4a-d100-43fa-95f3-dffdaf3e0e54.png">

- entire image를 다루는 대신 flattening 한 후 matrix multiply
- 과정
    
    1) 5*5 patch를 통해 25 dimensional vector로 추출
    
    2) dot product를 통해 one-dimensional output으로 get
    
    3) 전체 image에서 5*5 patch를 slide해서 위 과정 반복
    
    
<br>

### Filter stacks and ConvNets

<img width="491" alt="스크린샷 2022-05-02 오후 12 00 13" src="https://user-images.githubusercontent.com/81629116/166395223-ba6e6bcc-7375-4c22-8223-2a6d2f8a4ac3.png">

input과 output이 정확하게 같은 size는 아니지만 3-dimensional tensor는 유지하고 있다. 

<img width="555" alt="스크린샷 2022-05-02 오후 5 19 46" src="https://user-images.githubusercontent.com/81629116/166395245-a3b952d9-d170-4121-bd0d-4e719ac00553.png">


앞서 본 것은 linear operation. 실제로는 각 layer 뒤에 non-linearity 적용.

<br>

### Strides & Padding

- Strides
    - Convolutions can subsample the image by jumping across some locations - called ‘stride’
    
<img width="514" alt="스크린샷 2022-05-02 오후 5 40 32" src="https://user-images.githubusercontent.com/81629116/166395261-b8472943-dfef-4739-a2ab-eda4f873a166.png">

만일 위의 예시와 같이 Stride가 커서 filter가 이동했을 때 image를 벗어나게 되면 어떻게 해야할까? → Padding

<br>

- Padding
    - Padding solves the problem of filters running out of image
    - Done by adding extra rows/cols to the input (usually set to 0)
    - ‘SAME’ padding is illustrated here for filter=(3,3) with stride=(2,2)
    - Not padding is called ‘VALID’ padding
    
<br>

### Filter Math

- Input: WxHxD volume
- Parameters:
    - K filters, each with size (F, F)
        - commonly set to powers of 2 (e.g. 32, 64, 128)
    - ... moving at stride (S, S)
        - commonly (5,5), (3,3), (2,2), (1,1)
    - ... with padding P
        - ‘SAME’ sets it automatically
- Output
    - W’ = (W - F + 2P) / S + 1
    - H’ = (H - F + 2P) / S + 1
- Each filter has (F * F * D) parameters
- K * (F * F * D) total in the layer

<br>

### Implementation notes

<img width="554" alt="스크린샷 2022-05-02 오후 5 57 28" src="https://user-images.githubusercontent.com/81629116/166395303-bb721462-1c71-46fd-bd09-c2f817451b3b.png">

<img width="557" alt="스크린샷 2022-05-02 오후 6 10 06" src="https://user-images.githubusercontent.com/81629116/166395320-20b46df5-febd-48a0-ab34-2297b6d47879.png">

- X_col (27 * 9)
    - 27 = 3 * 3 * 3 (extracted patch)
    - 9 = each of the positions in the input tensor
    

<img width="545" alt="스크린샷 2022-05-02 오후 6 29 40" src="https://user-images.githubusercontent.com/81629116/166395326-4cffd2b1-bc51-44b1-b4ed-be5e4c900537.png">


- W (32 * 27)
    - 32개의 filter
    - the # of weights (3 * 3 filter, 3-channel input) = 27 (3*3*3)
- W @ X = (32*27) @ (27*9) = (32 * 9)
- Reshape (3*3*32)

<br>
<br>

## Other important ConvNet operations

- Increasing the **receptive field** (dilated convolutions)
- Decreasing the size of the tensor
    - pooling
    - 1*1 - convolutions

<br>

### Receptive fields
