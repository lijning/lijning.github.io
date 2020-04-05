---
layout:     post
title:      "Deep Learning: intro & CNN"
date:       2020-04-01 15:48:07
author:     "Jianing"
header-mask: 0.3
catalog:    true
lang: en
typora-root-url: "../../"
tags:
  - MachineLearning
  - coursework

---

# Deep Learning

## Overview

### Compared with traditional machine learning

- The old problem with neural network is scalability.

![image-20200401103347346](/../../../img/image-20200401103347346.png)

- Traditional:
  - Sensor :arrow_right: Feature Representation:arrow_right: Learning algorithm
  - Images contains just too many features for methods like Logistics Regression
  - Hand-tuned features
    - A feature extraction methods cannot be generalized to other domains: CV features are only useful for CV tasks
- Deep Learning:
  - Sensor :arrow_right:  Learning algorithm
  - Modelling directly on the **raw data** from the sensor
  - We can see all the **hidden layers** as a magic function that **map all features** into a space where we can simply do linear classification

### NN Compared with Boosting

- Both combing the results of many sub-classifier / sub-node.
- Boosting trains many sub-classifier consequently while NN trains them simultaneously.
- All sub nodes are at the same layers in Boosting (only linear combination), but for NN the can be stacked upon one another.

### Recent development

#### Take off: Alex Net

Image classification problem with 1000 categories: Alex Net improved the error rate from 26% to 15%.

## Build blocks of Neural Network

### SoftMax: from multinomial logistic regression

- $M$ classes to predict, $p$ dimensional features: Parameter matrix $W_{M\times p}$ 
- Class specific bias vector $b_{M\times 1}$ 

- In two-classes classification, we get rid of parameters for one class because $P(A)=1-P(B)$ 

### Multinomial logistic regression as "NN"

1. Input data vector
2. Probability vector: $\hat{h}_k$ (probability for class $k$)
3. Output layer: give a prediction randomly based on the probabilities.

### Basic neural network: layers & activation function

- If all layers are linear transformation, the results would be the same as that of single layer. (it's just linear combination of $X$)
- Activation function: non-linearization
  - i.e. sigmoid function
  - Only the last layer uses SoftMax

## Convolutional neural networks

### Why CNN?

- A drawback when we use fully-connected network for images:
  - We lost the spatial information when vectorizing the whole image

### How CNN structures?

- Each layer: a few layers of filters 每个filter提取该层的某些特征
- Each filter: some structural information?

- At last we vectorize a **cube** and do fully-connected layer 

#### issues

- :question: In each filter, hotspots corresponds to different directions? 
  - Slides 3-25 p37, video 3/30 28:47
- :question: why after filtering it's still $28\times 28$ (p39)

### Filter （卷积核）

- 传统CV的角度：每个filter是某种图像模式，filter的结果是input某个局部的图像跟模式模板匹配的相似度。[卷积运算](https://zhuanlan.zhihu.com/p/27908027)
- 神经网络的角度：每个filter是一个参数矩阵，同个layer的不同filter学习不同的特征。

### Pooling （池化）

- 用途：减少数据量 
- Skipping stride (subsampling) / Max-pooling 

- :grey_question: subsampling vs. dropout
  - dropout is for some iteration we don't use some values

### i.e. Face detection

- It scans every sub-images (the picture below is already a sub-image) and detect if there's a face here.
- The filters are like one-layer convolution.

Relation to Boosting?

- Some pre-defined filter (each for as one decision stump)
- As shown below, one filter activates when matching eye brows darker than eyes and another when the bright parts between two brows.
- Boosting is easier to build into hardware.

![image-20200401103716948](/../../../img/2020-04-01-ML-Deep-Learning/image-20200401103716948.png)

## Other DL frameworks

● Autoencoders (AE)
– unsupervised learning, representation learning
● Generative adversarial networks (GAN)
– try to “fool” a computer into thinking generated data is real
● Recurrent neural networks (RNN)
– sequential data, especially language modeling

## Issues

### Overfitting

- Early stopping: stop the iteration when we observe a turn (errors go back up) on the test set. 

