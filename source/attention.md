# Attention Mechanism
Attention mechanism mainly used for NLP because of sequence model. CNN could also use self-attention, such as SAGAN.

## Background
Before RNNsearch, sequence model is mostly implemented via RNN encoder-decoder. RNN could somehow handle sequence data, but it is heavely rely on the previous data (word for NLP), which is not flexible enough for language model.
### seq2seq
[Sequence to Sequence Learning with Neural Networks (NIPS 2014)](https://papers.nips.cc/paper/5346-sequence-to-sequence-learning-with-neural-networks.pdf)
> **multilayered LSTM** to map the input sequence to a vector of a fixed dimensionality, and then another deep LSTM to decode the target sequence from the vector.  

## RNNsearch
[Neural Machine Translation by Jointly Learning to Align and Translate (2014~ICLR 2015)](https://arxiv.org/abs/1409.0473)  
> In this paper, we conjecture that the use of a fixed-length vector is a bottleneck in improving the performance of this basic encoder-decoder architecture, and propose to extend this by allowing a model to **automatically (soft-)search for parts of a source sentence that are relevant to predicting a target word**, without having to form these parts as a hard segment explicitly.

## Show, Attend and Tell
[Show, Attend and Tell: Neural Image Caption Generation with Visual Attention (ICML 2015)](https://arxiv.org/abs/1502.03044)  
Generate word by word based on image

## Transformer
[Attention is all you need (NIPS 2017)](https://arxiv.org/abs/1706.03762) - Google  
[google AI blog](https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html) | 
[The Illustrated Transformer](http://jalammar.github.io/illustrated-transformer/) | 
[The Annotated Transformer - Harvard](http://nlp.seas.harvard.edu/2018/04/03/attention.html)
*Self-attention*: sometimes called *intra-attention* is an attention mechanism relating different positions of a single sequence in order to compute a representation of the sequence. (For previous non-self attention, decoder consider the output of encoder. For self-attention, layer (both encoder or decoder) consider other repersentation within sequence.
### Scaled Dot-Product Attention
![](http://nlp.seas.harvard.edu/images/the-annotated-transformer_33_0.png)
The input consists of queries `$Q$` and keys `$K$` of dimension `$d_k$`, and values `$V$` of dimension `$d_v$` (channel of features)
$$ Attention(Q, K, V) = softmax(\frac{QK^T}{sqrt{d_k}})V $$
### Multi-Head Attention
![small_img](http://nlp.seas.harvard.edu/images/the-annotated-transformer_38_0.png)  
$$
MultiHead(Q,K,V) = Concat(head_1,...,head_h)W^O \\
where head_i = Attention(QW_i^Q,KW_i^K,VW_i^V)
$$
Due to the reduced dimension of each head, the total computational cost is similar to that of single-head attention with full dimensionality.

## Non-local Neural Networks
[Non-local Neural Networks (CVPR 2018)](https://arxiv.org/pdf/1711.07971.pdf)  
[Caffe code](https://github.com/facebookresearch/video-nonlocal-net)  
spacetime Non-local block

## CBAM
[CBAM: Convolutional block attention module(ECCV 2018)](https://eccv2018.org/openaccess/content_ECCV_2018/papers/Sanghyun_Woo_Convolutional_Block_Attention_ECCV_2018_paper.pdf)
### Channel attention module (CAM)
### Spatial Attention Module (SAM)

## An Empirical Study of Spatial Attention Mechanisms in Deep Networks 
[An Empirical Study of Spatial Attention Mechanisms in Deep Networks (ICCV 2019)](http://openaccess.thecvf.com/content_ICCV_2019/papers/Zhu_An_Empirical_Study_of_Spatial_Attention_Mechanisms_in_Deep_Networks_ICCV_2019_paper.pdf) from MSRA
