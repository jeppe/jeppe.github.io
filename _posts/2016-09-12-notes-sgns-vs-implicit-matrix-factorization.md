---
layout: post
title: "Notes SGNS VS Implicit Matrix Factorization"
description: ""
category: ""
tags: []
date: 2016-09-12 16:30:33 +0300
---

Embedding is not a new concept, but recently has becomes extremely popular in many fields expecially natural language processing. It opens a door to represent a word with low-dimension continuous vector instead of one-shot vector. Generally, we could embed a word with different techniques such as SVD, neural network, and word2vec etc. Among those solutions, word2vec seems gain more attentions from both industry and academical worlds. Word2vec is originally proposed by Mikolov when he worked at Google. Initially, seldom formal stuff is shared to describe the mathmatical deduction behind it. However, we're shocked by the efficiency in dealing with large scale corpus. Many researchers do review the code shared by Mikolov and attempt to formulate them with mathmatical theory. By now, you can find many interesting tutorials from google by searching terms "word2vec". 

I would like to introduce some works from [Omer Levy](https://levyomer.wordpress.com/). Before you read his publications, I think you should have basic understanding about mathmatical formulation of word2vec from [Tomas Mikolov](https://papers.nips.cc/paper/5021-distributed-representations-of-words-and-phrases-and-their-compositionality.pdf). As I said before, it's a little hard to follow Mikolov's papers. So if you're not familiar with word2vec, more information about word2vec can be found in references [1,2,3]. In this post I would like to discuss reference [3], entilted "Neural Word Embedding as Implicit Matrix Factorization". In this work, Levy et al. do analyze skip-gram negative sampling $\(SGNS\)$ method and show that it equals to factorize a word-context PMI $\(pointwise\ mutual\ information\)$ matrix with a shifted value. Under his assumption, you could see some interesting results but may not be theorically rigorous.  

Reference:

[1] Goldberg, Yoav, and Omer Levy. "word2vec Explained: deriving Mikolov et al.'s negative-sampling word-embedding method." arXiv preprint arXiv:1402.3722 (2014).

[2] Levy, Omer, and Yoav Goldberg. "Neural word embedding as implicit matrix factorization." Advances in neural information processing systems. 2014.

[3] Levy, Omer, Yoav Goldberg, and Ido Dagan. "Improving distributional similarity with lessons learned from word embeddings." Transactions of the Association for Computational Linguistics 3 (2015): 211-225.

[4] Schnabel, Tobias, et al. "Evaluation methods for unsupervised word embeddings." Proc. of EMNLP. 2015.

