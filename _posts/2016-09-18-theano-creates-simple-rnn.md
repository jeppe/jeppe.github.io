---
layout: post
title: "Theano creates simple RNN"
description: ""
category: ""
tags: []
date: 2016-09-18 10:27:32 +0300
---

Before creating a simple Recurrent Neural Network, we should know how it works to deal with sequences datasets. You can find an impressive describtion about RNN from [here](http://www.wildml.com/2015/09/recurrent-neural-networks-tutorial-part-1-introduction-to-rnns/) and LSTM from [here](http://colah.github.io/posts/2015-08-Understanding-LSTMs/). I definitely believe that after you read them, a breif understanding of RNN and LSTM could be encoded into your mind. Next you need to download a sample code from [Denny Britz's Github](https://github.com/dennybritz/rnn-tutorial-rnnlm) as a base to build more complex RNN model. It uses some fancy functions of Theano, like scan with bptt_truncate, function definition etc. Initially, you may be mad about the unfamiliar notion used by Theano. But you will find the expression could be so simple to clearify a recurrent network. Some basic concepts about Theano can be found from this [tutorial](http://www.marekrei.com/blog/theano-tutorial/).

As an initial user of Theano, many of you might get stuck with the symbolic programming. At the beginning, I take a lots of time to understand the core part of RNN code, especially the concept of theano.scan function. From the official explaination, we could regard it as a loop function or map function of theano, but beyond them. You could modify it to be a recurrent neurall network easily, just pass a value to bptt_truncate parameter. After that, the function could be automically implemented the unfolding operation. To date, I just have an basic concept about the symbolic variable graph, which could be regard as a data flow. After you call a theano function, data could flow cross the graph. Then updates could be implemented by an inverse pass.  
