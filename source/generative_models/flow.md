# Flow
Flow-based generative model
## NICE
[NICE: Non-linear Independent Components Estimation (2014)](https://arxiv.org/abs/1410.8516)
workshop paper at ICLR 2015  
optimize distribution by integration  
General coupling layer

merits:
* Exact latent-variable inference and log-likelihood evaluation
* Efficient inference and efficient synthesis
* Useful latent space for downstream tasks
[细水长flow之NICE：流模型的基本概念与实现](https://kexue.fm/archives/5776)
## realNVP
real-valued non-volume preserving  
generalize coupling layer, add convolution
## Glow
[Glow: Generative Flow with Invertible 1×1 Convolutions (2018)](https://arxiv.org/abs/1807.03039)
extends from NICE and RealNVP  
addition of a reversible 1x1 convolution, as well as removing other components, simplifying the architecture overall  
[Glow: Better Reversible Generative Models - OpenAI](https://openai.com/blog/glow/)  
BIG disadvantage: computation cost for training is too high  
256x256 high resolution face is in trained with 40 GPU for about a week. ~1 year for 1 GPU _(:3 J L)_
[github issue #37: anyone reproduced the celeba-HQ results in the paper](https://github.com/openai/glow/issues/37)
