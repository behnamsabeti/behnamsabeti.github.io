---
layout: post
title: Documents to Vectors using an Auto-Encoder 
---

<p style="text-align: justify;">Auto-Encoder is a neural network architecture, which tries to extract features from data samples. In this post, we will use this concept to convert a set of documents to fixed-length vectors. These vectors can then be used for any classification or clustering tasks. This post will cover the following:</p>
<ul style="text-align: justify;">
<li>what is an auto-encoder?</li>
<li>implement an auto-encoder with two LSTM networks</li>
<li>train the networks on amazon data</li>
<li>use the generated vectors to build a sentiment analysis model</li>
<li>evaluate the generated model</li>
</ul>
<p style="text-align: justify;">If you're not familiar with any of these concepts, don't worry! I will try to explain every thing from scratch.</p>
<p style="text-align: justify;">Ok first things first, what is an auto-encoder?<br />Auto-Encoder consists of two parts: encoder and decoder. Each part is an arbitrary neural network:</p>
<ul style="text-align: justify;">
<li>Encoder: this network tries to trasnform input samples to a latent space</li>
<li>Decoder: this network tries to transform samples from latent space back into their original representation</li>
</ul>

![alt text]({{ site.baseurl }}/images/post_0/ae.jpg "Auto-Encoder Architecture")

<p style="text-align: justify;">Auto-Encoder is a kind of compression algorithm, because it transforms each sample into a, usually lower dimension, latent space which contains all the information for decoder to decode it and construct the original sample. After training the Auto-Encoder on a large enough dataset, the model can be used to transform any sample to the latent space, which is our desired fixed-legnth vector.</p>

<p>The following code builds our model:</p>
<script src="https://gist.github.com/behnamsabeti/001f38927628d6cdc65eaa7f7df6e116.js"></script>
<p>Model parameters are:</p>
<script src="https://gist.github.com/behnamsabeti/b4ea7fa51383050287c0d3854fe51fd4.js"></script>
<p>And finally the following code trains the model and saves the best one:</p>
<script src="https://gist.github.com/behnamsabeti/13c438761ef6ce862e818eb8d8c20a97.js"></script>

