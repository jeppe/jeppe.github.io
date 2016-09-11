---
layout: post
title: "Notes on Gradient boosting factorizatioin machines"
description: ""
category: ""
tags: []
date: 2016-09-11 14:46:58 +0300
---

Few years ago, Chen et al. contributes to combining the benefits from both families of gradient boosting and factorization machines. In this work, a greedy searching function is defined to select optimal pair of interaction features. It differs from original factorization machines which can not filter noisy feature interactions. Sequently, the target functioin is updated by simply adding an interaction between the selected pair of features. This framework is very clear, however, there're still several puzzles remained.

Authors routinely unfold the objective function under the help of Tylor's expansion. Then objective could be transformed as a least square optimization problem with closed solution. One strang operation is that the target rating function $f(\cdot)$ is replaced by the greedy feature selection function. While authors did not prove the equality between rating function with the defined greedy function, and no more words is used to describe the reasons behind it. Another one is the operation $\textbf(x)_j == \textbf(z)_j$ at Equation 24. Nothing about $\textbf(z)_j$ is given. Does it have any relationship to $z_i$? This is a very important part to clear how to select optimal features. 

As GBFM will add only one pair of interaction feature at each iteration $s$, we may assume that those selected pairs might donimate the final prediction value. As far as we know, original factorization machines have a particular side-effect, i.e. high-order feature selection. We can train factorization machines by optimizing the pre-defined objective function. Then the significance of a pair fectures can be caculated via dot-product of their feature vectors. We can select out those most significant features by sorting previous caculated value. Feature interaction might have some special distribution, which may decrease fast after top-k item in the sorted list. If someone selects out the top-k pairs of features, then compare with the GBFM selected features. By doing that, we could gain more insight into the coincide between original objective function and replaced one.



