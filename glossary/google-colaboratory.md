---
layout_: post
title:  "Google Colaboratory"
categories: tool
---

# {{ page.title }}

![](https://colab.research.google.com/img/colab_favicon_256px.png)

- [https://colab.research.google.com](https://colab.research.google.com/)

> Colaboratory is a free Jupyter notebook environment that requires no setup and runs entirely in the cloud.
>  
>  With Colaboratory you can write and execute code, save and share your analyses, and access powerful computing resources, all for free from your browser.

- [Get started with Google Colaboratory (Coding TensorFlow) | Coursera](https://www.coursera.org/learn/introduction-tensorflow/ungradedWidget/O9WuE/get-started-with-google-colaboratory-coding-tensorflow)

[< Home](..)


## Features

### Upload files

- [Horse-or-Human-NoValidation.ipynb - Colaboratory](https://colab.research.google.com/github/lmoroney/dlaicourse/blob/master/Course%201%20-%20Part%208%20-%20Lesson%202%20-%20Notebook.ipynb#scrollTo=NR_M9nWN-K8B)

```python
# !wget --no-check-certificate \
#     https://storage.googleapis.com/laurencemoroney-blog.appspot.com/horse-or-human.zip \
#     -O /tmp/horse-or-human.zip
    
import os
import zipfile

local_zip = '/tmp/horse-or-human.zip'
zip_ref = zipfile.ZipFile(local_zip, 'r')
zip_ref.extractall('/tmp/horse-or-human')
zip_ref.close()

# Directory with our training horse pictures
train_horse_dir = os.path.join('/tmp/horse-or-human/horses')

# Directory with our training human pictures
train_human_dir = os.path.join('/tmp/horse-or-human/humans')
```