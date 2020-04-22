# AutoML

## Survery
[Taking Human out of Learning Applications: A Survey on Automated Machine Learning](https://arxiv.org/abs/1810.13306)

### Automated model selection
#### Simple Search
* Grid search
* Random search
#### Derivative-Free Optimization
* Heuristic Search
* Model-Based Derivative-Free Optimization
    * Bayesian Optimization: builds a probabilistic model
        * Gaussian process
        * Tree-based model
        * Deep network

### Neural Architecture serach

### Automated Feature Engineering
#### Feature Enhancing Methods
##### Dimension reduction
* PCA -Principal components analysis [On lines and planes of closest fit to systems of points in space (1901)]
* LDA -Linear Discriminant Analysis [The use of multiple measurements in taxonomic problems]
* Auto-encoders [Extracting and composing robust features with denoising autoencoders](https://www.researchgate.net/publication/221346269_Extracting_and_composing_robust_features_with_denoising_autoencoders)
##### Feature generation
##### Feature encoding

## Papers
### MnasNet (CVPR 2019)
[MnasNet: Platform-Aware Neural Architecture Search for Mobile](https://arxiv.org/abs/1807.11626) by Google  

### NAS-FPN (CVPR 2019)
[NAS-FPN: Learning Scalable Feature Pyramid Architecture for Object Detection](https://arxiv.org/abs/1904.07392)

### EfficientNet (ICML 2019)
[EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks](https://arxiv.org/abs/1905.11946) by Google Brain  
[Blog](https://ai.googleblog.com/2019/05/efficientnet-improving-accuracy-and.html) | 
[Code: tensorflow/tpu/models/official/efficientnet](https://github.com/tensorflow/tpu/tree/master/models/official/efficientnet)  
[如何评价谷歌大脑的EfficientNet？ - 知乎](https://www.zhihu.com/question/326833457)  
used in [EfficientDet](/CNN/object_detection/object_detection.html#efficientdet-cvpr-2020)

## Others
[Google's AutoML: Cutting Through the Hype](https://www.fast.ai/2018/07/23/auto-ml-3/)
Neural architecture search vs. transfer learning: two opposite approaches

~[[D\] Google's AutoML: Cutting Through the Hype](https://www.reddit.com/r/MachineLearning/comments/91fpbi/d_googles_automl_cutting_through_the_hype/)
grad student descent lol~