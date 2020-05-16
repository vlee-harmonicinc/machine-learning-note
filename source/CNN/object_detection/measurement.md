# Measure Object Detection

## Precision, Recall, and F1
```math
\begin{split}
&Precision &= \dfrac{TP}{\text{total detection}}&= \dfrac{TP}{TP+FP}\\
&Recall &= \dfrac{TP}{\text{total positive}}    &= \dfrac{TP}{TP+FN}\\
&F1&=\dfrac{precision\cdot recall}{precision+recall}\\

&TP=\text{True Positive}\\
&TN=\text{True Negative}\\
&FP=\text{False Positive}\\
&FN=\text{False Negative}\\
\end{split}
```
## Intersection over union, IoU
consider area of Ground Truth and area of Prediction
```math
IoU = \dfrac{\text{area of overlap}}{\text{area of union}}
```
It is used to define Positive or negative  
## Non-Maximum Suppression, NMS
To filter overlapped object
## mean Average Precisiion, mAP
When The confident level threshold increase, the precision decrease and recall increase.  
Average Precision is the area under the precision-recall curve, with a confident or IoU threshold  
```math
AP = \int_0^1p(r)dr
```
In Pascal VOC, an average for the 11-point interpolated AP is calculated. [0, 0.1, 0.2, 0.3, ...1.0]  
## COCO AP
[Detection Evaluation - COCO](http://cocodataset.org/#detection-eval)

Average Precision (AP)|-
-------------|---
`$AP$`        |% AP at IoU=.50:.05:.95 (primary challenge metric)
`$AP^{IoU=.50}$`|% AP at IoU=.50 (PASCAL VOC metric)
`$AP^{IoU=.75}$`|% AP at IoU=.75 (strict metric)

AP Across Scales|-
---|---
`$AP^{small}$` |% AP for small objects: area < 322
`$AP^{medium}$`|% AP for medium objects: 322 < area < 962
`$AP^{large}$` |% AP for large objects: area > 962

Average Recall (AR)|-
---|---
`$AR^{max=1}$`|% AR given 1 detection per image
`$AR^{max=10}$`|% AR given 10 detections per image
`$AR^{max=100}$`|% AR given 100 detections per image

AR Across Scales|-
---|---
`$AR^{small}$`|% AR for small objects: area < 322
`$AR^{medium}$`|% AR for medium objects: 322 < area < 962
`$AR^{large}$`|% AR for large objects: area > 962