Classifcation Intro
=====================
# What is classification?
* Supervised learning technique where $x$ is a feature vector of size $d$ and $y$ is a finite discrete value $\set{1, 2, ..., k\}$.

# Discriminant Analysis
## Quadratic Discriminant Analysis
* Assume $x | y=k \sim N(\mu_k, \Sigma_k)$ and that $p(y=k) = \pi_k$
* By Bayes Rule, we have:

$$
p(y = k | x) \propto p(x | y = k) * p(y = k) = \pi_k N(x | \mu_k, \Sigma_k) 
$$

* Inference Rule:

$$
\max_k \log p(y = k | x) = \underbrace{\log \pi_k + \log N(x | \mu_k, \Sigma_k)}_{d_k(x)}
$$

* $d_k(x)$ is called discriminant

$$
d_k(x) = \log \pi_k - \frac{1}{2} (x - \mu_k)^T \Sigma_k^{-1} (x - \mu) - \frac{1}{2} \log | \Sigma_k |
$$

* TODO: Training

## Linear Discriminant Analysis
* Instead of assuming that we have a different covariance matrix for each class we assume that all class distributions share a global covariance matrix $\Sigma$
* Discriminant becomes:

$$
d_k(x) \equiv \log \pi_k - \frac{1}{2} (x - \mu_k)^T \Sigma^{-1} (x - \mu_k) \equiv \log \pi_k - \frac{1}{2} (-2 x^T \Sigma^{-1} \mu_k + \mu_k^T \Sigma^{-1} \mu_k^T)
$$

* Quadratic term $x^T \Sigma^{-1} x$ falls out of discriminant since it does not depend on $k$.

## Naive Bayes
* Naive Bayes are a set of models that assume that all features of $x_j$ are conditional independent given $y$ (Naive Bayes Assumption). 
* We can simplify discriminants as:

$$
d_k(x) = \log p(y = k | x) = \log p(y = k) + \log p(x | y = k) = \log p(y = k) + \sum_{j=1}^d \log p(x_j | y = k)
$$

### Example: Naive Bayes QDA
* Under the Naive Bayes assumption, the covariance matrix is diagonal. 

$$
d_k(x) = \log \pi_k - \frac{1}{2} \sum_{j=1}^d \frac{(x_j - \mu_{kj})^2}{\sigma_{kj}^2}
$$

* With QDA we have to estimate:
  * $K$ params for priors
  * $K$ vectors of size $d$ for means
  * $K$ matrices of size $d \times d$ for covariances
* Naive Bayes reduces param count of varainces to just $Kd$  

## Logistic Regression



