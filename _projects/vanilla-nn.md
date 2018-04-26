---
title: A Neural Network for Bike Sharing prediction
layout: project_page
description: In this project, we build a neural network from scratch to carry out a prediction problem about daily bike rental ridership, on a real dataset.  By building a neural network from the ground up, we'll have a much better understanding of gradient descent, backpropagation, and other concepts that are important to know before we move to higher level tools such as Tensorflow. Some boilerplate code has been already provided, especially if we are not familiar enough with pandas. 
project-link: "https://github.com/nvmoyar/dlnd-your-first-neural-network"
project-image: "vanillann_screenshot.png"
project-category: Feed Forward
project-tags:
 Feed Forward Neural Network
---

In this project, we build a neural network from scratch to carry out a prediction problem about daily bike rental ridership, on a real dataset.  By building a neural network from the ground up, we'll have a much better understanding of gradient descent, backpropagation, and other concepts that are important to know before we move to higher level tools such as Tensorflow. Some boilerplate code has been already provided, especially if we are not familiar enough with pandas. 

In the first part of this notebook, we perform some data preprocessing. It is really worth to get used to pandas since it is an easy way to explore and transform data. Data preprocess in general might include transforming categorical data into binary dummy variables -such in this case-, [standarize, reescale][1] or [normalize][2] the continuous variables, etc. 

In the second part, we build the neural network model. This is a Vanilla or Feed Forward Network, which means that we need to implement by hand the forward pass, set hyperparameters -learning rate, number of hidden units, and number of training passes-. We will use the sigmoid function for activations. We use the weights to propagate signals forward from the input to the output layers in a neural network, and we use the weights to also propagate error backward from the output back into the network to update our weights during backpropagation. 

To tune, hyperparameters means to find a strategy that the keeps the error on the training set is low, but without overfitting to the data, which means that the model will be able to generalize over other data instead of being too specific to this problem. If we train the network too long or have too many hidden nodes -too much complexity-, it can become overly specific to the training set and will fail to generalize to the validation set. That is, the loss on the validation set will start increasing as the training set loss drops.

For this problem, we use Stochastic Gradient Descent (SGD) to train the network to do backpropagation. The idea is that for each training pass, you grab a random sample of the data instead of using the whole data set. We use many more training passes than with normal gradient descent, but each pass is much faster. This ends up training the network more efficiently. 

Eventually, we find that model is not learning well with the initially given hyperparameters as the validation loss is usually higher compared to the training loss. The accuracy might be improved increasing the epoch batches, however, many epochs lead the model to overfit as well -checked, over 3000 epoch, some values have been tested, adds too much complexity and the accuracy decreases, especially over 5000 epochs. The number of hidden nodes seems to be not very effective over 8 hidden nodes. The predicted model is not bad, however this model is fairly simple. We are using MSE as cost function, and we could improve it by adding L2 or Ridge  Regularization to prevent overfitting by penalizing large weights. 


* [1](http://sebastianraschka.com/Articles/2014_about_feature_scaling.html)
* [2](https://stats.stackexchange.com/questions/35591/normalization-vs-scaling)