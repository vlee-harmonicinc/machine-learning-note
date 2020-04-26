# CNN
* [Models](models.md)
* [Multi-Scale Feature Representations](multi-scale_feature_representations.md)
* [Visualization](visualization.md)
* [Image-to-Image Translation](img2img/index.md)
* [Optical character recognition, OCR](optical_character_recognition.md)
* [Image Retrieval](image_retrieval.md)
* [Object Detection](object_detection/index.md)
## 3D
* [3D Object Detection](3D/3D_object_detection.md)
* [3D Pose Estimation](3D/3D_pose_estimation.md)
* [3D Reconstruction](3D/3D_reconstruction.md)

## Concept
### Image Convolution
![](img/image_convolution.png)
### Weighting Sharing
### Receptive Field
[VGG](#vgg-iclr-2014)
### Pooling
1. downscale
1. small translation-invariance

### Downscale
1. resize
1. stride
1. pooling
    1. max pooling
    1. avg pooling

##### Stride vs pooling

|           |stride|pooling|
|-----------|------|-------|
|computation|less  |4 times more computation+pooling operate|
|propagation|bad   |better |

### Upscale / Up-sampling
used for 1. reverse downscale, 2. increase resolution  
usually required for pix 2 pix application, e.g. segmentation, super-resolution
###### Methods
1. resize  
resampling and interpolation
2. deconvolution [Deconvnet](models.html#deconvolution)
4. [PixelShuffle](#pixelshuffle-cvpr-2016)

### 1x1 convolution
could be used for changing the number of features
see [Inception (ILSVRC 2014)](#inception-ilsvrc-2014), 
[ACNet: Strengthening the Kernel Skeletons for Powerful CNN via Asymmetric Convolution Blocks (ICCV 2019)](https://arxiv.org/abs/1908.03930)

