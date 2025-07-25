Statistics
=============
# Hypothesis Testing
# Estimation
## Properties
* Consistency: An estimator $\hat{\theta}_n$ is consistent if $\hat{\theta}_n \rightarrow \theta$ as $n \rightarrow \infty$
* Asymptotic Normality: An estimator $\hat{\theta}_n$ is asymptotically normal if 
## Maximum Likelihood
* The likelihood function maps parameter $\theta$ to the joint probability of observing all pieces of evidence $x_1, x_2, ..., x_n$.
```math
L_n(\theta) = p(x_1, ..., x_n) \stackrel{\text{iid}}{=} \prod_{i=1}^n p(x_i)
```
* We often think about the log-likelihood function as well.
```math
l_n(\theta) = \log p(x_1, ..., x_n) \stackrel{\text{iid}}{=} \sum_{i=1}^n \log p(x_i)
```
