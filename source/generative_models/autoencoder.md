# Auto-Encoder
## AutoEncoder, AE
Not sure where is the origin
[Autoencoder-Deep Learning](https://www.deeplearningbook.org/contents/autoencoders.html)
Usage:
1. Dimensionality reduction [Reducing the dimensionality of data with neural networks (Science 2006)](https://dbirman.github.io/learn/hierarchy/pdfs/Hinton2006.pdf)  
2. Information retrieval via **semantic hashing**: produce a code that is low-dimensional and binary, then stored in hash table. 1. easily return entries with same binary code and search similar (or less similar) entries efficiently
3. Denoising, inpaint task

## VAE (ICLR 2014)
[Auto-encoding variational bayes](https://arxiv.org/abs/1312.6114)  
1. add divergence loss
2. encode mean vector and standard deiation vector, combine them to sampled latent vector
regulatisation and generalize via adding noise that follow standard distribution to latent space
```math
log p(x) \geq log p(x) - D_{KL}(q(z)||p(z|x)) = E_{z~q} log p(x,z) + H(q)
```
Result:
* improve latent space, could be manipulated
* improve generalization ability
![](https://miro.medium.com/max/2000/1*9ouOKh2w-b3NNOVx4Mw9bg@2x.png) from [Understanding Variational Autoencoders (VAEs) - Towards Data Science](https://towardsdatascience.com/understanding-variational-autoencoders-vaes-f70510919f73)

Disadvantages comparing with GAN:
* blur output
* Not asymptotically consistent unless q is perfect

## AVB (2017)
[Adversarial Variational Bayes: Unifying Variational Autoencoders and Generative Adversarial Networks](https://arxiv.org/abs/1701.04722)

## VAE-GAN (ICML 2016)
[Autoencoding beyond pixels using a learned similarity metric](https://arxiv.org/abs/1512.09300)

## ALAE (CVPR 2020)
[Adversarial Latent Autoencoders (CVPR 2020)](https://arxiv.org/pdf/2004.04467v1.pdf)  
[PyTorch](https://github.com/podgorskiy/ALAE)  
StyleGAN + latent space reconstruction via VAE (is the concept a bit like UNIT in single domain & loss based on latent space ?)
