# Basic Layer Types
## Fully connected
## RNN
### LSTM
### GRU
### models
#### seq2seq
#### attention model
## CNN (convolutional neural network)
### Convolution
![image convolution](/img/image_convolution.png)

remain same size (with padding) or slightly smaller size (without padding)
### Receptive Field
### skip connection
see [U-net], [ResNet]
### downscale
stride, pooling or resize
less computation required 
get high level features
#### Stride vs pooling
---------
|stride|pooling|
|---|--|-----|
computation|less|4 times more computation+pooling operate
gradient propagation|bad|better
upscale|
could propagate with pooling indice
### upscale / up-sampling
used for 1. reverse downscale 2. increase resolution
usually required for pix 2 pix application, e.g. segmentation, super-resolution
#### Methods:
1. resize  
resampling and interpolation
2. un-pooling (if pooling is used)  
[DeconvNet]
3. Transposed Convolution (deconvolution)
4. pixel shuffle (sub-pixel convolution)
[Real-Time Single Image and Video Super-Resolution Using an Efficient Sub-Pixel Convolutional Neural Network (2016)](https://arxiv.org/abs/1609.05158)
#### 1x1 convolution
could be used for changing the number of features
see [Inception (2014)](CNN/inception.md)
[ACNet: Strengthening the Kernel Skeletons for Powerful CNN via Asymmetric Convolution Blocks (ICCV 2019)](https://arxiv.org/abs/1908.03930)
