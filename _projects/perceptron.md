---
layout: post
title: Perceptron Array
subtitle: Identifying Handwritten Digits
thumbnail: assets/images/projects/perceptron/perceptron_array.png
pdf: assets/images/projects/perceptron/HW1_Perceptrons.pdf
date: 2019-01-17
type: ml
---

An array of ten perceptrons designed to recognize handwritten digits from the MNIST
dataset. Each perceptron was assigned to recognize one of the digits from 0 to 9
and together they
could classify each digit by assigning the class from the most confident of the
ten perceptrons.

Perceptrons used the Perceptron Learning Algorithm and were tested with three
different learning rates. The different learning rates resulted in accuracies
from 87% to 89%. Some digits were identified up to 95% accurately, while others
only achieved accuracies between 82% and 85%. It was interesting to note the
pattern of misclassifications and speculate why some digits were misclassified
in certain ways. Specifically interesting was that misclassification was often
**not** reciprocal; for example, 5 was misclassified as 3 but not the other way
around.

### Language
- Python
  - numpy
  - matplotlib

[Full Report](/assets/images/projects/perceptron/HW1_Perceptrons.pdf)
