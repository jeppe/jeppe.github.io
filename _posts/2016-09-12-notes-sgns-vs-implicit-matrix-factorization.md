---
layout: post
title: "Notes SGNS VS Implicit Matrix Factorization"
description: ""
category: ""
tags: []
date: 2016-09-12 16:30:33 +0300
---

Embedding is not a new concept, but recently has becomes extremely popular in many fields expecially natural language processing. It opens a door to represent a word with low-dimension continuous vector instead of one-shot vector. Generally, we could embed a word with different techniques such as SVD, neural network, and word2vec etc. Among those solutions, word2vec seems gain more attentions from both industry and academical worlds. Word2vec is originally proposed by Mikolov when he worked at Google. Initially, seldom formal stuff is shared to describe the mathmatical deduction behind it. However, we're shocked by the efficiency in dealing with large scale corpus. Many researchers do review the code shared by Mikolov and attempt to formulate them with mathmatical theory. By now, you can find many interesting tutorials from google by searching terms "word2vec". 

I would like to introduce some works from [Omer Levy](https://levyomer.wordpress.com/). Before you read his publications, I think you should have basic understanding about mathmatical formulation of word2vec from [Tomas Mikolov](https://papers.nips.cc/paper/5021-distributed-representations-of-words-and-phrases-and-their-compositionality.pdf). As I said before, it's a little hard to follow Mikolov's papers. So if you're not familiar with word2vec, more information about word2vec can be found in references [1,2,3]. In this post I would like to discuss reference [3], entilted "Neural Word Embedding as Implicit Matrix Factorization". In this work, Levy et al. do analyze skip-gram negative sampling $\(SGNS\)$ method and show that it equals to factorize a word-context PMI $\(pointwise\ mutual\ information\)$ matrix with a shifted value. Under his assumption, you could see some interesting results but may not be theorically rigorous. If you dive into the mathmatical details, you might find something puzzle about the changes at equation 3 to 5. 

Here is my first concern. Original SGNS objective function could be modefied as follows:

$$
\begin{equation}
\begin{aligned}
	\ell &= \sum_{w \in V_W} \sum_{c \in V_C} \#(w,c) (log \sigma(\vec{w} \cdot \vec{c})) + k \cdot \mathbb{E}_{c_N} \sim P_{D}[log \sigma(-\vec{w} \cdot \vec{c_{N}})]\\
	     &= \sum_{w \in V_W} \sum_{c \in V_C} \#(w,c) (log \sigma(\vec{w} \cdot \vec{c})) + \sum_{w \in V_W} \sum_{c \in V_C} \#(w,c) \cdot k \cdot \mathbb{E}_{c_N} \sim P_{D}[log \sigma(-\vec{w} \cdot \vec{c_{N}})]\\
	     &=\sum_{w \in V_W} \sum_{c \in V_C} \#(w,c) (log \sigma(\vec{w} \cdot \vec{c})) + \sum_{w \in V_W}\#(w) (k \cdot \mathbb{E}_{c_N} \sim P_{D}[log \sigma(-\vec{w} \cdot \vec{c_{N}}))]
\end{aligned}
\end{equation}
$$

where the expection term can be expanded as:

$$
\begin{equation}
\begin{aligned}
	\mathbb{E}_{c_N} \sim P_{D}[log \sigma(-\vec{w} \cdot \vec{c_{N}}) = \sum_{c_N \in V_C} \frac {\#(c_N)} {|D|} log\sigma(-\vec{w}\cdot\vec{c_N})\\
	= \frac {\#(c)} {|D|} log\sigma(-\vec{w} \cdot \vec{c}) + \sum_{c_N \in V_C \setminus {c}}\frac {\#(c_N)} {|D|} log\sigma(-\vec{w}\cdot\vec{c_N})
\end{aligned}
\end{equation}
$$

For a specific pair $\(w,c\)$, local objective could be:

$$
\begin{equation}
\ell(w,c) = \#(w,c)log\sigma(\vec{w}\cdot\vec{c}) + k \cdot \#(w) \cdot \frac {\#(c)} {|D|} log \sigma(-\vec{w}\cdot \vec(c)
\end{equation}
$$

Based on Equation 3, you can derivate with respect to $x = \vec{w} \cdot \vec{c}$. Then set derivation to 0, we could get following result:

$$
\begin{equation}
 \vec{w} \cdot \vec{c} = log(\frac {\#(w, c) \cdot |D|} {\#(w)\cdot\#(c)} \cdot \frac {1} {k}) = log(\frac {\#(w, c) \cdot |D|} {\#(w)\cdot\#(c)}) - log k
\end{equation}
$$

where $log\(\frac {\( w,c \) \cdot |D|} {\( w \) \cdot \( c \)}\)$ is the well known pointwise mutual information PMI. Therefore, Levy et al. come up with a conclusion that SGNS is equal to factorize a PMI matrix.

+ Negative context disappears from Equation 3

+ The reason why target context $c$ appears in the negative sampling term is not explained.

+ The conclusion that SGNS equals to PMI matrix factorization is not strict based on 1 and 2 consideration.

From the experimental results we can see that Levy et al. emphasize the comparison error between the estimated value and observed PMI matrix. In terms of this, SGNS performs better than pure SVD, worse than SPPMI. But the error rate is in an acceptable range, though not like SPPMI. I just suppose that SGNS keeps the negative sampling terms which might act a regularization term to penalty those unobserved word-context pairs. __The results show that SGNS and SPPMI may prefer frequent word-context pairs__.

Personally, this work dirves us to dig out the reason why SGNS could perform so well, and its connection to matrix factorization methods. However, PMI matrix is an empirical estimation about correlation of word-context pairs, which may not give us a deeper understanding about the word-context graph. If we represent word-context as a graph, SGNS could easily incorporate graph structure inforation into learning framework. While PMI matrix factorization may need some speical transformation to encode high-order graph structure into word-context correlation matrix. 

Reference:

[1] Goldberg, Yoav, and Omer Levy. "word2vec Explained: deriving Mikolov et al.'s negative-sampling word-embedding method." arXiv preprint arXiv:1402.3722 (2014).

[2] Levy, Omer, and Yoav Goldberg. "Neural word embedding as implicit matrix factorization." Advances in neural information processing systems. 2014.

[3] Levy, Omer, Yoav Goldberg, and Ido Dagan. "Improving distributional similarity with lessons learned from word embeddings." Transactions of the Association for Computational Linguistics 3 (2015): 211-225.

[4] Schnabel, Tobias, et al. "Evaluation methods for unsupervised word embeddings." Proc. of EMNLP. 2015.

