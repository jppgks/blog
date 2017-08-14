---
layout: post
title:  "Machine Learning Path"
author: "Joppe"
---

<div class="post-intro">
<p>
In this post, I will keep track of my progress in acquiring necessary skills to become productive in machine learning.
The end goal is to apply these skills and have a meaningful impact on people in "the real-world".
</p>
<p>
At every stop, I give a description together with a reflection of the contribution of this stop to my machine learning skills. 
</p>
</div>

<div class="post-line"></div>

![](/assets/machine-learning-path.png)
<br/>
* TOC
{:toc}

<br/>
<div class="post-line"></div>

## Stop 1 - Artificial Neural Networks
_Course at KU Leuven University - professor Suykens_

**Overview**. [This introductory course](https://onderwijsaanbod.kuleuven.be/syllabi/e/H02C4AE.htm#activetab=doelstellingen_idp1338320) 
covered the basics of artificial neural networks, 
starting with a *perceptron* and its universal approximating capabalities.
It then progressed with multi-layer feedforward networks and *backpropagation*,
including *training* methods and *regularization*.
We saw the basics of recurrent neural networks with *Hopfield* networks.

A few unsupervised learning methods like *PCA, K-means clustering and self-organising maps* were also on our plate.

The course material eventually touched briefly on *convolutional neural networks* 
as an introduction to a deep learning approach.

Apart from the lectures, this course was mainly evaluated on a number of assignments we had to code in Matlab.
The topics covered:
- a comparison of the Levenberg-Marquardt optimization, with versus without Bayesion regularization,
- reconstruction of noisy digits using a Hopfield network as well as using PCA,
- digit classification using stacked autoencoders,
- character recognition with a Hopfield network, and
- wine classification using a multi-layer feedforward network.

**Reflection.** The course was given from a mathematics perspective, 
which required the application of the linear algebra that I had seen in the previous semester.
If you need to build an intuition about a new subject, this approach might not be preferable. 
However, after I read the [Hacker's guide to Neural Networks](http://karpathy.github.io/neuralnets/),
I was comfortable reading the math in the course and connect it to the corresponding neural network elements.

The assignments forced the student to really get familiar with the mathematical background.
It's the combination of the theoretical and practical side of things that made this course 
a valuable contribution to my machine learning path.

## Stop 2 - Convolutional Neural Networks for Visual Recognition (CS231n)
_Course at Stanford University (YouTube) - Andrej Karpathy_

The examples at the end of the ANN course included the remarkable results attained with **convolutional neural networks**.
Thus, [this well-renowned course](http://cs231n.stanford.edu) by Fei-Fei Li and Andrej Karpathy was a logical next step.

TK

## Stop 3 - Assignments deeplearning.ai (Coursera)
_Coursera courses (1-3, 4 & 5 aren't open yet at time of writing) - Andrew Ng_

**Overview.** [Andrew Ng's deep learning courses](https://www.coursera.org/specializations/deep-learning) became available on Coursera [last week](https://twitter.com/AndrewYNg/status/894994683931148288) (August 8, 2017), so I had to check them out. It turns out that the material covered in the first three of the 5 courses (only three open at time of writing) is more or less the same as what I had seen at stop 1 and 2. I took this opportunity to validate my learnings, and went through all of the quizzes and programming assignments. I published my solutions [on GitHub](https://github.com/jppgks/coursera-deeplearning.ai).

**Reflection.** Although I haven't seen any videos from the course, I can speak about the programming assignments. I felt like they were relatively easy, since Python is my go-to language and the instructions are very clear. They really take you by the hand and guide you through each Jupyter Notebook. I even found it addictive to get to the bottom of each notebook, which is an admirable feat by the team behind these courses.

This was a nice stop that gave me confidence to start mini-side-projects of my own now.
