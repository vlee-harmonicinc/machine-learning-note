# Inpaint
## Context encoder
[Context Encoders: Feature Learning by Inpainting (CVPR 2016)](https://arxiv.org/abs/1604.07379)  
[Project](https://people.eecs.berkeley.edu/~pathak/context_encoder/) | [torch code](https://github.com/pathak22/context-encoder)
Semantic Image Inpainting with Deep Generative Models  
GAN with encoding manifold, weighted context loss
## Globally and Locally Consistent Image Completion
[Globally and Locally Consistent Image Completion (SIGGRAPH 2017)](http://iizuka.cs.tsukuba.ac.jp/projects/completion/data/completion_sig2017.pdf)  
[Project](http://iizuka.cs.tsukuba.ac.jp/projects/completion/en/)  
![](img/completion_model.png)
* global discriminator + local(patch) discriminator

# Image synthesis
## Stereo Magnification
[Stereo Magnification: Learning View Synthesis using Multiplane Images (SIGGRAPH 2018)](http://people.eecs.berkeley.edu/~tinghuiz/papers/siggraph18_mpi_lowres.pdf)  
[Project](https://people.eecs.berkeley.edu/~tinghuiz/projects/mpi/) | [google/stereo-magnification tensorflow](https://github.com/google/stereo-magnification) | [Dataset: RealEstate10K](https://google.github.io/realestate10k/)
* input: frames triplet with camera trajectories

## 3D Photo Inpant
[3D Photography using Context-aware Layered Depth Inpainting (CVPR 2020)](https://arxiv.org/abs/2004.04727)  
[Project Website](https://shihmengli.github.io/3D-Photo-Inpainting/) | [PyTorch](https://github.com/vt-vl-lab/3d-photo-inpainting) | [Google Colab](https://colab.research.google.com/drive/1706ToQrkIZshRSJSHvZ1RuCiM__YX3Bz)  
* input: RGB-D iamge
![](https://camo.githubusercontent.com/8dd5b529c99cdfcedd043c8239b68c4d7a23a148/68747470733a2f2f66696c65626f782e6563652e76742e6564752f7e6a626875616e672f70726f6a6563742f334450686f746f2f334450686f746f5f7465617365722e6a7067)

## Dynamic Scenes View
[Novel View Synthesis of Dynamic Scenes with Globally Coherent Depths from a Monocular Camera (CVPR 2020)](http://openaccess.thecvf.com/content_CVPR_2020/html/Yoon_Novel_View_Synthesis_of_Dynamic_Scenes_With_Globally_Coherent_Depths_CVPR_2020_paper.html)  
[Project - Nvidia](https://research.nvidia.com/publication/2020-06_Dynamic-Scene-View) | [Youtube](https://www.youtube.com/watch?v=S8_0V3fZIes)
* monocular view synthesis of a dynamic scene
