---
layout_: post
title:  "TensorFlow"
categories: tool
---

# {{ page.title }}

![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/TensorFlowLogo.svg/220px-TensorFlowLogo.svg.png)

- https://www.tensorflow.org/

> TensorFlow is an end-to-end open source platform for machine learning. It has a comprehensive, flexible ecosystem of tools, 
> libraries and community resources that lets researchers push the state-of-the-art in ML and developers easily build and deploy 
> ML powered applications

One of the most important features of TensorFlow is that we can save the trained model as a binary file.

The reason why TensorFlow is good at creating [neural networks](neural-network.html) is that it doesn’t actually create a neural network from scratch. 
Instead, it retrains an existing [classifier](classifier.html) called [Inception](inception.html).

compile / optimizer=sgd (stochastic gradient descent) loss=mwan_squared_error

__TensorFlow__ can be used with [Keras](keras.html).

See also [TensorFlow.js](https://www.tensorflow.org/js) include:
- Core API ~ TensorFlow
- Layers API ~ Keras 
- with import/export models with them
