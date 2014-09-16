---
layout: post
category : lessons
tags : [machine learning, simple note, linear model]
excerpt : In this post, we will explore a class of linear functions for classification task. The goal in classfication is to take an input vector $\textbf{x}$ and to assign it to one of $K$ discrete classes $\mathcal{C_k}$, where $k$ = 1,...,K. In the most common scenario, the classes are taken to be disjoint, so that each input is assigned to one and only class. The input space is there by divided into $decision\ regions$ whose boundaries are called $decision\ boundaries$ or $decision$ $surfaces$. In linear model, the decision surfaces are linearn function of input vector $x$ and are defined by (D - 1)-dimensional hyperplanes within the D-dimensional input space. Data sets whose classes can be separated exactly by linear decision surface are said to be $linearly$ $separable$. 
---
{% include JB/setup %}

In this post, we will explore a class of linear functions for classification task. The goal in classfication is to take an input vector $\textbf{x}$ and to assign it to one of $K$ discrete classes $\mathcal{C_k}$, where $k$ = 1,...,K. In the most common scenario, the classes are taken to be disjoint, so that each input is assigned to one and only class. The input space is there by divided into $decision\ regions$ whose boundaries are called $decision\ boundaries$ or $decision$ $surfaces$. In linear model, the decision surfaces are linearn function of input vector $x$ and are defined by ($n$ - $1$)-dimensional hyperplanes within the $n$-dimensional input space. Data sets whose classes can be separated exactly by linear decision surface are said to be $linearly$ $separable$.

Generally, each input vector $x_i \in D$ = {$x_1, x_2, \cdots ,x_{|D|}$} 

![least squares]({{ site.url }}/assets/images/prml/44.png)

**Fisher linear discriminant**

In terms of two classification cases, and suppose the $n$-dimensional input vector $x$ and project it down to on dimension using $$y = w^\top x$$. It provides alternative perspective to understand the basic linear function. We can see that the projection onto one dimension equals to project high-dimensional point into only one point, which could lead to a considerable loss of information, and classes that are separated in the original high-dimensional space may become strongly overlapping in one dimension. This following picture offers a visual way to under this concept.

![fisher]({{ site.url }}/assets/images/prml/46.png)

I will not given mathmatical description of the fisher linear function, since it is a special case of least squares for the two-class problem when some conditions are met, reference to Section 4.1.5, PRML. Thereby, Fisher criterion could also be sensitive to the outliers in some cases. We should carefully explore the distribution or statistical characteristics of the collected data. While I have no any experience on using fisher linear function, it's welcome to upload your idea on commonts.
