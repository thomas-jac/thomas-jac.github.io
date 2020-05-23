---
layout: post
title: Deep Convolutional GAN's  
subtitle: A Battle of Adversaries : Part 2
image: /img/dcgan_small.jpg
bigimg: /img/DCGAN_post.jpg
tags: [DCGAN, GAN, PyTorch, Kaggle, Deep Learning]
comments: true
---

Welcome to my 2nd post in the GAN series!

You can have a look at the complete code for training a DCGAN on the MNIST dataset in my [GitHub Repo](https://github.com/thomas-jac/DCGAN-on-CelebA-Dataset) or my [kaggle notebook](https://www.kaggle.com/tjac718/dcgan-on-celeba-dataset).  


In my last post, I talked about creating a vanilla GAN
using a basic architecture for both the generator and discriminator and training it on the MNIST dataset.
If you need a GAN refresher, go [here](https://thomas-jac.github.io/2020-05-08-GAN-MNIST/).  

The results, while being magical in the sense that they were born from random noise, were not too appealing because the generator and discriminator are not able to learn the fine details due to their simplistic architecture consisting of only fully connected layers. 

Enter DCGAN's: In a DCGAN, both the generator and discriminator apply convolutions to their inputs, which allows them to learn fairly complex details. I'll describe some of the DCGAN's architectural idiosyncrasies; you might want to take a look at [this paper](https://arxiv.org/abs/1511.06434) to know about it in detail.

# Architecture Details:
The generator model consists of transposed convolutions used to upsample the random noise vector (I used a 100 dimensional one for my model) to the desired target size. A Batch Norm layer follows each transposed convolution layer (except for the output) for faster learning. The generator also uses ReLU activations for all layers except the output, which uses the tanh activation.

For the discriminator, convolutional layers downsample the training images and the generator output, finally reducing them to a single number determining whether the image is real or fake. Similarly to the generator,  a Batch Norm layer follows each transposed convolution layer (except for the output) for faster learning. Here, the activations used for all layers are the Leaky ReLU activations except the output, which uses the sigmoid activation.

# Training:
Before starting model training, the authors of the paper recommended a random initialization of the weights with mean 0 and a standard deviation of 0.02. Further, the authors also used an Adam optimizer with a slight departure from the default parameters. They set the learning rate to 0.0002 as the model was a bit unstable, with the default of 0.001. The $\beta 1$ hyperparameter used is 0.5. Now, we can begin training our model. I trained it for five epochs with a mini-batch size of 128. 

# Example Outputs:
With this, the fun begins!
I printed out some fixed generated samples every epoch, here are a few results:

Epoch 1-
![Epoch 1](/img/dcgan_epoch1.png)

Epoch 3-
![Epoch 3](https://github.com/thomas-jac/thomas-jac.github.io/blob/master/img/dcgan_epoch3.png)

Epoch 5-
![Epoch 5](https://github.com/thomas-jac/thomas-jac.github.io/blob/master/img/dcgan_epoch5.png)

# Loss Plots:
The generator and discriminator losses varied as the following:
![GAN Loss](https://github.com/thomas-jac/thomas-jac.github.io/blob/master/img/dcgan_loss_plot.png)

