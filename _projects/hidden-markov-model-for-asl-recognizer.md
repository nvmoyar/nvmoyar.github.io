---
title: American Sign Language Recognizer using Hidden Markov Models
layout: project_page
description: The main goal of this project is to build a word recognizer for some American Sign Language video sequences using hidden Markov models using features extracted from gestural measurements taken from videos frames collected for research (see the RWTH-BOSTON-104 Database).
project-link: "https://github.com/nvmoyar/aind1-recognizer"
project-image: "recognizer_screenshot.png"
project-category: "Speech Recognition"
project-tags:
 "Automatic-Speech-Recognition"
 "Hidden-Markov-Models"
---

#### PART 1: Extracting the features

A data handler has been designed for this database provided as AslDb class. This module creates the pandas dataframe from the corpus and dictionaries for extracting data [hmmlearn library](https://hmmlearn.readthedocs.io/en/latest/) format-friendly. Every video frame can be expressed with an id and its features. Features are the most relevant variables that will allow us to train the model. They can be raw measurements directly taken from the video frames or derived from them like normalize each speaker's range of motion with grouped statistics using Pandas stats functions and pandas groupby. 	

#### PART 2: Training the HMM Model: Finding the optimal hidden states

Once extracting the features, we need to train the model but the number of optimal hidden states is unknown. The purpose the model selection is to tune the number of states for each word HMM prior to testing on unseen data. Three methods are explored: Log-likelihood using cross-validation folds (CV), Bayesian Information Criterion (BIC), Discriminative Information Criterion (DIC). 

#### PART 3: Build the recognizer

Finally, we get a dict with all the unique words we are going to use for training, and a GaussianHMM object as value with a probability distribution given the word. This dict is going to be used on unseen data and try to predict sequences and calculate Word error rate (WER), the common metric of the performance of a speech recognition or machine translation system, given different features and selectors criterion chosen.    
