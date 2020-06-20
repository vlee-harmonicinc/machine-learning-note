# 3D Reconstruction
[Paper with code](https://paperswithcode.com/task/3d-reconstruction)
## 3D RCNN (CVPR 2018)
[3D-RCNN: Instance-level 3D Object Reconstruction via Render-and-Compare](http://openaccess.thecvf.com/content_cvpr_2018/papers/Kundu_3D-RCNN_Instance-Level_3D_CVPR_2018_paper.pdf)

## Unsupervised Learning of Probably Symmetric Deformable 3D Objects from Images in the Wild
[Unsupervised Learning of Probably Symmetric Deformable 3D Objects from Images in the Wild (CVPR 2020 (Best Paper Award))](https://arxiv.org/abs/1911.11130)  
[Demo](http://www.robots.ox.ac.uk/~vgg/blog/unsupervised-learning-of-probably-symmetric-deformable-3d-objects-from-images-in-the-wild.html) | [Project Page](https://elliottwu.com/projects/unsup3d/) | [Video](https://www.youtube.com/watch?v=5rPJyrU-WE4)

Photo-Geometric Autoencoding: Our method is based on an **autoencoder** that factors each input image into **depth**, **albedo**, **viewpoint** and **lighting** (direction). These four components are combined to reconstruct the input image. The model is trained only using a reconstruction loss, without any external supervision.  
Exploiting Symmetry: depth and albedo flipped horizontally to obtain 2 reconsturctions.  
Probabilistic Modeling of Symmetry using Confidence Maps: adjust reconstruction loss for non-symmetric area.  
depth + albedo -> 3d model (output)  
depth + albedo + light + viewpoint -> render reconstructed image -> to compute loss