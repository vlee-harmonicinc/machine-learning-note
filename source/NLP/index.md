# NLP
Application:
0. word embedding (base of all other NLP task)
1. Sentence Pair Classification
2. Single Sentence Classification
3. Question Answering
4. Single Sentence Tagging

## word2vec
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

[google code archive](https://code.google.com/archive/p/word2vec/) | 
[word2vec Parameter Learning Explained](https://arxiv.org/abs/1411.2738) | 
[The Illustrated Word2vec](https://jalammar.github.io/illustrated-word2vec/)

## GloVe
Global Vectors for Word Representation
[Project page](https://nlp.stanford.edu/projects/glove/)

## ELMo
**E**mbeddings from **L**anguage **Mo**dels  
[Deep contextualized word representations (NAACL 2018)](https://arxiv.org/abs/1802.05365) | 
[AllenNLP code](https://allennlp.org/elmo)  
bi-LSTM  
Contextual/context-sensitive features: instead generate a representation of each word that is based on the other words in the sentence.  
ELMo collapses all layers in R into a single vector.  
The contextual representation of each token is the concatenation of the left-to-right and right-to-left(single direction) representations

## GPT
[Improving Language Understanding by **Generative Pre-Training** (2018)](https://s3-us-west-2.amazonaws.com/openai-assets/research-covers/language-unsupervised/language_understanding_paper.pdf) | [OpenAI blog](https://openai.com/blog/language-unsupervised/)  
Using Transformer, undirectional  
### GPT-3
[Language Models are Few-Shot Learners](https://arxiv.org/abs/2005.14165) - OpenAI  
It is not open-source and the computation cost is high even for inference. OpenAI provide API.
### Image GPT
[OpenAI blog](https://openai.com/blog/image-gpt/)

## BERT
**B**idirectional **E**ncoder **R**epresentations from **T**ransformers  
[BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding (2018)](https://arxiv.org/abs/1810.04805) | 
[Google AI Blog](https://ai.googleblog.com/2018/11/open-sourcing-bert-state-of-art-pre.html) | 
[Reddit](https://www.reddit.com/r/MachineLearning/comments/9nfqxz/r_bert_pretraining_of_deep_bidirectional/)  
<!--[The Illustrated BERT, ELMo, and co. (How NLP Cracked Transfer Learning)](http://jalammar.github.io/illustrated-bert/) -->  
almost identical to the original [Attention is all you need](../attention.html#transformer)  
2 Training task:
1. Masked LM: CBOW cannot be used to traing on multi-layer bi-directional model because it "see itself". 15% words selected; 80% changed to "masked" label, 10% changed to other word, 10% unchanged.
1. Next Sentence Prediction
### Multi-Head Attention
Attention in same layer could be shared to reduce computational cost.
[What Does BERT Look At? An Analysis of BERT’s Attention (BlackBoxNLP 2019)](https://arxiv.org/abs/1906.04341) - analyse the attention heads
