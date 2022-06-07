---
layout: post
title: K-means Clustering and Generation
subtitle: Classifying and Generating Handwritten Digits
thumbnail: assets/images/projects/k-means/number_grid.jpg
pdf: assets/images/projects/k-means/K_means_result_visualization.pdf
date: 2019-03-25
type: ml
---

Classify handwritten digits from the OptDigits dataset via the k-means
clustering algorithm. I implemented the algorithm myself using numpy and some
utility libraries.

After training, the centroid of each group could be interpreted as defining a
generalized version of that digit. It is trivial, then, to create an image using
the features of the centroid.

#### OptDigits image encoding
1. The original bitmap images are 32px &times; 32px.<br>
   Or, 32&sup2; = 1024 total pixels<br>
   <!-- ![32 x 32](/assets/images/projects/k-means/32x32.png) -->
   <img src="/assets/images/projects/k-means/32x32.png" alt="32x32" width="25%"/>
 
   Each pixel either contains information (1, on) or it does not (0, off). The
   pixels where the person writing the
   digit placed their pen contain information and are considered "on". Wherever the
   pen was not placed retains the background color and is considered "off".<br>
 
   (Perhaps confusingly, pixels that are "on" are colored white and pixels that are
   "off" are colored black. This may be the opposite of what we think of when we
   imagine someone writing a number with pen and paper but you can think of the pixel being on in the
   same way that a light is on, and the background is dark. (Or how pixels on a
   monochrome monitor are turned on to show information in that location.))<br>
 
   TL;DR: information present &rarr; pixel is on/1/white<br>

2. The pixels are grouped into non-overlapping blocks that are 4px x 4px (or
   16px total). <br>
   32px per side &divide; 4px per block = 8 blocks per side<br>
   This divides the image into 8&sup2; = 64 blocks<br>
   <!-- ![4 x 4 block](/assets/images/projects/k-means/4x4.png) -->
   <img src="/assets/images/projects/k-means/4x4.png" alt="4x4 block" width="25%"/>
   
3. For each block of 16 pixels the value of that block is determined by the
   number of pixels that are on (ranging from 0 to 16).<br>
   The spatial arrangement of the pixels is not encoded.<br>
   The values of the 64 blocks form the input values for each example that are fed
   into the k-means model.<br>
   This reduces the dimensionality from 1024 binary values (pixels) to 64 numerical
   values (each of which ranges from 0 to 16).
   
   <!-- ![example of a 7](/assets/images/projects/k-means/k-means_grid_final.png) -->
   <!-- ![input values for each block](/assets/images/projects/k-means/example_values.png) -->
   <p float="left">
   <img src="/assets/images/projects/k-means/k-means_grid_final.png" alt="example of a 7" width="45%"/>
   <img src="/assets/images/projects/k-means/example_values.png" alt="input values for each block" width="45%"/>
   </p>
   <br>
   On the left is an example digit (with the pixels and blocks delineated), on
   the right are the values for each block.<br>
   Hopefully you can still that the non-zero values in the image on the right
   form the vague shape of the digit from the image on the left.

(It took me some time looking through the dataset description, my results, and
my code to confirm the encoding. It's been several years since I did
the project and I wasn't required to write a full report, although now I
kind of wish I had.<br>
Perhaps there's a lesson to be learned about robust documentation.)

You can view the dataset for yourself on the
[OptDigits page](https://archive.ics.uci.edu/ml/datasets/Optical+Recognition+of+Handwritten+Digits)
hosted by UC Irvine.

#### Learning each digit by K-means
A K-means model is applied to the 16-dimensional representations of the various
digits and expected values are learned for each feature/dimension.
The combination of the 16 expected values defines the centroid of the group in
the 16-dimensional space.
New examples can be classified by assigning them to the same class as whichever
digit's centroid they are closest to (according to least squared Euclidean
distance).

#### Generating an image of the learned digit
Once the centroids have stabilized, they can be interpreted as generalized
digits. They are, after all, essentially the average of each training example in
a given cluster. 

###### Why are the images so fuzzy?
Of course, some examples may have been mis-classified and these
would distort the digit but mis-classifications should be rare and we can
confirm this by applying the learned centroids to our testing set. Anyway, the
existence of different number forms (such as those with and without feet, hats,
crossbars; 4's where the upper hollow is either open, semi-closed, or
fully-closed; as well as differences between U.S. and European/world standard
number forms) all mean that we should expect some amount of variation and no
centroid will have perfect boundaries.

Even ignoring different number forms, the positions and angles which people use
to write their numbers is often different. Although the examples in the data set
seem to be well-centered in the image some people may produce an image that is
translated slightly in one direction and there are certainly examples which are
wider or narrower, with angles more obtuse or more acute, and with line segments
slightly longer or shorter than their counterparts. In fact, if any one person
were asked to write the same number 100 times there would almost certainly by
some amount of variation, even though it was the exact same hand producing the
image.

TL;DR: The images are basically the average of the training examples and no two
are exactly the same, so there will always be some amount of divergence.

##### The mechanics of generating an image
Recall that the centroids each have 64 features corresponding to the 64 blocks
of the training image arranged in an 8&times;8 grid.<br>
Each feature has a value from 0 to 16 corresponding to the number of pixels in
that block that contained part of the drawn number.

Each value is scaled from the [0, 16] range to a [0, 255] greyscale range 
We are changing the resolution from the original<br> <!-- needed to keep 32x32
on together -->
32px &times; 32px black and white to
8&times;8 greyscale.
The greyscale serves to smooth the image and is integral in producing an image
that is at all recognizable.

(We discarded information on the position of each pixel in the dimensionality
reduction step at the very beginning, implicitly changing the resolution at that
point. We could maintain the original resolution at the cost of higher
dimensionality.)

One can then use any suitable method to arrange the greyscale pixels in the
correct positions and with the correct values to produce the generalized image.
The final image is only 8px &times; 8px so it is quite small, but by adjusting the
zoom I usually found a suitable level that was recognizable as the expected
digit.

(This actually highlights an interesting characteristic of the human visual
system. If the image is too small one cannot easily distinguish specific
features of the digit and it just looks like a white blob on a black background.
If the image is too large one tends to get distracted by the slight differences
between pixels and sees the image as a disparate collection of shades. Only
in the "Goldilocks zone" are the features of the digits distinct and coherent.)

![generated numbers](/assets/images/projects/k-means/number_grid.jpg)

A small amount of performance analysis was also done to evaluate the model.

### Language
- Python
  - numpy


[Report of Results](/assets/images/projects/k-means/K_means_result_visualization.pdf)

