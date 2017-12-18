---
layout: post
title: Convert Documents to Vectors using an Auto-Encoder and build a Sentiment Analysis model
---

Auto-Encoder is a neural network architecture, which tries to extract features from data samples. In this post, we will use this concept to convert a set of documents to fixed-length vectors. These vectors can then be used for any classification or clustering tasks. This post will cover the following:

	* what is an auto-encoder?
	* implement an auto-encoder with two LSTM networks
	* train the networks on amazon data
	* use the generated vectors to build a sentiment analysis model
	* evaluate the generated model

If you're not familiar with any of these concepts, don't worry! I will try to explain every thing from scratch.

Ok first things first, what is an auto-encoder?
Auto-Encoder consists of two parts: encoder and decoder. Each part is an arbitrary neural network:

	* Encoder: this network tries to trasnform input samples to a latent space
	* Decoder: this network tries to transform samples from latent space back into their original representation

![alt text](https://github.com/behnamsabeti/behnamsabeti.github.io/blob/master/images/post_0/ae.jpg "Auto-Encoder Architecture")

Auto-Encoder is a kind of compression algorithm, because it transforms each sample into a, usually lower dimension, latent space which contains all the information for decoder to decode it and construct the original sample. After training the Auto-Encoder on a large enough dataset, the model can be used to transform any sample to the latent space, which is our desired fixed-legnth vector.

	