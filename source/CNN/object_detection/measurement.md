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