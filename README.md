![image](https://github.com/user-attachments/assets/6c991496-8feb-474d-83a7-9b0ee179c20c)

# Predicting Psychiatric Disorders Based on EEG Features

This project uses a deep neural network to analyze EEG data and how they relate to a specific mental disorder.

## Overview

The task is to be able to predict a mental disorder based on EEG data. I used a deep neural network with 3 dense layers and classification loss function. The results were that the model would converge at around a 30% accuracy in predicting a mental disorder based off EEG data. This was out of 10 classes which is better than a 10% accuracy expected from random guessing.

## Summary of Workdone

### Data and data visualization

The data was large with 945 different patients and 1148 different features. 

First I looked at the non-EEG data which were age, education, and IQ. 
Age
![image](https://github.com/user-attachments/assets/3f4d5f5b-d6a4-4357-8c3c-f97712c2d68a)

IQ
![image](https://github.com/user-attachments/assets/89000ca0-7b26-4ba5-ab93-b7def3f5071b)

Education
![image](https://github.com/user-attachments/assets/fee7c5bc-dedc-47f5-9642-d0b5ac2925f2)

The distribution of the education column was not normal and would be optimal to remove it. I decided to remove all of the features from the data and aimed to predict based off pure EEG data instead.

![image](https://github.com/user-attachments/assets/10200dbc-9aba-48c1-a49a-5bd0852d767a)

![image](https://github.com/user-attachments/assets/60a372fa-58f9-427f-8087-af650f27f2c2)

![image](https://github.com/user-attachments/assets/34eaa738-31b7-4bed-90cf-63ca4ce6c1fb)

![image](https://github.com/user-attachments/assets/8b9ae580-18e4-4c07-b41c-34823b57d06e)

![image](https://github.com/user-attachments/assets/1549a1d1-63ca-4abe-b9e0-02c8d29f89d3)

![image](https://github.com/user-attachments/assets/6491d518-3a3a-41c1-af63-99e9823c4816)

![image](https://github.com/user-attachments/assets/f5250fa3-4d5f-42ec-82e5-4d3b1b67d166)

![image](https://github.com/user-attachments/assets/6453a4df-48a8-4eb6-942a-b63e8a362358)

![image](https://github.com/user-attachments/assets/cc00156e-f912-4d82-96c6-756b82d1eeea)

![image](https://github.com/user-attachments/assets/90e25531-4dc3-4ba9-b77d-3481fe737d35)

![image](https://github.com/user-attachments/assets/60a7cdf3-3637-4b4e-93c3-958d0bea8e63)

![image](https://github.com/user-attachments/assets/3ce8c950-a534-4436-8a24-7e7995e39ef9)

Most of the IQ distribution between the different classes were around 100 and with a standard deviation of 15 which suggests that there will be minimal effects of IQ on the disorder or brain waves of the person.

#### Preprocessing / Clean up

I decided to keep the EEG features pure because they are already feature engineered and batch normalization was done within the neural network.
However, for the target variables, I decided to one-hot encode the target variables and transformed them into floating-point values. I decided to remove the Acute Stress Disorder and Adjustment Disorder classes because of their low frequency. 

![image](https://github.com/user-attachments/assets/3d819421-b624-4fd1-af27-c37cf61f954a)


### Problem Formulation

The input were the EEG features that were engineered and the target variables were the disorders classified. I used a dense neural network model with 3 dense layers and binary-crossentropy loss function.

### Training

The training was done with large batch sizes and the use of an "elastic-net" which is the combination of L1 and L2 regularizing functions to prevent overfitting of the data.

![image](https://github.com/user-attachments/assets/8c0e595b-d25b-4ed3-ad14-662ccd642808)

![image](https://github.com/user-attachments/assets/e7e7ed1a-a974-46d4-b29f-1eb90ce655d2)

### Performance Comparison

The following ROC curves were done for each initial feature classification. More clearly, every single disorder had a binary classifier attached to it based on the neural network architecture.

![image](https://github.com/user-attachments/assets/0a620a67-01c3-4853-8f4d-f4c538e1a175)

![image](https://github.com/user-attachments/assets/7da5a49c-b745-4685-94ed-0d17bac8b546)

![image](https://github.com/user-attachments/assets/ecac69e6-f3e7-46bd-8520-af406cfefe2f)

![image](https://github.com/user-attachments/assets/c8f49391-c063-43bf-8916-0c5137c50304)

![image](https://github.com/user-attachments/assets/33aec17f-3bd4-4833-9a49-9c7114de18ee)

![image](https://github.com/user-attachments/assets/33f9a72c-1ea4-49dd-b162-aec85e6d6374)

![image](https://github.com/user-attachments/assets/f8995e4a-927a-4b62-a990-e2a4cc1f8cb3)

![image](https://github.com/user-attachments/assets/09d44ba4-bbd7-47b8-aa81-414edbfc6c52)

Better ROC curves than before but they are still poorly performing and are as good as random guesses. However, it seems like it learned something about the healthy control group which means there are features about the healthy controls not seen in those with mental health disorders.

### Conclusions

It seems like people who were healthy controls tended to have features different from those diagnosed with a disorder. I decided to compare the distributions of the aggregated features based off the frequency. 
Delta: 0.5–4 Hz
Theta: 4–8 Hz
Alpha: 8–12 Hz
Beta: 12–30 Hz
Gamma: 30–100 Hz

The two most notable features were the gamma and beta frequency bands.

![image](https://github.com/user-attachments/assets/3523e5db-14b7-4973-9b9e-6488267944ce)

![image](https://github.com/user-attachments/assets/048db32b-049c-4aba-8415-881d3311d9db)

I did a signal significance test and found that the upper thresholds were ~76 hz for the gamma frequencies and ~62hz both with a signifiance of ~3.4 which suggests that hyperactivity of both gamma and beta
frequencies are implicated in psychiatric disorders. This makes sense as these two bands are involved in higher-order thinking.

### Future Work

It would be optimal to try different neural network architectures and perhaps apply a more sophisticated regularizer or architecture. I was looking at data transformation on a manifold.







