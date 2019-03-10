---
layout_: post
title:  "Normalize"
categories_: jekyll update
---

# {{ page.title }}

If we are training a [neural network](neural-network.html), for various reasons it's easier if we treat all values as between 0 and 1, a process called __normalizing__.

For example, in the case of [MNIST](mnist.html), the 128x128 pictures are greyscale: each pixel has a 0 to 255 value as greyscale. 
In this case, the images are normalized by dividing greyscales by 255.