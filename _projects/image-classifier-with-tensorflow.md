---
title: An image classifier for CIFAR-10 dataset
layout: project_page
description: In this project, a Convolutional Neural Network is built to classify a subset of the CIFAR-10 dataset. This is a classic multiclass classification problem that illustrates Supervised Learning in action.  
project-link: https://github.com/nvmoyar/dlnd-cnn-image-classifier
project-image: cifar-10-image-classifier_screenshot.png
project-category: Image Classifier
project-tools: Jupyter Notebooks, Numpy, Pandas, SciKit-Learn, TensorFlow, CIFAR-10 Dataset, AWS Deep Learning AMI with Source Code (CUDA 8, Ubuntu)
project-tags:
 CNN
 TensorFlow
---

In this project, a Convolutional Neural Network is built to classify a subset of the CIFAR-10 dataset. This is a classic multiclass classification problem that illustrates Supervised Learning. This dataset consists of airplanes, dogs, cats, and other objects that will be labeled from 0 to 9 by using the LabelBinarizer function of Sckikit-Learn in a pre-process function, therefore we get a One-Hot encoded Numpy array with targets/labels for each input image. The images need only to be rescaled, getting a 3D input tensor or cube of numbers between [0, 1]. 

This CNN model takes a batch of images and labels to output the logits, and it consists of a stack of: 

* Some Convolution layers and Max Pooling layers to reduce dimensionality preserving the spatial integrity, getting a 4D tensor.

* A Flatten layer that will process the 4D tensor output of the previous stack of layers, to output a 2D tensor.

* Some Fully Connected connected layers. Since we are using the tf.nn module -low abstraction level API- instead of tf.layers -high abstraction level API-, the operations performed at this layer are manually defined. This way we can expressly set weights initialized to random normal rather than random distribution, etc. For this reason, a different Fully Connected layer called Output layer is needed to reduce dimensionality to the number of classes needed for this problem. Please notice that Dropout layers are used to prevent overfitting, and the keep probability has been defined as a 0D Tensor or Scalar. 

* Output layer, the last used Fully Connected layer needed to reduce the dimensionality of the convoluted data to the classes that need to be classified. 

After tuning this model, and training it on this subset of CIFAR-10, we get a ~70% accuracy, which makes that more the predictions are likely, still, it is not a great classifier depending on the final use, but it supposes a great introduction to hands-on on Supervised Learning. 