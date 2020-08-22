# image-to-image

## pix2pix
[Image-to-Image Translation with Conditional Adversarial Networks (CVPR 2017)](https://arxiv.org/abs/1611.07004) by Phillip Isola, Jun-Yan Zhu, Tinghui Zhou, Alexei A. Efros  
[https://phillipi.github.io/pix2pix/](https://phillipi.github.io/pix2pix/) | 
[Image-to-Image Demo](https://affinelayer.com/pixsrv/)
based on [conditional GAN](GAN_repersentation_learning.html#conditional-gan-2014), with image as conditional&noise input  
![](img/pix2pix_result.png)
dataset: paired image (supervised), e.g. segmentation/edge/map -> real photo, real photo → map
discriminator: PatchGAN which also take conditional as pairs 

## DTN
[Unsupervised Cross-Domain Image Generation (ICLR 2017)](https://arxiv.org/abs/1611.02200)  
Domain Transfer Network(DTN) with Identity Loss.  
![](img/DTN.png)
##### Identity Loss
first proposed in Equation 6 of this paper  
> The generator trained with this loss will often be more conservative for unknown content. -- from CycleGAN FAQ

## cycleGANs
[cycleGAN](cycleGAN.md)  
Could use unpaired datasets

## UNIT
[UNIT](UNIT.md)  

## GauGAN
### SPADE (CVPR 2019)
[Normalization/SPADE](/normalization.html#spade)
### Project
[Live Interactive Demos](https://www.nvidia.com/en-us/research/ai-playground/) | 
[Project](https://arxiv.org/abs/1903.07291) | 
[blog](https://blogs.nvidia.com/blog/2019/03/18/gaugan-photorealistic-landscapes-nvidia-research/)
<iframe width="1173" height="660" src="https://www.youtube.com/embed/p5U4NgVGAwg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Spectral Regularization
[Watch your Up-Convolution: CNN Based Generative Deep Neural Networks are Failing to Reproduce Spectral Distributions (CVPR 2020)](https://arxiv.org/pdf/2003.01826.pdf)  
> Generative convolutional deep neural networks, e.g. popular GAN architectures, are relying on convolution based up-sampling methods to produce non-scalar outputs like images or video sequences. In this paper, we show that **common up-sampling methods, i.e. known as upconvolution or transposed convolution, are causing the inability of such models to reproduce spectral distributions of natural training data** correctly. This effect is independent of the underlying architecture and we show that it can be used to easily detect generated data like deepfakes with up to 100% accuracy on public benchmarks. To overcome this drawback of current generative models, we propose to add a novel **spectral regularization** term to the training optimization objective. We show that this approach not only allows to train spectral consistent GANs that are avoiding high frequency errors. Also, we show that a correct approximation of the frequency spectrum has positive effects on the training stability and output quality of generative networks.
