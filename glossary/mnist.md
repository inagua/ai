---
layout_: post
title:  "MNIST"
date:   2014-10-18 12:58:29
categories_: jekyll update
---

# {{ page.title }}

### _Modified National Institute of Standards and Technology_ database

It is a famous category of exercise in [computer vision](computer-vision.html).

![](../resources/images/mnist-fashion.png)

> The MNIST database (Modified National Institute of Standards and Technology database) is a large database of handwritten digits 
> that is commonly used for training various image processing systems

- [https://en.wikipedia.org/wiki/MNIST_database](https://en.wikipedia.org/wiki/MNIST_database)


The data can be found from the [Kerias](keras.html) framwork:

```py
fashion_mnist = keras.datasets.fashion_mnist
(train_images, train_labels), (test_images, test_labels) = fashion_mnist.load_data()
```

### See also

- [Normalizing](normalize.html) 

[< Home](..)