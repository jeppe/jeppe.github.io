---
layout: post
title: "Notes SGNS VS Implicit Matrix Factorization"
description: ""
category: ""
tags: []
date: 2016-09-12 16:30:33 +0300
---

Embedding is not a new concept, but recently has becomes extremely popular in many fields expecially natural language processing. It opens a door to represent a word with low-dimension continuous vector instead of one-shot vector. Generally, we could embed a word with different techniques such as SVD, neural network, and word2vec etc. Among those solutions, word2vec seems gain more attentions from both industry and academical worlds. Word2vec is originally proposed by Mikolov when he worked at Google. Initially, seldom formal stuff is shared to describe the mathmatical deduction behind it. However, we're shocked by the efficiency in dealing with large scale corpus. Many researchers do review the code shared by Mikolov and attempt to formulate them with mathmatical theory. By now, you can find many interesting tutorials from google by searching terms "word2vec". 

In this post, I would like to introduce some works from [Omer Levy](https://levyomer.wordpress.com/). Before you read his publications, I think you should have basic understanding about mathmatical formulation of word2vec from [Tomas Mikolov](https://papers.nips.cc/paper/5021-distributed-representations-of-words-and-phrases-and-their-compositionality.pdf). Let's begin from Omer Levy's NIPS'14, entilted "Neural Word Embedding as Implicit Matrix Factorization". In this work, Levy et al. do analyze skip-gram negative sampling $\(SGNS\)$ method and show that it equals to factorize a word-context PMI $\(pointwise\ mutual\ information\)$ matrix with a shifted value. Under his assumption, you could see some interesting results but may not be theorically rational. 



