Statistics
=============
# Hypothesis Testing
## Terminology
* Hypothesis testing is a statistical method that uses data to make yes or no inferences about a population.
* Null hypothesis $H_0$ is a statement that usually indicates the status quo such as a new drug having no effects.
* Alternative hypothesis $H_1$ is a statement contradicting the null hypothesis.
* The hypothesis test can either accept the null hypothesis or reject the null hypothesis (note we don't accept the alternative hypothesis.
* A type I error (also known as false positive) indicates that we incorrectly rejected the null hypothesis.
* A type II error (also known as a miss) indicates that we incorrectly accepted the null hypothesis.

|              | H_0      | H_1     |  
| ------------ | -------- | ------- |
| Accepted H_0 | Correct  | Type II |
| Rejected H_0 | Type I   | Correct |


## 

# Estimation
## Terminology
* Estimator: An estimator is a random variable computed from sample data that approximates the true value of a parameter. 
* Bias: 
* Weak Consistency: An estimator $\hat{\theta}_n$ is weakly consistent if $\hat{\theta}_n \xrightarrow{p} \theta$ as $n \rightarrow \infty$.
* Strong Consistency: Similar to weak consistency, but converges almost surely.
* Asymptotic Normality: An estimator $\hat{\theta}_n$ is asymptotically normal if
```math
\sqrt{n} (\hat{\theta}_n - \theta \xrightarrow{d} N(0, \sigma^2)
```

## Confidence Intervals
* A confidence interval with confidence level $1 - \alpha$ is a random interval $I$ such that the probability of $I$ capturing the true parameter is at least $1 - \alpha$
```math
P(I \ni \theta) \ge 1 - \alpha
```
* An asymptotic CI means that the bound holds in the limit as our sample size increases. 
* Asymptotic normality allows us to construct confidence intervals for point estimators.

### The Delta Method


## Maximum Likelihood
* The likelihood function maps parameter $\theta$ to the joint probability of observing all pieces of evidence $x_1, x_2, ..., x_n$.
```math
L_n(\theta) = p(x_1, ..., x_n) \stackrel{\text{iid}}{=} \prod_{i=1}^n p(x_i)
```
* The goal of maximum likelihood is to find the parameter that maximizes the likelihood of the observed data.  
* In many cases, we instead maximize the log-likelihood function instead,
```math
l_n(\theta) = \log p(x_1, ..., x_n) \stackrel{\text{iid}}{=} \sum_{i=1}^n \log p(x_i)
```
### Relationship to KL Divergence
