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


## Python

```py
import tensorflow as tf
import numpy as np
from tensorflow import keras

model = tf.keras.Sequential([keras.layers.Dense(units=1, input_shape=[1])])

model.compile(optimizer='sgd', loss='mean_squared_error')

xs = np.array([-1.0,  0.0, 1.0, 2.0, 3.0, 4.0], dtype=float)
ys = np.array([-3.0, -1.0, 1.0, 3.0, 5.0, 7.0], dtype=float)

model.fit(xs, ys, epochs=500)

print(model.predict([10.0]))
```