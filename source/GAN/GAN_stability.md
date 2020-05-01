# Improve training stability

### LSGAN
[Least Squares Generative Adversarial Networks](https://arxiv.org/abs/1611.04076)  
adopt least squares loss function for the **discriminator**, which yeilds minimizing the Pearson x^2 divergence to enforce the fake samples toward the decision boundary  
According to [Gapeng](https://zhuanlan.zhihu.com/p/25768099) , [google study](#are-gans-created-equal-a-large-scale-study-nips-2018), [ajolicoeur/cats](https://ajolicoeur.wordpress.com/cats/) seems LS loss do not improve result, but [DeblurGANv2](/CNN/img2img/deblurring.html#deblurgan-v2-iccv-2019) using it. I guess least-square loss is suitable for restoration/ enhancement, but not generative task.

### WGAN (ICML 2017)
[Towards Principled Methods for Training Generative Adversarial Networks](https://arxiv.org/abs/1701.04862)
[Wasserstein GAN](https://arxiv.org/abs/1701.07875)  
improve the stability of learning by using Wasserstein-1 distance.  
Note: WGAN aims for stabilize the GAN without tweaking, not improving output. 
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

### SN-GAN (ICLR 2018)
[Spectral Normalization for Generative Adversarial Networks](https://openreview.net/pdf?id=B1QRgziT-)  
> One of the challenges in the study of generative adversarial networks is the instability of its training. In this paper, we propose a *novel weight normalization technique* called **spectral normalization** to **stabilize the training of the discriminator**. Our new normalization technique is computationally light and easy to incorporate into existing implementations. We tested the efficacy of spectral normalization on CIFAR10, STL-10, and ILSVRC2012 dataset, and we experimentally confirmed that spectrally normalized GANs (SN-GANs) is capable of generating images of better or equal quality relative to the previous training stabilization techniques.

### Relativistic Discriminator (ICLR 2019)
[The relativistic discriminator: a key element missing from standard GAN](https://arxiv.org/abs/1807.00734)  
[Relativistic GAN – Alexia Jolicoeur-Martineau](https://ajolicoeur.wordpress.com/relativisticgan/) | [reddit](https://www.reddit.com/r/MachineLearning/comments/8vr9am/r_the_relativistic_discriminator_a_key_element/)  
also called: RaGAN  
![](https://ajolicoeur.files.wordpress.com/2018/06/screenshot-from-2018-06-30-11-04-05.png)  
Aim to stablize the training process of GAN  
![](img/RaGAN_explaination.png)