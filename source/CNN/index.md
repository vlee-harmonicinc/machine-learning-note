# CNN
* [Models](models.md)
* [Multi-Scale Feature Representations](multi-scale_feature_representations.md)
* [Visualization](visualization.md)
* [Image-to-Image Translation](img2img/index.md)
* [Optical character recognition, OCR](optical_character_recognition.md)
* [Image Retrieval](image_retrieval.md)
* [Object Detection](object_detection/index.md)
## Video
* [Video Enhancement](video/video_enhancement.md)
* [Video Frame Interpolation](video/video_frame_interpolation.md)
* [Video Deblurring](video/video_deblurring.md)
* [Video Fingerprint](video/video_fingerprint.md)

## 3D
* [3D Object Detection](3D/3D_object_detection.md)
* [3D Pose Estimation](3D/3D_pose_estimation.md)
* [3D Reconstruction](3D/3D_reconstruction.md)

## Concept
### Image Convolution
![](img/image_convolution.png)
### Weighting Sharing
### Receptive Field
[VGG](models.html#vgg-iclr-2014)
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
1. deconvolution [Deconvnet](models.html#deconvolution)
1. [PixelShuffle](models.html#pixelshuffle-cvpr-2016)
