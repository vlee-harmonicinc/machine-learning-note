# Video Synthesis

## vid2vid
[Video-to-Video Synthesis (NeurIPS 2018)](https://arxiv.org/abs/1808.06601) | 
[Video-to-Video Synthesis](https://tcwang0509.github.io/vid2vid/) | 
[github](https://github.com/NVIDIA/vid2vid) - by Nvidia (Includes works of pix2pixHD and SPADE)  
conditional GAN + optical flow given paired data. 
![img](https://tcwang0509.github.io/vid2vid/images/teaser.gif)
<iframe width="1024" height="575" src="https://www.youtube.com/embed/5zlcXTCpQqM" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Deep Video-Based Performance Cloning
[Deep Video-Based Performance Cloning (2018/ Eurographics 2019)](https://arxiv.org/pdf/1808.06847.pdf) - Kfir Aberman  
conditional GAN + optical flow, concurrent with vid2vid. Used in [Learning Character-Agnostic Motion for Motion Retargeting in 2D](../pose/motion_retargeting.md#lcm) (Same author)

## Everybody Dance Now
[Everybody Dance Now (ICCV 2019)](../pose/motion_retargeting.md#edn)

## Few-shot vid2vid
[Few-shot Video-to-Video Synthesis (NeurIPS 2019)](https://arxiv.org/pdf/1910.12713.pdf) - Nvidia | [PyTorch 1.2](https://github.com/NVlabs/few-shot-vid2vid)  
Above auto-encoder models (vid2vid, EDN) do not consider generalization to unseen domains. 
For example, for pose transfer, above models train with dataset of single person, and the person is remembered by the decoder. 
To synthesize a new person, one needs to collect a dataset of the new person and uses it to train a new vid2vid model. 

Few-Shot vid2vid can synthesize videos of new persons without re-training by leveraging few example images as input provided during inference.  

conditional GAN + attention
![img](https://github.com/NVlabs/few-shot-vid2vid/blob/master/imgs/dance.gif?raw=true)
Note: it is kinda based on optical flow, not fully generative. The sample output a bit looks like moving and stretching the body part to target location, just like optical flow based frame interpolation.
