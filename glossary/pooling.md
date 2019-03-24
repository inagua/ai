---
layout_: post
title:  "Pooling"
date:   2019-03-24 12:58:29
categories_: jekyll update
---

# {{ page.title }}

Used in a [Convolutional Neural Network](convolution.html), the [pooling](pooling.html) compresses the information to make it more manageable. 

For example it takes max of each 4 neighbour pixels as new pixel: in this case the effect is to __quarter__ the size of the image
(halves the number of horizontal, and halves the number of vertical pixels).


## TensorFlow snippet

```py
model = tf.keras.models.Sequential([
  tf.keras.layers.Conv2D(64, (3, 3), activation='relu', input_shape=(28, 28, 1)), # see External below for API documentation
  tf.keras.layers.MaxPooling2D(2, 2),                                             # see External below for API documentation
  ...
]);
```


# See also

- [Convolutional Neural Network](convolution.html)

## External

- [(263) Convolutional Neural Networks (Course 4 of the Deep Learning Specialization) - YouTube](https://bit.ly/2UGa7uH)
- [tf.keras.layers.Conv2D | TensorFlow](https://www.tensorflow.org/versions/r1.8/api_docs/python/tf/keras/layers/Conv2D)
- [tf.layers.MaxPooling2D | TensorFlow](https://www.tensorflow.org/versions/r1.8/api_docs/python/tf/layers/MaxPooling2D)


[< Home](..)
