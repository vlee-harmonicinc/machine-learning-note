## General

### GAN (NIPS 2014)
[Generative Adversarial Networks](https://arxiv.org/abs/1406.2661) by iangoodfellow  
[Ian Goodfellow NIPS 2016 tutorial](https://arxiv.org/pdf/1701.00160.pdf)| [PPT](http://www.iangoodfellow.com/slides/2016-12-04-NIPS.pdf) 

### DCGAN
[DCGAN (ICLR 2016)](GAN_repersentation_learning.html#dcgan-iclr-2016)

<!--
### LSGAN
[Least Squares Generative Adversarial Networks](https://arxiv.org/abs/1611.04076)  
adopt least squares loss function for the discriminator, which yeilds minimizing the Pearson x^2 divergence  
Notes: [Gapeng](https://zhuanlan.zhihu.com/p/25768099) said change the loss in DCGAN without modification of model architecture do not imporve result
-->

### WGAN (ICML 2017)
[Towards Principled Methods for Training Generative Adversarial Networks](https://arxiv.org/abs/1701.04862)
[Wasserstein GAN](https://arxiv.org/abs/1701.07875)  
improve the stability of learning by using Wasserstein-1 distance. 
##### Wasserstein distance= Earth-Mover(EM) distance
KL, JS divegence is discontinue, not stable when training nerual network; introduce **WS divegence**, which is continues.  
the minimum cost of transporting mass in converting the data distribution q to the data distribution p  
solve: vanishing gradients in GAN casued by good discriminator + bad generator  
![middle_img](img/WGAN_critic.png)
##### Apart from Wasserstein-1 distance:
* No log in the loss. The output of D is no longer a probability, hence we do not apply sigmoid at the output of D
* Clip the weight of D (0.01)
* Train D more than G (5:1)
* Do not use optimator based on momentum. Use RMSProp instead of ADAM. (SGD is also okay)
* Lower learning rate (0.00005)
#### WGAN-GP (NIPS 2017)
[Improved Training of Wasserstein GANs](https://arxiv.org/abs/1704.00028)
WGAN issue: weight clipping to force continues
contrib: gradient penalty
* do NOT use batch noramlization

### Are GANs Created Equal? A Large-Scale Study (NIPS 2018)
[Are GANs Created Equal? A Large-Scale Study](https://arxiv.org/pdf/1711.10337.pdf) by Google Brain  
> Generative adversarial networks (GAN) are a powerful subclass of generative models. Despite a very rich research activity leading to numerous interesting GAN algorithms, it is still very hard to assess which algorithm(s) perform better than others. We conduct a neutral, multi-faceted large-scale empirical study on state-of-the art models and evaluation measures. We find that **most models can reach similar scores** with enough hyperparameter optimization and random restarts. This suggests that improvements can arise from a higher computational budget and tuning more than fundamental algorithmic changes. To overcome some limitations of the current metrics, we also propose several data sets on which precision and recall can be computed. Our experimental results suggest that future GAN research should be based on more systematic and objective evaluation procedures. Finally, we did not find evidence that any of the tested algorithms consistently outperforms the non-saturating GAN introduced in \cite{goodfellow2014generative}.

### SN-GAN (ICLR 2018)
[Spectral Normalization for Generative Adversarial Networks](https://openreview.net/pdf?id=B1QRgziT-)  
> One of the challenges in the study of generative adversarial networks is the instability of its training. In this paper, we propose a *novel weight normalization technique* called **spectral normalization** to **stabilize the training of the discriminator**. Our new normalization technique is computationally light and easy to incorporate into existing implementations. We tested the efficacy of spectral normalization on CIFAR10, STL-10, and ILSVRC2012 dataset, and we experimentally confirmed that spectrally normalized GANs (SN-GANs) is capable of generating images of better or equal quality relative to the previous training stabilization techniques.

### Projection Discriminator (ICLR 2018)
[cGANS with Projection Discriminator](https://openreview.net/pdf?id=ByS1VpgRZ)  
> We propose a novel, *projection based* way to **incorporate the conditional information into the discriminator** of GANs that respects the role of the conditional information in the underlining probabilistic model. This approach is in contrast with most frameworks of conditional GANs used in application today, which use the conditional information by concatenating the (embedded) conditional vector to the feature vectors. With this modification, we were able to significantly improve the quality of the class conditional image generation on ILSVRC2012 (ImageNet) 1000-class image dataset from the current state-of-the-art result, and we achieved this with a single pair of a discriminator and a generator. We were also able to extend the application to super-resolution and succeeded in producing highly discriminative super-resolution images. This new structure also enabled high quality category transformation based on parametric functional transformation of conditional batch normalization layers in the generator. 
[code](https://github.com/pfnet-research/sngan_projection)

### Relativistic Discriminator (ICLR 2019)
[The relativistic discriminator: a key element missing from standard GAN](https://arxiv.org/abs/1807.00734)  
[Relativistic GAN – Alexia Jolicoeur-Martineau](https://ajolicoeur.wordpress.com/relativisticgan/) | [reddit](https://www.reddit.com/r/MachineLearning/comments/8vr9am/r_the_relativistic_discriminator_a_key_element/)  
also called: RaGAN  
![](https://ajolicoeur.files.wordpress.com/2018/06/screenshot-from-2018-06-30-11-04-05.png)  
Aim to stablize the training process of GAN  
![](img/RaGAN_explaination.png)

### SAGAN (PMLR 2019)
[Self-Attention Generative Adversarial Networks](https://arxiv.org/pdf/1805.08318.pdf)  
learn global, **long-range dependencies** for generating images.  
![](img/SAGAN_attention_map.png)
Background: CNN usually fails to capture geometric or strcutural patterns because long range dependencies processed after passing through several convolutional layers, preventing learning about long-term dependencies for 
1. small model may not be able to represent them
2. optimization algorithms may have trouble discovering parameters value that carefully coordinate multiple layers to capture these dependencies
3. these parameterizations may be statistically brittle and prone to failure when applied to previously unseen inputs
Increasing the size of convolution kernel loses the computational and statistical efficiency
![](img/SAGAN_module.png)
Self-attention: map attention map by transpose (adapt non-local model of [Non-local Neural Network](/basic/attention.html#non-local-neural-networks-cvpr-2018)

> The reason is that self-attention receives more evidence and enjoys more freedom to choose conditions with larger feature maps
(i.e., it is complementary to convolution for large feature maps), however, it plays a similar role as the local convolution when modeling dependencies for small (e.g., 8×8) feature maps. It demonstrates that the attention mechanism gives more power to both the generator and the discriminator to directly model the long-range dependencies in the feature maps. 
##### Application
[DeOldify](https://github.com/jantic/DeOldify) [mention](https://www.reddit.com/r/MachineLearning/comments/9tcfls/p_introducing_deoldify_a_progressive/) self-attention GAN work well.

### BigGAN (ICLR 2019)
[Large Scale GAN Training for High Fidelity Natural Image Synthesis](https://arxiv.org/abs/1809.11096) by DeepMind  
__TPU advertisement__: 512 TPU  
[PyTorch code](https://github.com/ajbrock/BigGAN-PyTorch) | 
[\[P\] Want to train your own BigGAN on just 4-8 GPUs? Today we're releasing BigGAN-PyTorch](https://www.reddit.com/r/MachineLearning/comments/b461zt/p_want_to_train_your_own_biggan_on_just_48_gpus/)  
high resolution (512x512) output, based on [SA-GAN](#sa-gan-pmlr-2019)  
Not only increase the computation, there are still novel improvement to handle the big GAN.
1. Batch size and regularization
2. **truncation trick**: improve quality of output (trade-of diversity)
3. why big GAn usually not stable and solutions

### Mode Seeking GAN (CVPR 2019)
[Mode Seeking Generative Adversarial Networks for Diverse Image Synthesis](http://openaccess.thecvf.com/content_CVPR_2019/papers/Mao_Mode_Seeking_Generative_Adversarial_Networks_for_Diverse_Image_Synthesis_CVPR_2019_paper.pdf), MSGAN
![](img/Mode_Seeking_GAN.png)
mode seeking regularization term to directly maximize the ratio of the distance between G(c, z1) and G(c, z2) with respect to the distance between latent code z1 and z2  
```math
L_{ms}=max_G(\frac{d_I(G_(c,z_1), G_(c,z_2))}{d_z(z_1,z_2)})
```
