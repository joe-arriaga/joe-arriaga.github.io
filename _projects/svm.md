---
layout: post
title: SVM Spam Filter
subtitle: Investigating Feature Selection
thumbnail: assets/images/projects/svm/spam_mail.png
pdf: assets/images/projects/svm/HW3_SVM.pdf
type: ml
---

A scikit-learn Support Vector Machine was applied to the problem of
identifying spam emails using varying selections of data features to investigate
their effect on performance.

### Method
The SVM from scikit-learn was applied to the [UCI Spambase
dataset](https://archive.ics.uci.edu/ml/datasets/Spambase) in three rounds to
investigate the effects of feature selection.

Round 1:
<br>
Use all 57 features from the dataset

Round 2:
<br>
Use only the most predictive features as identified from round 1.
         The number of features used was varied, beginning with only the two
         most important features, then the three most important, then four, up
         to using all 57 features again.

Round 3:
<br>
Use a limited number of features similar to round 2 but select the features at 
random.

The accuracies of each trial were compared.

### Results
Round 1:
<br>
Using all features, the model achieved an accuracy of 90%.

Round 2:
<br>
Selecting features by predictive power showed that the top two most
predictive features accounted for
the entirety of the model's predictive power; adding further features did not
increase (or decrease) the model's accuracy.

Round 3:
<br>
Selecting features at random showed that as few as 4 features were able
to achieve 70% accuracy but around 32 features were sometimes able to achieve
90% accuracy. However, that was unstable as it depended on which specific
features were used and using more features often degraded performance. Only
after using about 51 of the 57 total features did accuracy reliably remain at
least 90%.

<br>
#### Ancillary Illuminating Details

This dataset was constructed from a set of personal emails and is described as
being only useful for a personalized spam filter and not a general purpose
spam filter that anyone can use. If you want to use an SVM spam filter you
will have to train it on your own emails!

Inspecting the most predictive features and doing some detective work reveals
that the most predictive features are pieces of specific personal information
such as the creator's name, company, department, keywords related to their
line of work, and even numbers which may have been associate with their office
or phone number.

My conclusion was that the legitimate emails from the training set would have
almost alwasy included the subject's name in the salutation and the content
would have likely been about a small number of subjects which allowed certain
keywords to be extracted as predictive features. Conversely, spam emails
likely did not contain the subject's name and would have been about a wide
array of topics. So it seems there was also a lesson about the
generalizability of one's training/testing data.


This dataset was created in 1999 so the tactics of spammers may be quite
rudimentary compared to those of today and thus easier to identify. I'd be
curious, but not very hopeful, about how such a spam filter would perform on
modern emails.

### Language
- Python
  - scikit-learn
  - numpy
  - matplotlib

[Full Report](/assets/images/projects/svm/HW3_SVM.pdf)

