---
layout_: post
title:  "TensorFlow"
categories: tool
---

# {{ page.title }}

![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/TensorFlowLogo.svg/220px-TensorFlowLogo.svg.png)

- [https://www.tensorflow.org](https://www.tensorflow.org)
- [http://playground.tensorflow.org](http://playground.tensorflow.org)

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

- [The Hello World of Deep Learning with Neural Networks](https://colab.research.google.com/github/lmoroney/dlaicourse/blob/master/Course%201%20-%20Part%202%20-%20Lesson%202%20-%20Notebook.ipynb#scrollTo=oxNzL4lS2Gui) - Google Colab
- You can use [Google Colab](google-colaboratory.html) to write and run Python code on from the cloud.

```py
import tensorflow as tf
import numpy as np
from tensorflow import keras

# Create the simplest possible neural network:
#  - as a sequence
#  - of 1 Dense layer (aka connected neurons)
#  - having 1 neuron, 
#  - and the input shape to it is just 1 value.
model = keras.Sequential([keras.layers.Dense(units=1, input_shape=[1])])

# Compile the neural network with 2 functions
#  - The *optimizer* to make another guess ('Stochastic Gradient Descent' here)
#  - The *loss* function measures how well or badly the guessed answers is against the known correct answers
model.compile(optimizer='sgd', loss='mean_squared_error')

xs = np.array([-1.0,  0.0, 1.0, 2.0, 3.0, 4.0], dtype=float)
ys = np.array([-3.0, -1.0, 1.0, 3.0, 5.0, 7.0], dtype=float)

# Train the neural network
model.fit(xs, ys, epochs=500)

print(model.predict([10.0]))
```

### MNIST - Computer vision problem

See [MNIST](mnist.html)

```py
import tensorflow as tf
print(tf.__version__)

mnist = tf.keras.datasets.fashion_mnist

(training_images, training_labels), (test_images, test_labels) = mnist.load_data()

import matplotlib.pyplot as plt
plt.imshow(training_images[10])
print(training_labels[10])
print(training_images[10])

training_images  = training_images / 255.0
test_images = test_images / 255.0

model = tf.keras.models.Sequential([tf.keras.layers.Flatten(), 
                                    tf.keras.layers.Dense(128, activation=tf.nn.relu), 
                                    tf.keras.layers.Dense(10, activation=tf.nn.softmax)])

model.compile(optimizer = tf.train.AdamOptimizer(),
              loss = 'sparse_categorical_crossentropy',
              metrics=['accuracy'])

model.fit(training_images, training_labels, epochs=5)

model.evaluate(test_images, test_labels)
```

- `classifications = model.predict(test_images)` ==> classifications[0] is a N probabilities array (for N labelled classes), each ones are the proba that the input match the i-th class
- What's the impact if increase to 1024 Neurons? ==> Training takes longer, but is more accurate
- What would happen if you remove the Flatten() layer. Why do you think that's the case? ==> error as input layer dimension different then inputs dimension
- Consider the final (output) layers. Why are there 10 of them? What would happen if you had a different amount than 10? For example 5? ==> error as different than class count
- Consider the effects of additional layers in the network. What will happen if you add another layer between the one with 512 and the final layer with 10? ==> no impact as simple data 
- Consider the impact of training for more or less epochs. Why do you think that would be the case? ==> better loss, mode times
- Before you trained, you normalized the data, going from values that were 0-255 to values that were 0-1. What would be the impact of removing that? ==> Bad loss
- Trained for extra epochs might have taken a bit of time but for what? (if 95% accuracy after 3 epochs is enough why wait for more epochs ? How would you fix that? ==> callbacks


### Callback to stop training

Called a the end of each epoch (each epoch is fully played):

```py

class myCallback(tf.keras.callbacks.Callback):
  def on_epoch_end(self, epoch, logs={}):
    if(logs.get('acc')>0.6):
      print("\nReached 60% accuracy so cancelling training!")
      self.model.stop_training = True

callbacks = myCallback()

...

# model.fit(training_images, training_labels, epochs=5)
model.fit(training_images, training_labels, epochs=5, callbacks=[callbacks])

```


### Convolution 

- [Course 1 - Part 6 - Lesson 2 - Notebook.ipynb - Colaboratory | Coursera](https://colab.research.google.com/github/lmoroney/dlaicourse/blob/master/Course%201%20-%20Part%206%20-%20Lesson%202%20-%20Notebook.ipynb#scrollTo=SS_W_INc_kJQ)

```py
import tensorflow as tf
print(tf.__version__)
mnist = tf.keras.datasets.fashion_mnist
(training_images, training_labels), (test_images, test_labels) = mnist.load_data()
training_images=training_images.reshape(60000, 28, 28, 1)
training_images=training_images / 255.0
test_images = test_images.reshape(10000, 28, 28, 1)
test_images=test_images/255.0
model = tf.keras.models.Sequential([
  tf.keras.layers.Conv2D(64, (3,3), activation='relu', input_shape=(28, 28, 1)),
  tf.keras.layers.MaxPooling2D(2, 2),
  tf.keras.layers.Conv2D(64, (3,3), activation='relu'),
  tf.keras.layers.MaxPooling2D(2,2),
  tf.keras.layers.Flatten(),
  tf.keras.layers.Dense(128, activation='relu'),
  tf.keras.layers.Dense(10, activation='softmax')
])
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])
model.summary()
model.fit(training_images, training_labels, epochs=5)
test_loss = model.evaluate(test_images, test_labels)
```

- __Change the 32s__ to either 16 or 64 convolutions. What impact will this have on accuracy and/or training time?
- __Remove the final Convolution__. What impact will this have on accuracy or training time?
- How about __adding more Convolutions__? What impact do you think this will have? Experiment with it.
- __Remove all Convolutions but the first__. What impact do you think this will have? Experiment with it. 
- In the previous lesson you __implemented a callback__ to check on the loss function and to cancel training once it hit a certain amount. See if you can implement that here!

Visualizing the Convolutions and Pooling:

```python
print(test_labels[:100])             # shows the first 100 labels in the test set

import matplotlib.pyplot as plt
f, axarr = plt.subplots(3,4)
FIRST_IMAGE=0
SECOND_IMAGE=7
THIRD_IMAGE=26
CONVOLUTION_NUMBER = 1
from tensorflow.keras import models
layer_outputs = [layer.output for layer in model.layers]
activation_model = tf.keras.models.Model(inputs = model.input, outputs = layer_outputs)
for x in range(0,4):
  f1 = activation_model.predict(test_images[FIRST_IMAGE].reshape(1, 28, 28, 1))[x]
  axarr[0,x].imshow(f1[0, : , :, CONVOLUTION_NUMBER], cmap='inferno')
  axarr[0,x].grid(False)
  f2 = activation_model.predict(test_images[SECOND_IMAGE].reshape(1, 28, 28, 1))[x]
  axarr[1,x].imshow(f2[0, : , :, CONVOLUTION_NUMBER], cmap='inferno')
  axarr[1,x].grid(False)
  f3 = activation_model.predict(test_images[THIRD_IMAGE].reshape(1, 28, 28, 1))[x]
  axarr[2,x].imshow(f3[0, : , :, CONVOLUTION_NUMBER], cmap='inferno')
  axarr[2,x].grid(False)
```

## See also

- [Epoch](epoch.html) 
- [Loss function](loss.html) 
- [Optimizer](optimizer.html)

[< Home](..)