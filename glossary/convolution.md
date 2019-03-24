---
layout_: post
title:  "Convolutional Neural Network (CNN)"
date:   2019-03-24 12:58:29
categories_: jekyll update
---

# {{ page.title }}

A CNN apply a filter to ignore wast space on images = a way to condense images to better distinguish feature. By passing filters over an image 
to reduce the amount of information, they then allowed the [neural network](neural-network.html) to effectively extract features that can 
distinguish one class of image from another.

The concept of Convolutional Neural Networks is to add some layers to do convolution before you have the dense layers, and then the information 
going to the dense layers is more focussed, and possibly more accurate.

For example it can multiply 8 neighbours of a pixel by weights and sum 9 values as new pixel.

Used with the [pooling](pooling.html) which can be seen as a compression.

This is a really nice way to improve our image recognition performance: training take more time but decrease the loss and increase the accuracy.


## TensorFlow snippet

```py
model = tf.keras.models.Sequential([
  tf.keras.layers.Conv2D(64, (3, 3), activation='relu', input_shape=(28, 28, 1)), # see External below for API documentation
  tf.keras.layers.MaxPooling2D(2, 2),                                             # see External below for API documentation
  ...
]);
```


## Breadcrumb

- [Artificial intelligence](artificial-intelligence.html)
  - [Machine Learning](machine-learning.html)
    - [Neural network](neural-network.html)
      - [Deep learning](deep-learning.html)
        - Convolutional Neural Network
    - [Computer vision](computer-vision.html)
        - image recognition, 
        - segmentation, 
        - captioning, 
        - and object detection.


# See also

- [Neural Network](neural-network.html)
- [Pooling](pooling.html)


## External

- [(263) Convolutional Neural Networks (Course 4 of the Deep Learning Specialization) - YouTube](https://bit.ly/2UGa7uH)
- [Intuitively Understanding Convolutions for Deep Learning](https://towardsdatascience.com/intuitively-understanding-convolutions-for-deep-learning-1f6f42faee1)
- [tf.keras.layers.Conv2D | TensorFlow](https://www.tensorflow.org/versions/r1.8/api_docs/python/tf/keras/layers/Conv2D)
- [tf.layers.MaxPooling2D | TensorFlow](https://www.tensorflow.org/versions/r1.8/api_docs/python/tf/layers/MaxPooling2D)
- Coursera: 
Introduction to TensorFlow for Artificial Intelligence, Machine Learning, and Deep Learning:
  - [Enhancing Vision with Convolutional Neural Networks](https://www.coursera.org/learn/introduction-tensorflow/lecture/5bJjm/a-conversation-with-andrew-ng)
  - [Course 1 - Part 6 - Lesson 2 - Notebook.ipynb - Colaboratory](https://colab.research.google.com/github/lmoroney/dlaicourse/blob/master/Course%201%20-%20Part%206%20-%20Lesson%202%20-%20Notebook.ipynb)
  - [Image Filtering](https://lodev.org/cgtutor/filtering.html)

[< Home](..)
