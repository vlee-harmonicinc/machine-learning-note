# CNN
* [Models](models.md)
* [Image-to-Image Translation](img2img/index.md)
* [Optical character recognition, OCR](optical_character_recognition.md)
* [Image Retrieval](image_retrieval.md)
## Detection
* [Object Detection](object_detection/object_detection.md)
* [Segmentation](object_detection/segmentation.md)
* [Tracking](object_detection/tracking.md)
* [Temporal Action Proposal Genration](object_detection/temporal_proposal.md)
* [Measurement of Object Detection](object_detection/measurement.md)
* [Face Recognition](object_detection/face.md)
* [Pose Estimation](object_detection/pose.md)
* [Action Recognition](object_detection/action.md)
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
### Downscale
stride, pooling or resize
less computation required 
get high level features
##### Stride vs pooling

---------
|stride|pooling|
|---|--|-----|
computation|less|4 times more computation+pooling operate
gradient propagation|bad|better
upscale|
could propagate with pooling indice
### Upscale / Up-sampling
used for 1. reverse downscale, 2. increase resolution  
usually required for pix 2 pix application, e.g. segmentation, super-resolution
###### Methods
1. resize  
resampling and interpolation
2. un-pooling (if pooling is used) [Deconvnet](#deconvnet-iccv-2015)
3. Transposed Convolution (deconvolution)
4. [PixelShuffle](#pixelshuffle-cvpr-2016)

### 1x1 convolution
could be used for changing the number of features
see [Inception (ILSVRC 2014)](#inception-ilsvrc-2014), 
[ACNet: Strengthening the Kernel Skeletons for Powerful CNN via Asymmetric Convolution Blocks (ICCV 2019)](https://arxiv.org/abs/1908.03930)

