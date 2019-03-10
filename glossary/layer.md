---
layout_: post
title:  "Layer"
categories_: jekyll update
---

# {{ page.title }}

The core building block of [neural networks](neural-network.html) is the layer, a data-processing module that you can think of 
as a tunable function from tensors to tensors.

Rules of thumb:

- the first layer in your network should be the same shape as your data
  - In Python with [TensorFlow](tensorflow.html) you can use the method `tf.keras.layers.Flatten()` to convert a MxN-resolution image into a (MxN)x1 input layer)
- the number of neurons in the last layer should match the number of classes you are classifying for
- if the input data are simple, additional layers there isn't a significant impact 

[< Home](..)