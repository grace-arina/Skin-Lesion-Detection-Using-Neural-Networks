# Skin-Lesion-Detection-Using-Neural-Networks
In cancer, there are over 200 different forms. Out of 200, melanoma is the deadliest form of skin cancer. Among all the skin cancer type, melanoma is the least common skin cancer, but it is responsible for 75% of death. Melanoma skin cancer is highly curable if it gets identified at the early stages. The first step of Melanoma skin cancer diagnosis is to conduct a visual examination of the skin's affected area. This project aims to build an automated classification system based on image processing techniques to classify skin cancer using skin lesions images. The approach uses Convolutional Neural Network (CNN) to perform a binary classification from outlier lesions images. This reduction of a gap has the opportunity to impact millions of people positively.

## Dataset
The project dataset is openly available on Kaggle(https://www.kaggle.com/drscarlat/melanoma).

#### Sample Images from the Dataset:

-The images below are labelled as Melanoma in the dataset.

-The images below are labelled as NotMelanoma in the dataset.



## Data Preprocessing

In any machine learning project, it is critical to set up a trustworthy validation scheme, in order to properly evaluate and compare models. This is especially true if the dataset is small which is the case of this project.

For a typical image classification problem, the standard approach is to take a deep CNN model (such as the most popular EffcientNet) trained on ImageNet, replace the last layer so that the output dimension equals the target's dimension, and fine tune it on the specific dataset.

The target to predict in this year's (2020) competition is binary-benign (i.e. no melanoma) or malignant (i.e. melanoma). We noticed that the target information is included in the diagnosis column: target is malignant if and only if diagnosis is melanoma.

## Data Augmentation

In a small size dataset, image augmentation is required to avoid overfitting the training dataset. The augmentation that helps to improve the prediction accuracy of the model is selected. The selected augmentation are as follows:
- **Rotation:** rotates the image by a specified degree.
- **Shearing:** shifts one part of the image like a parallelogram

### Network Configurations
I used ensemble terminology to train diverse models. The model configuration is as follows:

1. **Pretrained CNN Models:** I chose to use Efficent Net B4 AND ResNet 50 as they achieved higher accuracy on ImageNet competition
2. Targets: The models are trained 10682 images belonging to two classes 
3. Resized input image sizes to 224x224 pixels to lower resolution due to GPU memory constraints
4. **Optimizer**: *Adam*. As we have sparse data, Adam is used because of the adaptive learning rate.

### Results
| Models        | Test Accuracy  |  # Trainable Params |
| ------------- |:-------------:| -----:|
| Baseline      | 82.83% | 1,625,026 | 
| Efficent Net B4      | 81.24%     |   5,619,906 |
| Efficient Net B4 (1 trainable layer) | 90.96%      | 5,619,906 |
| Efficeint Net B4 (3 trainable layer) | 92.59%      | 6,426,306 |
| ResNet 50  | 93.23%      |    6,422,722 |
| ResNet 50 (3 trainable layers) | 93.91%      |    6,426,818 |
| ResNet 50 (5 trainable layers) | 93.29%      |    7,477,442 |

## Tensorboard
TensorBoard provides the visualization and tooling needed for machine learning experimentation:
- Tracking and visualizing metrics such as loss and accuracy
- Visualizing the model graph (ops and layers)
- Viewing histograms of weights, biases, or other tensors as they change over time

To view my interactive Tensorboard scan the QR code below or Click [here](https://tensorboard.dev/experiment/UVAwdGFwQA6JBWJPZEWLPQ/#scalars)

![qr-code](https://user-images.githubusercontent.com/93217519/157250970-69819cec-2024-4550-8f8d-8c3d13acfb17.png)

