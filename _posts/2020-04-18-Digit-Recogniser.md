---
layout: post
title: Handwritten Digit Recognition 
subtitle: Torching the digits!
image: /img/PyTorch_Img.jpeg
bigimg: /img/CNN_Img.jpg
tags: [PyTorch, Keras, Kaggle, Deep Learning]
comments: true
---

In my last post, I talked about using Keras as the programming framework for building my Convolutional Neural Network (CNN). Today, I'd like to write about my experience using PyTorch and Keras both for making a handwritten digit recognizer on [kaggle](https://www.kaggle.com/).  

PyTorch initially seemed a bit difficult to me given that I was used to the level of abstractions in Keras where you could contruct a fully fledged NN in a couple lines with relative ease. PyTorch also seemed to be more unintuitive in its syntax and sets of functions. After going through loads of documentation and being stuck on a bad bug for 2 days, I came to realise that its so much more dynamic and flexible.

Handwritten digit recognition is probably one of the basic problems that one new to CNN's would implement. Since I was relatively unfamiliar with PyTorch, I first created a very basic model with Keras, tuned its hyperparameters to achieve a fairly decent test accuracy of 99.3% and then used the same model with PyTorch and improved it by adding certain features like regularization to optimize it.  

Specifically, my model consisted of 2 convolutional layers and a maxpool layer, followed by another 2 convolutional layers and a maxpool layer, after which came 2 fully connected layers. I also used batch normalization and dropout in intermediate stages to allow for faster convergence and prevent overfitting to the training set. Training the model even for 15-20 epochs was taking an abominable amount of time so I switched over to my GPU and after that, training was a breeze and I was able to go for 150-200 epochs easily. You can look at the complete code in my [Github Repo](https://github.com/thomas-jac/Digit-Recognizer).      

Finally, long story short, I trained my model for 150 epochs using Adam optimizer and was really excited to be able to get to 99.42% test accuracy in PyTorch and 99.47% in Keras after refining it. I plan to use data augmentation in the future hoping to drive the test accuracy to about 99.6-99.7%.
