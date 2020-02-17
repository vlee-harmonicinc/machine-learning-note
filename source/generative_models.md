## Generative Models
### GAN
* [GAN page](/GAN.md)

### AutoEncoder, AE
Usage:
1. compression
2. denoising, etc application
3. For training deeper model. AE reduce data dimensions/ data whitening for training deeper network (in 2012, but replaced by normalization and Residual module later)

#### Variational Autoencoders, VAE
force the latent pace follow standard distribution
1. add divergence loss
2. encode mean vector and standard deiation vector, combine them to sampled latent vector
Result:
* improve latent space, could be manipulated
* improve generalization ability
  
comparing to GAN, it output is blur

### Flow
Flow-based generative model
#### NICE
[NICE: Non-linear Independent Components Estimation (2014)](https://arxiv.org/abs/1410.8516)
workshop paper at ICLR 2015  
optimize distribution by integration  
General coupling layer

merits:
* Exact latent-variable inference and log-likelihood evaluation
* Efficient inference and efficient synthesis
* Useful latent space for downstream tasks
[细水长flow之NICE：流模型的基本概念与实现](https://kexue.fm/archives/5776)
#### realNVP
real-valued non-volume preserving  
generalize coupling layer, add convolution
#### Glow
[Glow: Generative Flow with Invertible 1×1 Convolutions (2018)
](https://arxiv.org/abs/1807.03039)
extends from NICE and RealNVP  
addition of a reversible 1x1 convolution, as well as removing other components, simplifying the architecture overall  
[Glow: Better Reversible
Generative Models - OpenAI](https://openai.com/blog/glow/)  
BIG disadvantage: computation cost for training is too high  
256x256 high resolution face is in trained with 40 GPU for about a week. ~1 year for 1 GPU _(:3 J L)_
[github issue #37: anyone reproduced the celeba-HQ results in the paper](https://github.com/openai/glow/issues/37)
## Latent Space
Latent Space of encoder could be manipulated
### Process
input: unlabelled dataset to train enco
1. Train encoder-decoder with unlabelled dataset
2. Obtain average encoding of positive and negative inputs from labelled dataset
3. Get manipulation vector by taking difference
4. Manipulate new x_input along z_manipulate