# Maxium Likelihood Estimation (MLE)
The Maximum Likelihood Estimation (MLE) is a method of estimating the parameters of a model.
The central idea behind MLE is to select that parameters (θ) that make the observed data the most likely.
[Stanford cs109 Lecture Note 20](http://web.stanford.edu/class/cs109/lectureNotes/LN20_parameters_mle.pdf)([archive](/_static/pdf/LN20_parameters_mle.pdf)) by [David Varodayan](https://web.stanford.edu/~divad/) have great and simple equations of Bernoulli, Poisson, Normal distribution with probability mass function to measure likelihood.  
[5.5 Maximum Likelihood Estimation of deep learning book](https://www.deeplearningbook.org/contents/ml.html) also teach MLE details with KL divergence to measure dissimilarity with condition `$P(y|x;\theta)$`.
Max likelihood->min negative log-likelihood -> min cross-entropy
