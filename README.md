# Skin Lesion Detection Using Neural Networks
![logo](https://user-images.githubusercontent.com/93217519/157762783-04e4699a-941c-45a7-a6ce-a7bae22adeec.jpeg)

There are over 200 different forms. Out of 200, melanoma is the deadliest form of skin cancer. Among all the skin cancer type, melanoma is the least common skin cancer, but it is responsible for 75% of death. Melanoma skin cancer is highly curable if it gets identified at the early stages. The first step of Melanoma skin cancer diagnosis is to conduct a visual examination of the skin's affected area. This project aims to build an automated classification system based on image processing techniques to classify skin cancer using skin lesions images. The approach uses Convolutional Neural Network (CNN) to perform a binary classification from outlier lesions images. This reduction of a gap has the opportunity to impact millions of people positively.

## Dataset
The project dataset is openly available on Kaggle(https://www.kaggle.com/drscarlat/melanoma).

#### Sample Images from the Dataset:

-The images below are labelled as Melanoma in the dataset.

<img width="100" alt="Screen Shot 2022-03-09 at 09 32 15" src="https://user-images.githubusercontent.com/93217519/157761856-6d900aca-63e5-4b02-89ad-392f19401704.png"> <img width="100" alt="Screen Shot 2022-03-09 at 09 31 59" src="https://user-images.githubusercontent.com/93217519/157761910-8da0cd74-d723-4281-9695-cad6a07f0069.png"> <img width="100" alt="Screen Shot 2022-03-09 at 09 31 28" src="https://user-images.githubusercontent.com/93217519/157761912-67c66006-ce7b-4d85-a390-886781b97cc3.png">

-The images below are labelled as NotMelanoma in the dataset.

<img width="100" alt="Screen Shot 2022-03-10 at 17 01 14" src="https://user-images.githubusercontent.com/93217519/157762087-5dae3253-dd3f-4c8b-8a52-7d26cf6542b7.png"> <img width="100" alt="Screen Shot 2022-03-10 at 17 01 05" src="https://user-images.githubusercontent.com/93217519/157762088-ebdc7997-1fe4-43c1-9dad-240441660851.png"> <img width="100" alt="Screen Shot 2022-03-10 at 17 00 56" src="https://user-images.githubusercontent.com/93217519/157762089-0cae884c-fd02-430f-91d4-d8f25e3a3fa7.png">


## Preprocessing

In any machine learning project, it is critical to set up a trustworthy validation scheme, in order to properly evaluate and compare models. This is especially true if the dataset is small which is the case of this project.

For a typical image classification problem, the standard approach is to take a deep CNN model (such as the most popular EffcientNet) trained on ImageNet, replace the last layer so that the output dimension equals the target's dimension, and fine tune it on the specific dataset.

The target to predict is binary-melanoma i.e. Melanoma and Not Melanoma. 

## Data Augmentation

In a small size dataset, image augmentation is required to avoid overfitting the training dataset. The augmentation that helps to improve the prediction accuracy of the model are as follows:
- **Rotation:** rotates the image by a specified degree.
- **Shearing:** shifts one part of the image like a parallelogram
- **Horizontal flip:** randomly flipps half the images horizontally—relevant when there are no assumptions of horizontal asymmetry

## Network Configurations
I used ensemble terminology to train diverse models. The model configuration is as follows:

1. **Pretrained CNN Models:** I chose to use Efficent Net B4 AND ResNet 50 as they achieved higher accuracy on ImageNet competition
2. **Targets:** The models are trained 10682 images belonging to two classes 
3. **Resized** input image sizes to 224x224 pixels to lower resolution due to GPU memory constraints
4. **Optimizer**: *Adam*. As we have sparse data, Adam is used because of the adaptive learning rate.

## Results & Evaluation

| Models        | Test Accuracy  |  # Trainable Params |Epochs |
| ------------- |:-------------:| -----:|-----:|
| Baseline      | 82.83% | 1,625,026 | 30 |
| Efficient Net B4 (augmented)      | 89.53%     |   5,619,906 |29 |
| Efficient Net B4 (1 trainable layer) | 90.96%      | 5,619,906 |15 |
| Efficient Net B4 (3 trainable layer) | 92.59%      | 6,426,306 |10 |
| ResNet 50 (augmented) | 93.23%      |    6,422,722 |30 |
| ResNet 50 (3 trainable layers) | **93.91%**      |    6,426,818 |37 |
| ResNet 50 (5 trainable layers) | 93.29%      |    7,477,442 |18 |

The ResNet ensemble mechanism significantly improves the average prediction performance and is able to generalise well as the models are getting higher accuracy on the validation set compared to the training set.

<img width="400" alt="Screen Shot 2022-03-10 at 18 16 39" src="https://user-images.githubusercontent.com/93217519/157771308-f8b4ce49-a6cc-4c13-b73d-21a41cec1298.png">
<img width="384" alt="Screen Shot 2022-03-10 at 18 10 09" src="https://user-images.githubusercontent.com/93217519/157770559-495d48a8-e8b4-4e00-96e9-c72b2f7c629a.png">


## Tensorboard
TensorBoard provides the visualization and tooling needed for machine learning experimentation:
- Tracking and visualizing metrics such as loss and accuracy
- Visualizing the model graph (ops and layers)
- Viewing histograms of weights, biases, or other tensors as they change over time

To view my interactive Tensorboard scan the QR code below or Click [here](https://tensorboard.dev/experiment/UVAwdGFwQA6JBWJPZEWLPQ/#scalars)

![qr-code](https://user-images.githubusercontent.com/93217519/157250970-69819cec-2024-4550-8f8d-8c3d13acfb17.png)

## Demo

https://user-images.githubusercontent.com/93217519/157778753-2d096604-97f9-4e89-ab0b-8c9da2b19983.mov

