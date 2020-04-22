# Keypoints based detector
## CornerNet (ECCV 2018)
[CornerNet: Detecting Objects as Paired Keypoints](https://arxiv.org/abs/1808.01244)  
detect pairs of top-left corner and bottom-right corner of bounding box.  
using [hourglass](/CNN/object_detection/pose#hourglass-eccv-2016) as backbone, followed by 2 prediction modules (top-left corners and bottom-right corners).  
Corners prediction module output *heatmap* of corner, *embedding* (for matching 2 corners) and offsets (to match original resolution).

Contribution:
* formulate the task of object detection as a task of detecting and grouping corners with embeddings
* the corner pooling layers that help better localize the corners
* significantly modify the hourglass architecture and add our novel variant of focal loss (Linet al., 2017) to help better train the network

### Corner Loss
[Focal loss](focal_loss.md) + reduce the penalty within a radiuss of positive location
```math
L_det = -\dfrac{1}{N} \sum_{c=1}^C\sum_{i=1}^H\sum_{j=1}^W 
\begin{cases}
(1-p_{cij})^\alpha log(p_{cij})       , & \text{if } y_{cij}=1\\
(1-y_{cij})^\beta (p_{cij})^\alpha log(1-p_{cij}), & \text{otherwise}
\end{cases}
```
where N is the number of objects in an image, and 
α and β are the hyper-parameters which control the contribution of each point (we set α to 2 and β to 4 in all experiments). 
α = ``$`\gamma`$`` in focal loss
With the Gaussian bumps encoded in ``$`y_{cij}`$`` , the ``$`(1-y_{cij})^\beta`$`` term reduces the penalty around the ground truth locations
### Corner pooling  Layer
It is one-stage detector with ~4fps (even slower than two-stage?)
### Backbone: Hourglass
Backbone for keypoints is important to keypoint estimation network. 
It is tested using hourglass increase 8.2 AP.
### CornerNet-Lite
real-time fps + higher AP than YOLO
## CenterNet: Keypoint Triplets for Object Detection (ICCV 2019)
[CenterNet: Keypoint Triplets for Object Detection](https://arxiv.org/abs/1904.08189)  
[中科院牛津华为诺亚提出CenterNet，one-stage detector可达47AP，已开源！](https://zhuanlan.zhihu.com/p/62789701)  
triplets: top-left + bottom right + center  
reduce incorrect bounding boxes via using predicted centre point to check if center keypoint of the same class falling within its central region

## ExtremeNet (CVPR 2019)
[Bottom-up Object Detection by Grouping Extreme and Center Points](https://arxiv.org/abs/1901.08043)  
based on [CornerNet](#cornernet-eccv-2018)  
predict 5 heatmaps: top, left, bottom, right, center + 4 offset map: top, left, bottom, right  
No embedding, brute center grouping  
code: [xingyizhou/ExtremeNet (PyTorch v0.4.1)](https://github.com/xingyizhou/ExtremeNet), developed upon CornerNet, fine-tuned on pre-trained CornerNet  
Disadvantage: for single-scale testing, AP lower than CornerNet, for larger objects. It is probably due to center response map is not accurate enough to perform well on large objects.

## CenterNet: Objects as Points (2019)
[Objects as Points](https://arxiv.org/abs/1904.07850) by same Author of [ExtremeNet](#extremenet-cvpr-2019)  
It is NOT [CenterNet: Keypoint Triplets for Object Detection](#centernet-keypoint-triplets-for-object-detection-iccv-2019)  
code: [xingyizhou/CenterNet (pyTorch)](https://github.com/xingyizhou/CenterNet)  
output: heatmap of center points (# of class channel) + width, height of pixel location (2 channels) + offset (2 channels)
### From points to bounding boxes (Inference)
0. Get network output keypoints ``$`\hat{Y}`$`` x number of class, offset ``$`O`$`` x 2 channels (x,y) and size ``$`S`$`` x 2 channels
1. extract the peaks in heatmap for each category independently
    1. detect all response whose value greater or equal to its 8 connected neighbors
    2. keep top n peaks ``$`\hat{P}_c`$``
2. For each keypoint in ``$`\hat{P}`$``, get it 2D location (i,j)
3. Get corresponding ``$`O_{i,j}`$``, ``$`S_{i,j}`$``
4. Produce bounding boxes
5. (Optional) Post-processing all boxes with NMS.
inference time: 28fps with DLA-34 backbone, 7.8fps with hourglass-104 (45.1 AP)
### Other applications
3D detection, Human pose estimation
### Backbone & Preformance
#### Object Detection on COCO validation

| Backbone     |  AP / FPS | Flip AP / FPS|  Multi-scale AP / FPS |
|--------------|-----------|--------------|-----------------------|
|[Hourglass](/CNN/object_detection/pose#hourglass-eccv-2016)-104 | 40.3 / 14 | 42.2 / 7.8   | 45.1 / 1.4            |
|[DLA](/CNN/models#deep-layer-aggregation-dla-cvpr-2018)-34        | 37.4 / 52 | 39.2 / 28    | 41.7 / 4              |
|ResNet-101    | 34.6 / 45 | 36.2 / 25    | 39.3 / 4              |
|ResNet-18     | 28.1 / 142| 30.0 / 71    | 33.2 / 12             |

hourglass is pre-trained in [ExtremeNet](#extremenet-cvpr-2019)
#### Keypoint detection on COCO validation

| Backbone     |  AP       |  FPS         |
|--------------|-----------|--------------|
|Hourglass-104 | 64.0      |    6.6       |
|DLA-34        | 58.9      |    23        |

### Center point collision
CenterNet is unable to predict <0.1% objects due to collision in center points. But this number is lower than collisions of anchors-based detector
### Remark
According to [issue 269: Comparing with ExtremeNet and CornerNet](https://github.com/xingyizhou/CenterNet/issues/269)  
, this paper is rejected because it is not all better than ExtremeNet. However, this model do not require grouping keypoints hence faster.

## TTFNet (AAAI 2020)
[Training-Time-Friendly Network for Real-Time Object Detection](https://arxiv.org/abs/1909.00700)  
based on [CenterNet: Objects as Points](#centernet-objects-as-points-2019)  
* using Gaussian kernels to encode training samples for center localization and size regression ~increasing batch size, so that enlarge the learning rate[(Accurate, Large Minibatch SGD: Training ImageNet in 1 Hour)](https://arxiv.org/abs/1706.02677) and accelerate the training process. (It predict ``$`(w_l, h_t, w_r, h_b)`$`` instead of size since the training sample of size regression is not only the center points
* initiative sample weight for better information utilization
result: balance training time while the accuracy and inference time still comparable to CenterNet