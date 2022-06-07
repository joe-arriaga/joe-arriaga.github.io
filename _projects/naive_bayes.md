---
layout: post
title: Naive Bayes
subtitle: Building a Better Spam Filter?
thumbnail: assets/images/projects/naive_bayes/spam_folder.png
pdf: assets/images/projects/naive_bayes/HW4_Naive_Bayes.pdf
date: 2019-03-19
type: ml
---

Classify spam vs. legitimate email using a Naive Bayes classifier with Gaussian
probability distribution.

#### Note
In this project the majority of the work was done by using numpy functions and a
hand-rolled probability density function. A pre-packaged model from scikit-learn
was *not* used.

#### Further Explanation
Naive Bayes classification differs from many machine learning algorithms in that
it does not use an iterative process (like a neural network). Instead, the
classification is based on the static statistical properties of the data set.
> By "data set" here, I mean:
> 1. Training Data
> 2. Testing Data
>   - New examples encountered during deployment to be classified
The functionality of the algorithm comes from calculating the mean and standard
deviation of the various classes and then using the chosen probability
distribution to calculate the most likely class for each example to be
classified.


### Language
- Python

### Tools
- numpy
- matplotlib
- utility functions from scikit-learn
  - the functionality of the algorithm was implemented by hand

[Full Report](/assets/images/projects/naive_bayes/HW4_Naive_Bayes.pdf)

