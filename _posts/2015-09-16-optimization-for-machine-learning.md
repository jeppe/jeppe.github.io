---
layout: post
title: "Optimization for Machine Learning"
description: ""
category: ""
tags: [optimization, machine learning]
date: 2015-09-16 19:52:45 +0800
---

随着用户网上行为累积量剧增，不同商业领域在面对海量样本数据的时候，往往缺少有效的算法工具从中发现有价值的知识。面对这些问题，机器学习专家们发挥聪明才智，提出了许多可分布式的解决方案，如ADMM, VW, L-BFGS, Distributed SGD, OwLQN 等等。关于多种分布式解决方案，各有优势，需要通过深入研究其原理才能够掌握这些解决方案的应用场景。

### ADMM 的特点

通过研究文献 [1,2]

+ 可将海量数据集拆分，分布式存储于不同机器中
+ 通过构建全局参数约束允许单机迭代更新模型参数，然后通过 Batch 的方式更新全局参数
+ 收敛速度依赖具体的学习策略，收敛速度较慢，涉及好几个 Hyperparameters，比较难掌握
+ 通信频率较高，但可以通过根据具体问题，设计数据分配策略降低复杂度


References:

[1] Stephen Boyd, [Distributed Optimization and Statistical Learning via the Alternating Direction Method of Multipliers](https://web.stanford.edu/~boyd/papers/pdf/admm_distr_stats.pdf)

[2] Yong Zhuang, et al., [Distributed Newton Methods for Regularized Logistic Regression](https://www.csie.ntu.edu.tw/~cjlin/papers/mpi-liblinear/distributed_tron.pdf)
