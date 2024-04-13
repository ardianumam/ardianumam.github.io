---
layout: post
title: Linear Regression Using Least Square Estimation
date: 2017-09-20 11:12:00-0400
description: 
tags: machinelearning regression lse
categories: machine-learning
disqus_comments: false
related_posts: true
---


It is a good start to learn regression linear on machine learning study, since it is simple and can give intuitive meaning how a machine learns a bunch of data. See picture below.

`insert image here`

Given data points (red dots) and we want to plot a linear line that fits those data (blue line). In machine learning context, we will use those data points as training data to make best linear function to fit those those points. Picture above has one input element with one output element. We will use 1-dimensional array with $$n$$ component for input with one output element. Our linear model can be written as follow, with $$h(\mathbf{x})$$ means hypothesis/prediction of input $$\mathbf{x}$$.