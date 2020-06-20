# Decision Tree
interpretable and intuitive model

## Information Theory
### Entropy
Measure the impurity of the attribute, that will be used to select the atrribute to be splited.  
The lower Entropy -> distribution varied (not uniform) -> more information for prediction
$$ H(X) = - \sum^y_{y\in Y}P(y)log_2P(y) $$
### Conditional Entropy
$$
H(A|S) = -\sum^x_{x \in S} P(x) \sum^y_{y \in A}P(y|x)log_2 P(y|x)
$$
For decision tree, take data in dataset `$S$` (of current branch) as `$x$`, attribute as `$y$`
### Information Gain
```math
Gain(S, A)  &= \text{expected reduction in entropy due to branching on attribute A} \\
            &= \text{original entropy} - \text{entropy after branching} \\
            &= H(S) - H(A|S)
```
Compute for all attributes, lower Entropy -> higher gain
$$arg max_x Gain(x) = arg max_x H(Y) - H(Y|X) = arg min_x H(Y|X)$$
#### Continus
```math
H(Y|X:t) &= p(X <t) H(Y|X < t) + p(X >= t) H(Y|X >= t) \\
Gain(Y|X:t) &= H(Y) - H(Y|X:t)  \\
Gain*(Y|X) &= max_t IG(Y|X:t)
```
### Gain Ratio
One problem with Gain is that it likes to partition too much, and favors numerous splits. 
```math
\frac{Gain(S,A)}{SplitInfo(S,A)}
```
```math
SplitInfo(S,A)=-\sum^J_{j=1}\frac{|S_j|}{|S|}log(\frac{|S_j|}{|S|})\\  \text{, where } |S_j| = \text{the number of data in splited }branch j
```
## Pruning
avoid Overfit

## Methods
1. Chi-square automatic interaction detection, CHAID (1974)
1. Classification and regression tree, CART (1984)
1. Iterative Dichotomiser 3, ID3 (1986)
1. successor of ID3, C4.5 (1993)
### CHAID

### CART
* GINI index
* binary splits
* Regression
    - (usually) average output number of data in current branch
    - (usually) object function: square error
    - mininize object function
### ID3
* Information Gain
1. Calculate the entropy of every attribute `${\displaystyle a}$` of the data set `${\displaystyle S}$`.
1. Partition ("split") the set `${\displaystyle S}$` into subsets using the attribute for which the resulting entropy after splitting is minimized; or, equivalently, information gain is maximum.
1. Make a decision tree node containing that attribute.
1. Recurse on subsets using the remaining attributes.
### C4.5
1. Check for the base cases.
1. For each attribute a, find the normalized information **gain ratio** from splitting on a.
1. Let a_best be the attribute with the highest normalized information gain.
1. Create a decision node that splits on a_best.
1. Recurse on the sublists obtained by splitting on a_best, and add those nodes as children of node.

* Handling both **continuous** and discrete attributes - In order to handle continuous attributes, C4.5 creates a *threshold* and then splits the list into those whose attribute value is above the threshold and those that are less than or equal to it.
* **Pruning** trees after creation - C4.5 goes back through the tree once it's been created and attempts to remove branches that do not help by replacing them with leaf nodes.
    * Options
        1. leaving the tree as is
        1. replace that part of the tree with a leaf corresponding to the most frequent label in the data S going to that part of the tree.
        1. replace that part of the tree with one of its subtrees, corresponding to the most common branch in the split
    * compute the upper bound of probability of error with fixed $\alpha=0.25$
    * Select options with smallest upper bound
* Handling training data with missing attribute values - C4.5 allows attribute values to be marked as ? for missing. Missing attribute values are simply not used in gain and entropy calculations.
* Handling attributes with differing costs.

ref: [MIT15_097S12_lec08](https://ocw.mit.edu/courses/sloan-school-of-management/15-097-prediction-machine-learning-and-statistics-spring-2012/lecture-notes/MIT15_097S12_lec08.pdf)

# Random Forest
Generate M randomize decision tree, take majority vote branch
## Randomize methods
1. Bagging: each tree is grown using a bootstrap sample of training data
1. Random Vector: At each node, best split is chosen from a random sample of attributes instead of all attributes.
# Gradient Boosting Decision Tree
For the current branch `$F_j$` learn the gradient
For square loss, gradient = residual = `$y_i-F_{j-1}(x_i)$` =true value - predicted value = true y - mean value of data in branch
## XGBoost
## Light GBM
## CatBoost