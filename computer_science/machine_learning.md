Machine Learning
=====================
# Classifcation Intro
* Supervised learning technique where $x$ is a feature vector of size $d$ and $y$ is a finite discrete value $\set{1, 2, ..., k\}$.

## Discriminant Analysis
### Quadratic Discriminant Analysis
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

### Linear Discriminant Analysis
* Instead of assuming that we have a different covariance matrix for each class we assume that all class distributions share a global covariance matrix $\Sigma$
* Discriminant becomes linear if we eliminate terms that do not depend on $k$:

$$
d_k(x) \equiv \log \pi_k - \frac{1}{2} (x - \mu_k)^T \Sigma^{-1} (x - \mu_k) \equiv \log \pi_k - \frac{1}{2} (-2 x^T \Sigma^{-1} \mu_k + \mu_k^T \Sigma^{-1} \mu_k^T)
$$

### Naive Bayes
* Naive Bayes are a set of models that assume that all features of $x_j$ are conditional independent given $y$ (Naive Bayes Assumption). 
* We can simplify discriminants as:

$$
d_k(x) = \log p(y = k | x) = \log p(y = k) + \log p(x | y = k) = \log p(y = k) + \sum_{j=1}^d \log p(x_j | y = k)
$$

### Example: Naive Bayes QDA
* Under the Naive Bayes assumption, the covariance matrix is diagonal $\Sigma_k = \text{diag}(\sigma_k)$. 

$$
d_k(x) = \log \pi_k - \frac{1}{2} \sum_{j=1}^d \frac{(x_j - \mu_{kj})^2}{\sigma_{kj}^2}
$$

* With QDA we have to estimate $Kd^2$ covarances. 
* Naive Bayes reduces param count of varainces to just $Kd$  

### Logistic Regression
* Binary classification technique. We assume that $y$ is either $0$ pr $1$
* Assume that $y | x$ is a Bernoulli distribution where the probability $y=1 | x$ is $g(w^Tx)$.
  * $g$ is often a sigmoid function since it maps between $[0, 1]$
  * $w$ are the parameters of our model.

$$
p(y | x) = p(y=1 | x) ^ {\delta_{1y}} p(y=0 | x) ^ {\delta_{0y}} = g(w^Tx) ^ {\delta_{1y}} (1 - g(w^Tx)) ^ {\delta_{0y}} 
$$

* To estimate $w$, we can use a cost function equal to the negative log-likehood function (maximum likelihood): 

$$
J(w) = -l(w) = -\delta_{1y} \log (g(w^Tx)) - \delta_{0y} \log (1 - g(w^Tx))
$$

* There is no closed form solution so we must use gradient descent to find the maximum likelihood solution.

### Softmax Regression


