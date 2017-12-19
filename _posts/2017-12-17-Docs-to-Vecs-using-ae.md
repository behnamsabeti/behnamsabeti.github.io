---
layout: post
title: Documents to Vectors using an Auto-Encoder 
---

<p style="text-align: justify;">Auto-Encoder is a neural network architecture, which tries to estimate distribution of data samples in a latent space. In this post, we will use this concept to convert a set of documents to fixed-length vectors. These vectors can then be used for any classification or clustering tasks. This post will cover the following:</p>
<ul style="text-align: justify;">
<li>what is an auto-encoder?</li>
<li>implement an auto-encoder with two LSTM networks</li>
<li>train the networks on amazon text data</li>
<li>use the generated model to extract representations for new documents</li>
</ul>
<p style="text-align: justify;">If you're not familiar with any of these concepts, don't worry! I wont get into details, it's just a practical post with no mathematics or proofs. I will use Keras library with Tensorflow Backend for implementation.</p>
<p style="text-align: justify;">Ok first things first, what is an auto-encoder?<br />Auto-Encoder consists of two parts: encoder and decoder. Each part is an arbitrary neural network:</p>
<ul style="text-align: justify;">
<li>Encoder: this network tries to trasnform input samples to a latent space</li>
<li>Decoder: this network tries to transform samples from latent space back into their original representation</li>
</ul>

![alt text]({{ site.baseurl }}/images/post_0/ae.jpg "Auto-Encoder Architecture")
*Auto-Encoder Architecture*

<p style="text-align: justify;">Auto-Encoder is a kind of compression algorithm, because it transforms each sample into a, usually lower dimension, latent space which contains all the information for decoder to decode it and construct the original sample. After training the Auto-Encoder on a large enough dataset, the model can be used to transform any sample to the latent space, which is our desired fixed-legnth vector.</p>

<p><strong>what is LSTM?</strong></p>
<p style="text-align: justify;">Long Short Term Memory or LSTM is a neural network which tries to model sequences. This model takes into account long dependencies between elements in a sequence, and avoids problems like gradient vanishing in vanilla RNNs.&nbsp;There is a great blog <a href="http://colah.github.io/posts/2015-08-Understanding-LSTMs/">post</a> by <a href="http://colah.github.io/about.html">Christopher Olah</a> on LSTM, if you want to know the details. We will use two LSTM networks as the encoder and decoder parts of our Auto-Encoder.</p>

![alt text]({{ site.baseurl }}/images/post_0/lstm.jpg "LSTM Architecture")
*Long Short Term Memory (LSTM) Architecture*

<p><strong>Fixed-length documents</strong></p>
<p style="text-align: justify;">In order to feed documents to the auto-encoder, we need to specify a fixed-length for the sequences. This way each input will have a specific size. To this end we will use padding elements, which will be used to increse length for documents which have a lower length than the sepecifeid one. Documents with higher length will be cut-off to match the desired length.</p>
<p><strong>Data Preparation</strong></p>
<p style="text-align: justify;">We need to have a machanism to encode words as vectors, because computer does not understand a String! Word embedding is the way to do that. There are some models like <a href="https://arxiv.org/abs/1301.3781">word2vec</a> and <a href="https://nlp.stanford.edu/projects/glove/">GloVec</a> which are pre-trained on huge corpora and can be used to generate a fixed-length vector for each word. We will use GloVec model to transform each word to a vector. These vactors are then concatenated together to form a 2D vector for each document. All documents are converted to these 2D vectors and form our training data. After training we will have a 1D vector representation for each document which is generated with respect to all other documents and, hopefully, encodes semantics. The code for loading and using GloVec model is:</p>
<p><strong>Model</strong></p>
<p>I used Keras Library with Tensorflow backend for implementation. Keras makes it really easy to create deep learning models. The following code generates an Auto-Encoder with 2 LSTM networks.</p>
<script src="https://gist.github.com/behnamsabeti/001f38927628d6cdc65eaa7f7df6e116.js"></script>
<p>Model parameters are:</p>
<script 
src="https://gist.github.com/behnamsabeti/b4ea7fa51383050287c0d3854fe51fd4.js"></script>
<p><strong>Train</strong></p>
<p>Ok, that's it! We now have the model and data prepared for training. Keras makes it really easy to train the model, and also saves the best model in the training process to be used later. The trainig code is:</p>
<script src="https://gist.github.com/behnamsabeti/13c438761ef6ce862e818eb8d8c20a97.js"></script>
<p><strong>Using the Model</strong></p>
<p>All we did to this point was to create a model which can convert each document to a fixed-length vector, and we have that now! All you need to do is to convert your document to a 2D vector using the same code for data preparation and feed it to the trained model. After that you get the middle weights and walah you have the vectorized representation of your documents. The following code shows how to do this:</p>
<p><strong>Conclusion</strong></p>
<p>In this post we used an Auto-Encoder architectue with 2 LSTM networks as encoder and decoder in order to convert documents to fixed-length vectors. This tool will come handy when you have a text classification or clustering task. You can use this instead of what we call feature engineering and feature extraction which are exhastive tasks themselves. In the next post i will show you how to build a fairly accurate sentiment analysis model based on this post. The Code for this post is available in github, which is fully commented. If you have any comments or questions just drop a comment and we will learn more together.&nbsp;</p>
<p>&nbsp;</p>





