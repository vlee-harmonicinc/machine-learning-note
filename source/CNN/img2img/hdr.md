# HDR

## HDRCNN (Siggraph Asia 2017)
[HDR image reconstruction from a single exposure using deep CNNs (Siggraph Asia 2017)](https://arxiv.org/abs/1710.07480)  
A hybrid dynamic range autoencoder that is tailored to operate on LDR input data and output HDR images. It utilizes HDR specific transfer-learning, skip-connections, color space and loss function
![](img/hdr-cnn_single_expo.jpg)

## Deep Reverse Tone Mapping (2017)
[Deep Reverse Tone Mapping](http://www.npal.cs.tsukuba.ac.jp/~endo/projects/DrTMO/)
input: 
1. LDR image
2. Fully CNNs: up-exposure model & down-exposure model → infer bracketed image
merge up-exposed and down-exposed image  
![](img/deep_reverse_tone_mapping.png)  
HDR image database is for creating bracketed LDR image by simulating cameras

## DeepHDR (ECCV 2018)
[https://arxiv.org/abs/1711.08937](https://arxiv.org/abs/1711.08937)
[Project](https://elliottwu.com/projects/hdr/) | 
[Tensorflow](https://github.com/elliottwu/DeepHDR)
> This paper proposes the first **non-flow-based** deep framework for high dynamic range (HDR) imaging of dynamic scenes with large-scale foreground motions. (without optical flows)


## hdrnet (Siggraph 2017)
[Deep Bilateral Learning for Real-Time Image Enhancement](https://groups.csail.mit.edu/graphics/hdrnet/data/hdrnet.pdf) by MIT, Google  
[Project](https://groups.csail.mit.edu/graphics/hdrnet/)
convert image to hdr image in real-time and mobile
### Image processing review
#### Bilateral Grid
[Real-time Edge-Aware Image Processing with the Bilateral Grid (SIGGRAPH 2007)](https://people.csail.mit.edu/sparis/publi/2007/siggraph/Chen_07_Bilateral_Grid.pdf)
x,y coordinates are augmented with third dimension which is a function of pixel's color
(gray 2D image -> 3D, color 2D image -> 5D)
3 contribution:
1. The bilateral grid: a new data structure that naturally enables edge-aware manipulation of image
2. Real-time bilateral filtering on GPU
3. Edge-aware algorithm: hdrnet introduce a number of real-time, edge-aware algorithms including edge-preserving painting, scattered data interpolation and local histogram equalization
#### Guided image filtering, ECCV 2010, TPAMI 2013
[Guided Image Filtering](http://kaiminghe.com/publications/eccv10guidedfilter.pdf)
#### Transform Recipes
[Transform Recipes for Efficient Cloud Photo Enhancement (ISGGRAPH 2015)](https://groups.csail.mit.edu/graphics/xform_recipes/data/xform_paper_sigasia2015.pdf)
Compression, image representation, image filter approximation
The task of computing the operator and fitting the recipe is offloaded to the cloud while the mobile device need only apply the recipe, thereby saving time and energy
[Bilateral Guided Upsampling (2016)](https://people.csail.mit.edu/hasinoff/pubs/ChenEtAl16-bgu.pdf)
### Contribution
targeting photographic transformation, which are often well-approximated with linear operation in bilateral space. Much faster than image-to-image transformation
1. Slicing: perform prediction in low-resolution bilateral grid
   new slicing operator for deep learning that performs data-dependent lookup that reconstructs output image from 3D bilateral grid
2. Affine color transform: predict transformation rather than output directly. hdrnet is designed to learn, as intermediate representation, a local affine color transformation.
3. full-resolution loss: loss function used is evaluated at full resolution, causes the low-resolution transformation learn to be optimized for high-resolution

## Deep Photo Enhancer (CVPR 2018)
[Deep Photo Enhancer: Unpaired Learning for Image Enhancement from Photographs with GANs](https://www.cmlab.csie.ntu.edu.tw/project/Deep-Photo-Enhancer/CVPR-2018-DPE.pdf)  
[Tensorflow implementation](https://github.com/nothinglo/Deep-Photo-Enhancer)  
trackle the problem with two-ways GAN whose structure similar to [CycleGAN](/generative_models/GAN_image2image.html#cyclegan-iccv-2017)  
individual batch normalization layers in generators with raw/ generated source  
**iBN**: without iBN, color will be broken  
**Global features**: extract iin layer 5, FC until 1x1x128, duplicated to 32x32x128  
**adaptive WGAN (A-WGAN)**  
__**Limitations**__
amplify noise if the input is very dark and contains a significant amount of noise. 
In addition, since some HDR images for training are products of tone mapping, our model could suffer from *halo artifacts* inherited from tone mapping for some images

## ExpandNet (Eurographics 2018)
[ExpandNet: A Deep Convolutional Neural Network for High Dynamic Range Expansion from Low Dynamic Range Content](https://arxiv.org/abs/1803.02266)
## Bit-Net