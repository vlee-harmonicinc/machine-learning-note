# UNIT series
## UNIT
[Unsupervised Image-to-Image Translation Networks (NIPS 2017)](https://arxiv.org/abs/1703.00848) by Nvidia  
Seperate the generator of GAN into encoder+decoder pairs, just like VAE.  
**Shared-latent space** constraint implies the cycle-consistency constraint.  
VAE + GAN + share weight of last layer of E1 and E2; also share the first layer of G1, G2  
![](img/UNIT.png)  
Cycle-consistency is not necessary for this task, however, preformance: proposed(UNIT-shared latent space + cycle-consistency) > cycleGAN > shared latent space (VAE-GAN)  
comparing with cycleGAN, it learn shape better.  
## MUNIT
[Multimodal Unsupervised Image-to-Image Translation (ECCV 2018)](https://arxiv.org/abs/1804.04732)  
1. seperate latent code into content code and style code, learn from swapping attribute code  
1. style is embedded in hidden layer of generator  
![](img/MUNIT.png)
## DRIT
[Diverse Image-to-Image Translation via Disentangled Representations (ECCV 2018)](https://arxiv.org/abs/1808.00948)  
[Project](http://vllab.ucmerced.edu/hylee/DRIT_pp/) | [Pytorch 0.4.0](https://github.com/HsinYingLee/DRIT/)  
1. concurrent works of MUNIT, style code in MUNIT~attribute code in DRIT  
1. keep weight sharing of UNIT
1. add content adversarial loss to force content generator produce encoding that could not be distingished, same concept of [Transfer Learning/DANN](/transfer_learning/index.html#dann-nips-2014)
### DRIT++
[DRIT++: Diverse Image-to-Image Translation via Disentangled Representations (IJCV Journal extension for ECCV 2018)](https://arxiv.org/abs/1905.01270) 
1. mode-seeking regularization for improving sample diversity [Mode Seeking GAN](GAN_general.html#mode-seeking-gan-cvpr-2019)
1. add one-hot domain code

## FUNIT
[Few-Shot Unsupervised Image-to-Image Translation (ICCV 2019)](https://openaccess.thecvf.com/content_ICCV_2019/papers/Liu_Few-Shot_Unsupervised_Image-to-Image_Translation_ICCV_2019_paper.pdf)  
[Project page](https://nvlabs.github.io/FUNIT/) | [pyTorch](https://github.com/NVlabs/FUNIT) | [FUNIT Explained](https://youtu.be/kgPAqsC8PLM) | [GANimal Demo Video](https://youtu.be/JTu-U0C4xEU) | [Have fun with GANimal](https://nvlabs.github.io/FUNIT/ganimal.html)  

## TUNIT
[Rethinking the Truly Unsupervised Image-to-Image Translation (2020)](https://arxiv.org/abs/2006.06500) - Clova AI  
[pyTorch 1.1](https://github.com/clovaai/tunit) | 
[reddit](https://www.reddit.com/r/MachineLearning/comments/h8qhsg/r_rethinking_the_truly_unsupervised_imagetoimage/) | 
[Twitter](https://twitter.com/KyungjuneB/status/1272093489635835904) | [youtube](https://www.youtube.com/watch?v=sEG8hD64c_Q&feature=youtu.be)  
*Truly unsupervised*: no any supervision, neither image-level(paired) or set-level (unpaired, domain)  
similar to styleGAN? but styleGAN assume no domain as all while TUNIT assume dataset have dmoain, but it is unknown in training dataset. TUNIT learn to produce domain label via [IIC](https://arxiv.org/abs/1807.06653) clustering.
