# YOLO
Offlical: [darknet/yolo](https://pjreddie.com/darknet/yolo/) (implemented in C and CUDA)  
Single Shot, very fast, real-time  
## YOLOv1
[You Only Look Once: Unified, Real-Time Object Detection (2015)](https://arxiv.org/abs/1506.02640)
1. divides input image into SxS grid
2. Each grid cell predicts B bounding boxes and confidence scores for those boxes.
3. Each grid cell predicts C conditional *class probabilites* `$Pr(Class_i|Object)$`  << classifier is within each grid, no proposal
Drawback: 
> YOLO imposes strong spatial constraints on bounding
box predictions since each grid cell only predicts two boxes
and can only have one class. This spatial constraint limits the number of nearby objects that our model can predict. Our model struggles with small objects that appear in
groups, such as flocks of birds.

## YOLOv2
[YOLO9000: Better, Faster, Stronger (2016)](https://arxiv.org/abs/1612.08242)  
* *Batch Normalization*: [Batch Normalization](/basic/normalization.html#batch-normalization-2015)
* *Convolutional With Anchor Boxes*: RPN like [Faster R-CNN](CNN/object_detection/object_detection.md#faster-r-cnn-2015), to increase recall  
* *Dimension Clusters*
>> Instead of choosing priors by hand, we run k-means
clustering on the training set bounding boxes to automatically find good priors.
* *Direct location prediction*
>> Most of the instability
comes from predicting the (x, y) locations for the box. Instead of predicting offsets we follow the approach of
YOLO and predict location coordinates relative to the location of the grid cell.
* *Fine-Grained Features*
>> YOLO simply adding a passthrough layer that brings
features from an earlier layer at 26 × 26 resolution.
The passthrough layer concatenates the higher resolution
features with the low resolution features by stacking adjacent features into different channels instead of spatial locations, similar to the identity mappings in ResNet.


## YOLOv3
[YOLOv3: An Incremental Improvement](https://pjreddie.com/media/files/papers/YOLOv3.pdf)
>> So here’s the deal with YOLOv3: We mostly took good ideas from other people. end.
### Extra: [Focal Loss](/CNN/object_detection/focal_loss.md)  
>> Things We Tried That Didn’t Work: Focal loss. We tried using focal loss. It dropped our mAP about 2 points. YOLOv3 may already be robust to the problem focal loss is trying to solve because it has separate objectness predictions and conditional class predictions. Thus for most examples there is no loss from the class predictions? Or something? We aren’t totally sure.
[为什么 YOLOv3 用了 Focal Loss 后 mAP 反而掉了？](https://www.zhihu.com/question/293369755)  
Dwzb said increase ignore threshold could improve result with focal loss. It is because label noise.

## YOLOv4
[YOLOv4: Optimal Speed and Accuracy of Object Detection](https://arxiv.org/pdf/2004.10934.pdf)
<!--
* FPN
* SPP
* Dense block
* CSP
* PAN
* SAM
* Bag of Freebies (BoF) for backbone/ detector
* Bag of Specials (Bos) for backbone/ detector
-->
