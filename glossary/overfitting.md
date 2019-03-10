---
layout_: post
title:  "Overfitting"
categories_: jekyll update
---

# {{ page.title }}

When a model is fit to the training data in such a way that the model has sufficient capacity to memorize the training data, 
we see the training loss continue to go down, but the testing or validation loss starts to rise. Models with this property begin 
to lose their ability to generalize and only perform well on the exact samples in the training data. We say models in this circumstance 
are overfit.

That can occur when there are too many [epochs](epoch.html) during the training.

[Home](..)