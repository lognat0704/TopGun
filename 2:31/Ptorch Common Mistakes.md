### 1. Didn't overfit batch
Use 1 batch to overfit
<img width="701" alt="Screen Shot 2022-06-13 at 10 49 15 PM" src="https://user-images.githubusercontent.com/9245626/173483103-032c8fa4-18e1-4804-9e77-8405a5e54b12.png">
<img width="800" alt="Screen Shot 2022-06-13 at 10 49 45 PM" src="https://user-images.githubusercontent.com/9245626/173483109-f70804ec-1042-4f01-8654-d10698fa45fe.png">

Uae Normal batch to see lose decrease
<img width="971" alt="Screen Shot 2022-06-13 at 10 51 10 PM" src="https://user-images.githubusercontent.com/9245626/173483259-48924481-d3cd-4efe-aff7-e73c9e12d8f1.png">

### 2. Forgot toggle train/eval
Eval will turn off dropout and batchnorm for prediction
<img width="492" alt="Screen Shot 2022-06-13 at 10 55 00 PM" src="https://user-images.githubusercontent.com/9245626/173483738-48262784-8d5a-4e73-ad2d-a56e72aebf9a.png">


### 3. Forgot .zero_grad()
If u forgot, it backprop using accumulated grad from all previous batches.
<img width="418" alt="Screen Shot 2022-06-13 at 10 56 44 PM" src="https://user-images.githubusercontent.com/9245626/173484035-0dd1baef-d582-41f9-9a09-e33dff56b848.png">

### 4. Softmax when using CrossEntropy
CrossEntropy = softmax+negative-log likelihood, do it u will ger gradient vanish problem.

### 5. Bias term with BatchNorm
Set Cov layer set bias=False if we have a batchnorm after
<img width="356" alt="Screen Shot 2022-06-13 at 11 05 43 PM" src="https://user-images.githubusercontent.com/9245626/173485065-d0f870e9-5945-4166-85a5-256861b65523.png">
<img width="819" alt="Screen Shot 2022-06-13 at 11 06 07 PM" src="https://user-images.githubusercontent.com/9245626/173485066-16d81293-208b-4e5f-8fbc-114a05919ba5.png">

### 6. Using view as permute
### 7. Incorrect Data Augmentation 
### 8. Not Shuffling Data
### 9. Not Normalizing Data
### 10. Not Clipping Gradients
