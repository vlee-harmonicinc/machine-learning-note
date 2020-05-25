# NLP

## word2vec (NIPS 2013)
[Efficient estimation of word representations in vector space (ICLR 2013)](https://arxiv.org/abs/1301.3781)  
an encoder to embed words (reduce dimension) with 2 tasks:
* Skip-gram: given the word, predict the context (before / after the input)
* Continuous Bag of Words (CBOW): given the surrounding words, predict the word in the middle

input: verb encoding/ one-hot encoding  
output: huffman tree encoding (a searching efficent one-hot)

Use the hidden layer as embedding for other tasks (Transfer learning)

[Distributed Representations of Words and Phrases and their Compositionality (NIPS 2013)](https://papers.nips.cc/paper/5021-distributed-representations-of-words-and-phrases-and-their-compositionality.pdf)  
1. subsampling of the frequent words
1. Negative Sampling (alt to Hierarchical Softmax)

[google code archive](https://code.google.com/archive/p/word2vec/)

[word2vec Parameter Learning Explained](https://arxiv.org/abs/1411.2738)

[The Illustrated Word2vec](https://jalammar.github.io/illustrated-word2vec/)


## ELMo (NAACL 2018)
[Deep contextualized word representations](https://arxiv.org/abs/1802.05365)  
**E**mbeddings from **L**anguage **Mo**dels  
[code](https://allennlp.org/elmo)  
LSTM


## BERT (2018)
Bidirectional Encoder Representations from Transformers  
[BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805)  
[Google AI Blog: Open Sourcing BERT: State-of-the-Art Pre-training for Natural Language Processing](https://ai.googleblog.com/2018/11/open-sourcing-bert-state-of-art-pre.html)  
[\[R\] BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://www.reddit.com/r/MachineLearning/comments/9nfqxz/r_bert_pretraining_of_deep_bidirectional/)  
[The Illustrated BERT, ELMo, and co. (How NLP Cracked Transfer Learning)](http://jalammar.github.io/illustrated-bert/)  



Tasks:
1. Sentence Pair Classification
2. Single Sentence Classification
3. Question Answering
4. Single Sentence Tagging