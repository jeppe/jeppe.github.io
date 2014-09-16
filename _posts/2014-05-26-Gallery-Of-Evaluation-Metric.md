---
layout : post
category : lessons
tags : [machine learning, data mining, metric, evluation]
excerpt : Selection of suitable evaluation metric plays a significant role in learning best mathmetic model, as well as offering a uniformed approach to measure the performance of the data mining models from different perspectives. This post aims to set up a collection for existing evaluation metrics, which will be organized by the data mining tasks, such as top-k ranking, rating prediction, stability, diversity etc.
---

{% include JB/setup %}

Selection of suitable evaluation metric plays a significant role in learning best mathmetic model, as well as offering a uniformed approach to measure the performance of the data mining models from different perspectives. This post aims to set up a collection for existing evaluation metrics, which will be organized by the data mining tasks, such as top-k ranking, rating prediction, stability, diversity etc.

### Ranking

`Precision#K`

`Recall#K`

`nDCG`

### Classification

`Receiver operating characteristic (ROC)` is a graphical plot illustrating the performance of a binary classifier system by plotting the fraction of true positives out of total actual positives (TPR = true positive rate) vs. the fraction of false positives out of total actual negatives (FPR = false positive rate).

Ref. [Wikipedia](http://en.wikipedia.org/wiki/Receiver_operating_characteristic) [ROC curves and classification](http://www.r-bloggers.com/roc-curves-and-classification/)

`Area Under the ROC (AUC)` gives a threshold independent measure of how well a model is able to distinguish bewtween two possible outcomes. AUC equals to the probability that a classifier will rank a randomly chosen positive instance higher than a randomly chosen negative one

Ref. [Calculating AUC the hard way](http://www.r-bloggers.com/calculating-auc-the-hard-way/) [Wikipedia](http://en.wikipedia.org/wiki/Receiver_operating_characteristic)