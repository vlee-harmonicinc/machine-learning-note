# CNN
* [Models](/CNN/models.md)
* [Image-to-Image Translation](/CNN/img2img/index.md)
* [Optical character recognition, OCR](/CNN/optical_character_recognition.md)
* [Image Retrieval](/CNN/image_retrieval.md)
## Detection
* [Object Detection](/CNN/object_detection/object_detection.md)
* [Segmentation](/CNN/object_detection/segmentation.md)
* [Tracking](/CNN/object_detection/tracking.md)
* [Video Detection/ Tracking](/CNN/object_detection/video.md)
* [Temporal Action Proposal Genration](/CNN/object_detection/temporal_proposal.md)
* [Measurement of Object Detection](/CNN/object_detection/measurement.md)
* [Face Recognition](/CNN/object_detection/face.md)
* [Pose Estimation](/CNN/object_detection/pose.md)
* [Action Recognition](/CNN/object_detection/action.md)
## 3D
* [3D Object Detection](/CNN/3D/3D_object_detection.md)
* [3D Pose Estimation](/CNN/3D/3D_pose_estimation.md)
* [3D Reconstruction](/CNN/3D/3D_reconstruction.md)

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
#### Stride vs pooling
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
#### Methods:
1. resize  
resampling and interpolation
2. un-pooling (if pooling is used) [Deconvnet](#deconvnet-iccv-2015)
3. Transposed Convolution (deconvolution)
4. [PixelShuffle](#pixelshuffle-cvpr-2016)
### 1x1 convolution
could be used for changing the number of features
see [Inception (ILSVRC 2014)](#inception-ilsvrc-2014), 
[ACNet: Strengthening the Kernel Skeletons for Powerful CNN via Asymmetric Convolution Blocks (ICCV 2019)](https://arxiv.org/abs/1908.03930)

