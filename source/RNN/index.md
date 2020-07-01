# Recurrent Neural Network - RNN
```math
h_t=f(Wx_t+U h_{t-1}+b)
```
## LSTM
[Long Short-term Memory (Neural Computation 1997)](https://www.researchgate.net/publication/13853244_Long_Short-term_Memory)  
vanilla RNNs gradients vanish or exploded during back-propagation. 
learning Long-Term Dependencies via cell state $C$  
[Understanding LSTM Networks -- colah's blog](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)

## GRU
[Empirical Evaluation of Gated Recurrent Neural Networks on Sequence Modeling (NIPS 2014)](https://arxiv.org/abs/1412.3555)  
simplified variant of LSTM

## FC-LSTM
[Learning precise timing with lstm recurrent networks (JMLR 2003)](http://www.jmlr.org/papers/volume3/gers02a/gers02a.pdf), [Generating Sequences With Recurrent Neural Networks (2013)](https://arxiv.org/abs/1308.0850)  
fully connected LSTM with peephole connection (add $C$ parameter into calucation of $f_t$, $i_t$ and $o_t$  
![](https://colah.github.io/posts/2015-08-Understanding-LSTMs/img/LSTM3-var-peepholes.png) from [colah](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)
## ConvLSTM
[Convolutional LSTM Network: A Machine Learning Approach for Precipitation Nowcasting (NIPS 2015)](https://papers.nips.cc/paper/5955-convolutional-lstm-network-a-machine-learning-approach-for-precipitation-nowcasting.pdf) - HKUST

