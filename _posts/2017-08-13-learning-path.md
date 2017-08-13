---
layout: post
title:  "Machine Learning Path"
author: "Joppe"
---

<div class="post-intro">
In this post, I will keep track of my progress in acquiring necessary skills to become productive in machine learning.
The end goal is to apply these skills and have a meaningful impact on people in "the real-world".

At every stop along the path, I give a description together with 
my evaluation of the contribution of this stop to my machine learning skills. 
</div>

* TOC
{:toc}

## Courses
### Stop 1. _Artificial Neural Networks_
_KU Leuven University - professor Suykens_

**Overview**. [This introductory course](https://onderwijsaanbod.kuleuven.be/syllabi/e/H02C4AE.htm#activetab=doelstellingen_idp1338320) 
covered the basics of artificial neural networks, 
starting with a **perceptron** and its universal approximating capabalities.
It then progressed with multi-layer feedforward networks and **backpropagation**,
including **training** methods and **regularization**.
We saw the basics of recurrent neural networks with **Hopfield** networks.

A few unsupervised learning methods like **PCA, K-means clustering and self-organising maps** were also on our plate.

The course material eventually touched briefly on **convolutional neural networks** 
as an introduction to a deep learning approach.

**Evaluation.** The course was given from a mathematics perspective, 
which required the application of the linear algebra that I had seen in the previous semester.
If you need to build an intuition about a new subject, this approach might not be preferable. 
However, after I read the [Hacker's guide to Neural Networks](http://karpathy.github.io/neuralnets/),
I was comfortable reading the math in the course and connect it to the corresponding neural network elements.

Apart from the lectures, this course was mainly evaluated on a number of assignments we had to code in Matlab.
The topics covered:
- a comparison of the Levenberg-Marquardt optimization, with versus without Bayesion regularization,
- reconstruction of noisy digits using a Hopfield network as well as using PCA,
- digit classification using stacked autoencoders,
- character recognition with a Hopfield network, and
- wine classification using a multi-layer feedforward network.

The assignments forced the student to really get familiar with the mathematical background.
It's the combination of the theoretical and practical side of things that made this course 
a valuable contribution to my machine learning path.

### Stop 2. [_CS231n_](http://cs231n.stanford.edu): Convolutional Neural Networks for Visual Recognition
_Stanford University - Andrej Karpathy_

The examples at the end of the ANN course included the remarkable results attained with **convolutional neural networks**.
Thus, this well-renowned course by Fei-Fei Li and Andrej Karpathy was a logical next step.

TK
