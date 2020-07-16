# Auto-Encoder
## AutoEncoder, AE
Not sure where is the origin
[Autoencoder-Deep Learning](https://www.deeplearningbook.org/contents/autoencoders.html)
Usage:
1. Dimensionality reduction [Reducing the dimensionality of data with neural networks (Science 2006)](https://dbirman.github.io/learn/hierarchy/pdfs/Hinton2006.pdf)  
2. Information retrieval via **semantic hashing**: produce a code that is low-dimensional and binary, then stored in hash table. 1. easily return entries with same binary code and search similar (or less similar) entries efficiently
3. Denoising, inpaint task

## VAE
[Auto-encoding variational bayes (ICLR 2014)](https://arxiv.org/abs/1312.6114)  
How to apply autoencoder to generative task like GAN? **V**ariantional **A**uto**E**ncoder
* enforce the posterior distribution of latent representation `$p(z|x)$` follows standard distribution
* encoder (MLP) compute mean vector $\mu$ and standard deiation vector `$\sigma$`, combine them to sampled latent vector `$z$`
```math
\text{variational loss} = D_{KL} [p(z|x) \parallel q(z|x)] = D_{KL} [N(\mu_x, \sigma_x) \parallel N(0,1)] \\
Loss = \text{reconstruction loss}_{MSE} + \text{variation loss}
```
### Re-parameterization Trick
adding noise that follow standard distribution to latent space in order to backpropagate through a random node
```math
z=\mu+\sigma \epsilon \text{ , where }\epsilon \text{ is an auxiliary noise variable }\epsilon \sim N(0, 1)
```
result: improve latent space that not accessable with samples in dataset
![](https://miro.medium.com/max/2000/1*9ouOKh2w-b3NNOVx4Mw9bg@2x.png) from [Understanding Variational Autoencoders (VAEs) - Towards Data Science](https://towardsdatascience.com/understanding-variational-autoencoders-vaes-f70510919f73)
### Inference
random generate latent representation `$z$` that follows sample distribution `$log q_\phi(z|x^{(i)})=log N(z;μ^{(i)},σ^{2(i)}I)$`, then use decoder to generate output

### Disadvantages of VAE comparing with GAN:
* usually blurry

### Other Explaination
[变分自编码器（一）：原来是这么一回事 - 科学空间|Scientific Spaces](https://spaces.ac.cn/archives/5253)

## CVAE
Conditional VAE
[Learning Structured Output Representation using Deep Conditional Generative Models (NIPS 2015)](https://papers.nips.cc/paper/5775-learning-structured-output-representation-using-deep-conditional-generative-models.pdf)

## VAE-GAN
[Autoencoding beyond pixels using a learned similarity metric (ICML 2016)](https://arxiv.org/abs/1512.09300)

## VQ-VAE

## ALAE
[Adversarial Latent Autoencoders (CVPR 2020)](https://arxiv.org/pdf/2004.04467v1.pdf)  
[PyTorch](https://github.com/podgorskiy/ALAE)  
StyleGAN + latent space reconstruction via VAE (is the concept a bit like UNIT in single domain & loss based on latent space ?)

## NVAE

