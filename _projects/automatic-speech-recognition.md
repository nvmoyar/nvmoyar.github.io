---
title: Speech Recognition
layout: project_page
description: In this notebook, some different approaches are used to build the acoustic model for an end-to-end automatic speech recognition (ASR) pipeline. In addition to providing different architectures, the notebook provides a discussion based on the observations after comparing the different models. The third part includes a predicted transcription based on the probability distribution of the chosen acoustic models, output on the second part of the notebook.
project-link: https://github.com/nvmoyar/aind2-speech-recognition
project-image: ASR_screenshot.png
project-category: Speech-Recognition
project-tags:
 Automatic-Speech-Recognition
 CNN
 LSTM
 Bidirectional-RNN
 RNN
---

In this notebook, some different approaches are used to build the acoustic model for an end-to-end automatic speech recognition (ASR) pipeline:

* Model 0: RNN
* Model 1: RNN + TimeDistributed Dense
* Model 2: CNN + RNN + TimeDistributed Dense
* Model 3: Deeper RNN + TimeDistributed Dense
* Model 4: Bidirectional RNN + TimeDistributed Dense
* Model 5: CNN + Deep RNN + TimeDistributed Dense 
* Models Comparison and discussion of the models 1, 2, 3, 4 and 5
* Final Model: Dilated Convolution + Deep RNN + TimeDistributed Dense 
* Discussion of final model architecture 

The first part of this notebook investigates the [LibriSpeech](http://www.danielpovey.com/files/2015_icassp_librispeech.pdf), the dataset that will be used to train and evaluate this pipeline. The wav signal is preprocessed in order to obtain frequencies and MFCC features. The final discussion includes observations about using either tensor as input features for the pipeline. 

```sample_models.py``` module, includes code for all the models. Once this module is imported in the notebook, the different architectures are trained within the notebook. 

The second and longest part of the notebook includes discussion about the performance of all the models and compares results on using spectrogram or MFCC features.

The third part shows a predicted transcription based on the probability distribution of the chosen acoustic models, the output on the second part of the notebook. 