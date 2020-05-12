# Dimension Reduction
## PCA
Matrix Decomposition method  
project feature to max. variance  
### SVD
A better way to perform PCA that aovid huge computation of `$A^TA$`  
sklearn is using SVD algo for PCA function  
## eigenvector
Manifold  method
## t-SNE
t-distributed stochastic neighbor embedding  
Manifold method
```
class sklearn.manifold.TSNE(n_components=2, perplexity=30.0, early_exaggeration=12.0, learning_rate=200.0, n_iter=1000, n_iter_without_progress=300, min_grad_norm=1e-07, metric='euclidean', init='random', verbose=0, random_state=None, method='barnes_hut', angle=0.5, n_jobs=None)
```
### Barnes-Hut t-SNE
faster, limited to 2~3 dimension (but enough for visualization)
