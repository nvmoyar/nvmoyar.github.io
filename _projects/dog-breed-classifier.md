---
title: Dog Breed Classifier
layout: project_page
description: In this project, we build a pipeline that can be used within a web or mobile app to process real-world, user-supplied images. Given an image, the algorithm will be able to detect if there is a human face in it or a dog image and it will return an estimate of the canine’s breed if a dog image is provided, and if an image of a human is provided, it will return the most resembling dog breed.
project-link: https://github.com/nvmoyar/aind2-dog-breed-classifier
project-image: dog-breed-classifier_screenshot.png
project-category: Image Classifier
project-tags:
 CNN
 Transfer-Learning
 VGGx
 ResNet
 Bottleneck-features
 Haar-cascades
 Keras
---

### Part 1: Image dectector

In this project, we build a pipeline that can be used within a web or mobile app to process real-world, user-supplied images. Given an image, the algorithm will be able to detect if there is a human face in it using OpenCV's implementation of Haar feature-based cascade classifiers. At this point, we need to make the first user experience decision about whether or not notify the user to provide only clear human images, since Haar cascades are good for generic and static objects, and these kind of classifiers are weak detecting variations of that object. A little discussion of this topic is provided in the notebook. 

Right after we proceed to use a pre-trained ResNet-50 model to detect dogs in images using ImageNet. Since this dataset is very large and the categories corresponding to dogs appear in an uninterrupted sequence and correspond to dictionary keys 151-268, some computation can be saved by returning the probability vector for the categories related to dog breeds on ImageNet. This way we can build a 'cheap' dog detector in the same way we built a 'human detector' with Haar cascades on the first part. 

### Part 2: Dog breed classifier using Keras 

The next step of the project is to build a dog breed classifier using a deep learning approach getting at least 1% of accuracy. The purpose of this model will be to build an algorithm that given an image of a dog, it identifies an estimate of the canine’s breed, and   if an image of a human is provided, the code will detect if there is a human face in the picture and will return the most resembling dog breed.   

A CNN is architecture using Keras is proposed, and its parameters used, are discussed. The final proposal uses **dropouts** to prevent overfitting, **Global Average Pooling** layers to reduce dimensionality and **Batch Normalization**. In order to improve the accuracy, **Data Augmentation** has been proven as worthy. Once the model was validated relatively quickly, Data augmentation has been demonstrated as an absolute performance enhancer achieving an accuracy of 26.1962% on the test set. 

### Part 3: Transfer learning

On this part, we use [bottleneck features](https://blog.keras.io/building-powerful-image-classification-models-using-very-little-data.html) to save time on computation. Since we are working with Keras bottleneck features, that means that we are working with the last activation maps before the fully-connected layers, thus we need to add the fully connected layers. A little experiment and discussion are provided, and InceptionV3 and ResNet-50 comparison are provided. 

### Part 4: Write a custom algorithm

For the last part of this notebook, we build a complete algorithm using the detectors and model written in the previous parts, and we use it to test not previously seen data of dogs and human faces to guess the dog breed or the resembling dog breed. 