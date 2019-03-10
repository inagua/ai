---
layout_: post
title:  "Tensor"
categories_: jekyll update
---

# {{ page.title }}

At its core, a __tensor__ is a container for data — almost always numerical data. 

So it can be thought of as a container for numbers, as a n-dimensional grid where each position in the grid holds exactly one element. 
You may already be familiar with vectors and matrices, which are 1D and 2D tensors, respectively: 
tensors are a generalization of matrices to an arbitrary number of dimensions. The number of dimensions and size of each dimension is called the tensor's __shape__. 

For instance:
- a 3 x 4 matrix is a tensor with shape [3, 4]
- A vector of length 10 is a 1D tensor with shape [10]

Each tensor instance holds only one type of element. They are designed this way because it allows for convenient, highly efficient implementations of common operations 
necessary for [deep learning](deep-learning.html) (for instance, matrix dot- products).


## See also

- [Layer](layer.html) 


[< Home](..)
