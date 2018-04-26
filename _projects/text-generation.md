---
title: Text Generation using Recurrent Neural Networks
layout: project_page
description:  In this project, a Recurrent Neural Network is created to generate a new script for the Simpsons TV series from the whole 'Simpsons by the data' dataset from Kaggle.
project-link: https://github.com/nvmoyar/dlnd-text-generation
project-image: text-generation_screenshot.png
project-category: Text Generation
project-tags:
 Word-embeddings
 Gradient-clipping
 LSTM
 TensorFlow
---

Recurrent Neural Networks are proven a good approach to deal with sequential data like time series or meaningful text. In this project, a new script for the Simpsons TV series is created from the 'Simpsons by the data' dataset from Kaggle. 

Initially, for this Udacity's project, only the graph built was trained only using all scenes at Moe's Tavern. However, for experimenting purposes, the whole dataset has been used for training in order to get a more sensical script. 

Unlike the Udacity's repo, in this project we find two Jupiter notebooks: 

* https://github.com/nvmoyar/dlnd-text-generation/simpsons_dataset_preparation.ipynb --> the additional operations to prepare a text with the whole The Simpsons Dataset from Kaggle. 
* https://github.com/nvmoyar/dlnd-text-generation/dlnd_tv_script_generation.ipynb --> the model, the training and the predicted script. 

We could visualize the input words passed as one-hot encoded vectors, and on this case, this might work if we are dealing with a small dataset, however, with a larger corpus, the dimensionality will be so huge that the computation could be unbearable. To deal with this high dimensionality problem, we would need a better vector representation for our words, since words that could be used in the same context should appear closer than unrelated words. This weight matrix is usually called the embedding matrix or embedding look-up table and Tensorflow provides a convenient function which does this lookup to get the embedding tensors. In this case, we build lookup tables for later use when creating the word embeddings. 

A tokenizer is needed in order to remove unnecessary marks. The Tokenizer function outputs a dictionary that will be used to token the symbols and add the delimiter (space) around it. This separates the symbols as it's own word, making it easier for the neural network to predict the next word. 

The final model is a stack of LSTM cells that will be fed in a custom length of batches of an embedding tensor randomly initialized between [-1, 1]. That means that additionally to the usual batch size, it is necessary to tune the length of the sequence of the batch jointly with the rest of hyperparameters. 

Besides, the neural network uses element-wise gradient clipping when it exceeds an absolute threshold. Although it introduces an additional hyperparameter, this parameter has not been exposed jointly with the rest of the hyperparameters to tune in this neural graph. Thresholds have been manually established in [-1., 1.]. 

The idea is to use the final graph to build a word picker function, that will be in charge of giving a word, find the probabilities of the next word, given a word set initially as a start of the sequence. 