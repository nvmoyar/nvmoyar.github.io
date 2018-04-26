---
title: Neural Machine Translation
layout: project_page
description: In this project a sequence to sequence model is trained on a custom small dataset of English and French sentences in order to translate new sentences from English to French using TensorFlow.  
project-link: https://github.com/nvmoyar/dlnd-lstm-language-translation
project-image: language-translation_screenshot.png
project-category: Text Generation
project-tags:
 Seq-2-Seq
 Neural-Machine-Translation
 Word-embeddings
 Gradient-clipping
 LSTM
 TensorFlow
---

In this project, a Neural Machine Translation is performed to translate sentences from English to French using a [Seq-2-Seq model](https://github.com/google/seq2seq/blob/master/docs/nmt.md) using [Tensorflow](www.tensorflow.org/tutorials/seq2seq). The model is trained on a custom small dataset of English and French sentences in order to later perform translation of new sentences, from English to French. 

The dataset consists of a small set of plain text with files corresponding to source sentences and target translations, aligned line-by-line: 

Input sequence (ENG): new jersey is sometimes quiet during autumn , and it is snowy in april .
Target sequence (FR): new jersey est parfois calme pendant l' automne , et il est neigeux en avril .

A preprocessing function is needed in order to tally the input sequence, by adding 'End of sentence' tag to the targets. Additionally, it is necessary also to control the 'End of input sequence', in this case by adding 'GO' tag at the beginning of each batch within the decoding layer. 

After creating the preprocess functions needed, the encoding and decoding layers are created by using the low-level of abstraction API, in Tensorflow. The encoder layer consists of a multi-stack of LSTM cells to prevent vanishing gradients, and dropouts to prevent overfitting. The decoding layer is more complex instead since it is formed by two main layers with a different purpose: allow the model to get the train logits from one side,  and the inference logits. The training process gives as an output a probability of distribution over words considering context. However we are more interested in applying this prob distribution on unseen sequential data -a new sentence-, thus [inference](https://www.tensorflow.org/tutorials/seq2seq#inference_how_to_generate_translations) over data. To build this two layers, we have available the [Seq-2-seq library](https://www.tensorflow.org/api_guides/python/contrib.seq2seq) in TensorFlow, which use the tf.contrib module, a high-abstraction API which functions are eventually merged into TF core. Therefore the layer for our decoder is composed by a stack of LSTM cells, the decoding layer for training, the decoding layer for inference, and since there are variable shared among training and inference processes, we use a context manager available in TF. 

We could visualize the input words passed as one-hot encoded vectors, and on this case, this might work since we are dealing with a small dataset, however, with a larger corpus, the dimensionality will be so huge that the computation could be unbearable. To deal with this high dimensionality problem, we would need a better vector representation for our words, since words that could be used in the same context should appear closer than unrelated words. This weight matrix is usually called the embedding matrix or embedding look-up table and Tensorflow provides a convenient function which does this lookup to get the embedding tensors. 

This network uses element-wise gradient clipping when it exceeds an absolute threshold. Although it introduces an additional hyperparameter, this parameter has not been exposed jointly with the rest of the hyperparameters to tune in this neural graph. Thresholds have been manually established in [-1., 1.]. 

Finally, we train, save the model, and after pre-process a testing sentence, we are able to do inference and get a translation of a new small sequence of words. 