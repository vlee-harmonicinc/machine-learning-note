# Recurrent Neural Network - RNN
```math
h_t=f(Wx_t+U h_{t-1}+b)
```
## LSTM (Neural Computation 1997)
[Long Short-term Memory](https://www.researchgate.net/publication/13853244_Long_Short-term_Memory)  
vanilla RNNs gradients vanish or exploded during back-propagation. 
learning Long-Term Dependencies via cell state $C$  
[Understanding LSTM Networks -- colah's blog](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)
## GRU (NIPS 2014)
[Empirical Evaluation of Gated Recurrent Neural Networks on Sequence Modeling](https://arxiv.org/abs/1412.3555)  
simplified variant of LSTM
## seq2seq