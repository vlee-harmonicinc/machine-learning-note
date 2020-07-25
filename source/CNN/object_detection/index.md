# Detection
* [Object Detection](object_detection.md)
* [Keypoints based detector](keypoints_based.md)
* [Segmentation](segmentation.md)
* [Tracking](tracking.md)
* [Temporal Action Proposal Genration](temporal_proposal.md)
* [Measurement of Object Detection](measurement.md)
* [Face Recognition](face.md)
## Pose related
* [Pose Estimation](pose.md)
* [Action Recognition](action.md)
* [Motion Retargeting](motion_retargeting.md)

## History
![](img/detector_history.png)
## AP-fps

|Method                     |Backbone        |AP  |AP(MM)|FPS |GPU  |
|---------------------------|----------------|----|------|----|-----|
|Faster R-CNN               |                |34.9|      |    |     |
|Mask R-CNN                 |                |39.8|      |  11|     |
|Soft-NMS                   |                |40.9|      |    |     |
|RetinaNet-50-500           |                |32.5|      | 23 |     |
|RetinaNet-101-800          |                |37.8|      |5.1 |     |
|YOLOv3-608                 |                |33.0|      | 20 |     |
|RetinaNet-variant          |                |40.8|      |5.4 |     |
|CornerNet                  |hourglass-104   |40.6|  42.2|4.1 |Titan X|
|CornerNet                  |hourglass-104   |40.6|  42.2|3.3 |P100 - CenterNet (ICCV 2019)|
|FSAF                       |ResNet-50       |35.9|      | 9.3|Titan X - FSAF speed on COCO minival|
|FSAF (Anchor-based)        |ResNet-50       |37.2|      | 7.2|Titan X - FSAF|
|FSAF                       |ResNet-101      |37.9|      | 6.8|Titan X - FSAF|
|FSAF (Anchor-based)        |ResNet-101      |40.9|  42.8| 5.5|Titan X - FSAF|
|FSAF                       |ResNeXt-101     |41.0|      | 3.5|Titan X - FSAF|
|FSAF (Anchor-based)        |ResNeXt-101     |42.9|  44.6| 3.8|Titan X - FSAF|
|FSAF (Anchor-based)        |ResneXt-101     |42.9|  44.6| 2.7|TITAN Xp - CenterNet|
|CenterNet(ICCV 2019)       |hourglass-52    |41.6|  43.5|3.7 |P100|
|CenterNet(ICCV 2019)       |hourglass-104   |44.9|  47.0|2.9 |P100|
|ExtremeNet                 |hourglass-104   |40.2|  43.7|3.1 | |
|CenterNet                  |hourglass-104   |40.3|      |14  |TITAN Xp - CenterNet
|CenterNet                  |DLA-34          |37.4|      |52  |TITAN Xp - CenterNet
|CenterNet                  |DLA-34          |37.4|      |55.0|GTX 1080Ti - TTFNet
|CenterNet                  |ResNet-101      |34.6|      |45  |TITAN Xp - CenterNet
|CenterNet                  |ResNet-101      |34.6|      |44.7|GTX 1080Ti - TTFNet
|CenterNet                  |ResNet-18       |28.1|      |142 |TITAN Xp - CenterNet
|CenterNet                  |ResNet-18       |28.1|      |128.5|GTX 1080Ti - TTFNet
|TTFNet                     |ResNet-18       |25.9|      |112.2|GTX 1080Ti - TTFNet | lower training time
|TTFNet                     |Darknet-53      |35.1|      |54.4|GTX 1080Ti - TTFNet
|TTFNet(10x)                |Darknet-53      |39.3|      |57.0|GTX 1080Ti - TTFNet

MS: multi. scale
