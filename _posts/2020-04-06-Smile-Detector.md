---
layout: post
title: Smile Detector! 
subtitle: Are You Happy Inside?
image: /img/keras_logo.png
bigimg: /img/cnn_img.png
tags: [Keras, Deep Learning]
comments: true
---

I've been taking Andrew NG's courses on the Deep Learning Specialisation lately, and frankly, it's a really good series and has introduced me to a lot of new things. One of the most fascinating ones has to be the use of programming frameworks. I'll describe my experience designing my first neural network completely by myself starting from its architechture with Keras in this post. 

I've been exposed to a few other frameworks namely, tensorflow and PyTorch but Keras seems to be the easiest one to implement a neural network in with a lot more abstractions than the other ones. At present, I'm doing the course on Convolutional Neural Networks, and I've implemented a Neural Network which can detect if a human is smiling or not in the image you feed into it. With the freedom of choosing one out of all the architectures in the world, I went for one similar to that on the paper [Parkhi et al.: Deep Face Recognition](https://ora.ox.ac.uk/objects/uuid:a5f2e93f-2768-45bb-8508-74747f85cad1). The dataset used by the authors had images of much higher resolution and they had a lot more training examples to start with than me (I was working on relatively much lower res images with fewer examples) so I just took some inspiration from the basic architechture of their Neural Network and sort of fiddled around with the hyperparameters like the filter numbers and sizes in the convolution and pooling layers and made it to be a 9 layered Neural Network. This is link to my [Git Repo](https://github.com/thomas-jac/Smile-vs-Not-Smile-Detector) for the code with the relevant datasets and supporting files (these, I obtained from the Keras tutorial on the CNN course by Stanford on coursera)

I trained the network for about 40 epochs. When I saw that it achieved about 100% accuracy at about 20 epochs only, I was honestly worried that I'd run into problems like gross overfitting and that the network would perform poorly on the test set but to my surprise, the test set accuracy was 98.667%! This was totally unexpected, so I'm thinking with regularization, this could achieve extremely impressive accuracy (if it wasn't impressive already). I'll probably do that at a later point and try to optimize it further.
