# Datasets
[wiki: List of datasets for machine learning research](https://en.wikipedia.org/wiki/List_of_datasets_for_machine-learning_research)
## Image
#### MNIST
[MNIST](http://yann.lecun.com/exdb/mnist/): handwriting digit
#### ImageNet
>14 million images  
20000 categories  
Labeled objects, bounding boxes, descriptive words, SIFT features  
#### CIFAR-10/100
[CIFAR-10 and CIFAR-100 datasets](https://www.cs.toronto.edu/~kriz/cifar.html)  
low-resolution. Good for generative model. Difficult to learn comparing to face  
CIFAR-10: 10 classes, with 6000 images per class
CIFAR-100: 100 classes containing 600 images each
### NUS-WIDE

#### Common Objects in COntext (COCO)
[COCO - Complex Adaptive Systems Laboratory](http://complexity.cecs.ucf.edu/coco/)
Number of images in the dataset: 330,000 images while more than 200,000 are labeled (roughly equal halves for training and validation+test)  
Number of classes: 80 object categories, 91 stuff categories  
Image resolution: 640×480

#### Open Image
[Open Image Dataset V5](https://storage.googleapis.com/openimages/web/index.html) by google
label + boxes + segmentation + relationship annotation

## Image Segmenation 
* [PASCAL Visual Object Classes (PASCAL VOC)](http://host.robots.ox.ac.uk/pascal/VOC/)
* [PASCAL-Context](https://cs.stanford.edu/~roozbeh/pascal-context/)
* [Cityscapes](https://www.cityscapes-dataset.com/)
* [CamVid](http://mi.eng.cam.ac.uk/research/projects/VideoRec/CamVid/)
* [ADE20K](https://groups.csail.mit.edu/vision/datasets/ADE20K/)

|             |Images  |Obj. Inst   |Obj. Cls|Part Inst.|Part Cls|Obj. Cls. per Img|
|-------------|--------|------------|--------|--------|-----|-----|
|COCO         |123,287 |  886,284   |      91|       0|    0|  3.5|
|ImageNet∗    |476,688 |  534,309   |     200|       0|    0|  1.7|
|NYU Depth V2 |  1,449 |   34,064   |     894|       0|    0| 14.1|
|Cityscapes   | 25,000 |   65,385   |      30|       0|    0| 12.2|
|SUN          | 16,873 |  313,884   |   4,479|       0|    0|  9.8|
|OpenSurfaces | 22,214 |   71,460   |     160|       0|    0|  N/A|
|PascalContext| 10,103 | ∼104,398∗∗ |     540| 181,770|   40|  5.1|
|ADE20K       | 22,210 |  434,826   |   2,693| 175,961|  476|  9.9|
from [Scene Parsing through ADE20K Dataset](http://people.csail.mit.edu/bzhou/publication/scene-parse-camera-ready.pdf)

### RGB-D  
#### SUN RGB-D
A RGB-D Scene Understanding Benchmark Suite  
[Project page](http://rgbd.cs.princeton.edu/)  
[Challenge](http://rgbd.cs.princeton.edu/challenge.html)  

#### NYU dataset
https://cs.nyu.edu/~silberman/datasets/nyu_depth_v2.html

## Object Tracking
### youtube-bb
### MOT Challenge: Multiple Object Tracking
[MOT Challenge](https://motchallenge.net/)
detection is provided
### OTB2015
provide one boundary box in a reference frame, then following this items
[OTB2015](http://cvlab.hanyang.ac.kr/tracker_benchmark/datasets.html)
## Face Datasets
#### Labled Faces in the Wild (LFW)
#### YouTube Faces (YTF)
#### MegaFace Challenge

## Pose
## Human Activity
[ActivityNet](http://activity-net.org/)

### HDR Datasets
#### Fairchild
[Fairchild](http://rit-mcsl.org/fairchild//HDR.html)
tone mapping with multi. exposures, 106 images

## Video
For frame interpolation, super-resolution etc  
[Vimeo90K](http://toflow.csail.mit.edu/)
### Optical Flow
[Middlebury](http://vision.middlebury.edu/flow/data/)

## Image grading
### MIT-Adobe FiveK Dataset
[Adobe FiveK](https://data.csail.mit.edu/graphics/fivek/)
5,000 photos in DNG format
An Adobe Lightroom catalog with renditions by 5 experts
Semantic information about each photo

## Image Compression
* [Image Cpmpression](https://www.compression.cc/)
