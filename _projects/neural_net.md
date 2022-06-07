---
layout: post
title: Two-Layer Neural Network
subtitle: Experiment Design, Network Design and Hyperparameter Tuning
thumbnail: assets/images/projects/neural_net/neural_net.png
pdf: assets/images/projects/neural_net/HW2_Neural_Networks.pdf
date: 2019-03-09
type: ml
---

A two-layer neural network was implemented to classify handwritten digits from
the MNIST dataset. The task was then run while varying:
- the number of hidden units
- the momentum value
- the size of the training dataset
The effects of the various changes on performance were evaluated.
<!--
A two-layer neural network with up to 100 nodes was implemented to classify
handwritten digits from the MNIST dataset. The task was run with several
combinations of different experiment design, network design, and hyperparameter
values and their performances compared in order to evaluate the effects of the
various changes.
-->
<!--
Several versions of a two-layer neural network were implemented and their
performances compared in order to evaluate the effects of varying design
decisions. 
-->
Three rounds of comparisons were made. In the first round the number
of hidden units varied, in the second round the momentum value varied, and in
the final round the size of the training data varied. The task was to classify
handwritten digits from the MNIST dataset.

The effects within each round were compared, but effects between rounds were not
suitable for comparison because changing multiple variables means that it would
be difficult to isolate the cause of the change in performance and attribute it
to a specific design change.

### Method
I implemented a two-layer neural network that used back-propagation with
stochastic gradient descent  as its learning algorithm. Each neural unit used a
sigmoid activation function. The default parameters for the network were:
- hidden units = 100
- momentum &alpha; = 0.9
- learning rate &eta; = 0.1
- training data = 60,000 examples
- training duration = 50 epochs 

In each round of evaluation one parameter was changed while the rest were left
as their default values. Models were evaluated
when varying:
- number of hidden units to 10, 20, 100
- momentum to 0.0, 0.5, 1.0
- size of the training data to 15k, 30k, 60k

### Results
It turns out that the problem may have been too easy since there was little
appreciable difference in the performance of models with different parameters.
Changing the number of hidden units and changing the momentum value both showed
very little change in performance. Changing the amount of training data reduced
accuracy only slightly and delayed the model from achieving its maximum accuracy
for only a few epochs.

See the [full report](/assets/images/projects/neural_net/HW2_Neural_Networks.pdf)
for more details.


### Language
- Python
  - numpy

