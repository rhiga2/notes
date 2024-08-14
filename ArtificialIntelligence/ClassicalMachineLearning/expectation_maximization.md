Expectation Maximization
==============

# Latent Variable Models
* Latent variables models are probability models that have both observed $x$ and unobserved (latent) variables $z$. 
* Adding latent variables to a model can make it more expressive, but also more difficult to fit.

## Mixture Models
* A mixture model is an example of latent variable model where the latent variables are discrete $( z \sim \text{Cat}(\pi_1, ..., \pi_K))$.
``` math
\begin{aligned}
p_\theta(x) &= \sum_{k=1}^K p_\theta(x | z=k) \underbrace{p_\theta(z=k)}_{\pi_k} \\
	&= \sum_{k=1}^K \pi_k p_\theta(x | z=k)
\end{aligned}
```
* Maximum likelihood estimation of mixture models is difficult because the likelihood is a sum of densities, which is difficult to optimize.
``` math
\max_\theta \log p_\theta(x) \equiv \max_\theta \log \left( \sum_{k=1}^K \pi_k p_\theta(x | z=k) \right) 
```

# Evidence Lower Bound
* Instead of maximizing the likelihood directly, we can maximize a lower bound on the likelihood. The intuition is that if we find a tight lower bound that is easier to maximize we can maximize the likelihood indirectly.  
``` math
\begin{aligned}
l(\theta) &= \log( p_\theta(x) ) = E_{z\sim q} \left[ \log(p_\theta(x) \right] \\
	&= E_{z \sim q} \left[ \log \left( p_\theta(x) \frac{q(z)}{q(z)} \right) \right] \\
	&= E_{z \sim q} \left[ \log \left( \frac{p_\theta(x, z)}{p_\theta(z | x)} \frac{q(z)}{q(z)} \right) \right] \\
	&= \underbrace{E_{Z \sim q} \left[ \log \left( \frac{p_\theta(x, z)}{q(z)} \right) \right]}_{F(q, \theta)} +  \underbrace{E_{z \sim q} \left[ \log \left( \frac{q(z)}{p_\theta(z | x)} \right) \right]}_{D_{KL}(q \Vert p_\theta(\cdot | x))} \\
	&= F(q, \theta) + D_{KL}(q \Vert p_\theta(\cdot | x)) \\
	& \ge F(q, \theta)
\end{aligned}
```
* Since KL divergence is always positive (Jensen's inequality), the quantity $F(q, \theta)$ is a lower bound; thus the name Evidence Lower Bound (ELBO).

# The Expectation Maximization Algorithm
* The goal of the EM algorithm is to maximize ELBO by performing iterative coordinate ascent wrt $q$ and $\theta$.

## E-Step
* In the E-step, we maximize the ELBO wrt to $q$:
``` math
\begin{aligned}
\max_q F(q, \theta) &\equiv \max_q (l(\theta) - D_{KL}(q \Vert p_\theta(\cdot | X))) \\	
	&\equiv \min_q D_{KL}(q \Vert p_\theta(\cdot | X)) \\
\end{aligned}
```
* KL divergence is minimized when $q(z) = p_\theta(z | x)$. Thus the goal of the E-step is find the posterior distribution of the latent variables given the observed data.

## M-Step
* In the M-step, we maximize the ELBO wrt to $\theta$ given $q(z) = p_{\bar{\theta}}(z | x)$ where $\bar{\theta}$ is the current estimator of $\theta$ (we will find a new estimator in the M-step):
``` math
\begin{aligned}
\max_\theta F(q, \theta) & \equiv \max_\theta E_{z \sim q} \left[ \log \left( \frac{p_\theta(x, z)}{q(z)} \right) \right] \\
& \equiv \max_\theta E_{z \sim q} \left[ \log \left( p_\theta(x, z) \right) \right] \\
\end{aligned}
```

* From the E-step, we have that $q(z) = p_\theta(z \Vert x)$. Therefore, in the M-step, we need to find $\theta$ that maximizes the complete data log-likelihood:
``` math 
Q(\theta, \bar{\theta}) = E_{z \sim p_{\bar{\theta}}(\cdot | X)} \left[ \log \left( p_\theta(x, z) \right) \right]
```

# Gaussian Mixture Models
* In a Gaussian Mixtures Model, the log-likelihood is given by:
``` math
p_{\theta}(x) = \sum_{k=1}^K \pi_k \mathcal{N}(x | \mu_k, \Sigma_k)
``` 
* Note that $\theta = \{(\pi_k, \mu_k, \Sigma_k)\}_{k=1}^K$.
## E-step
* In the E-step, we need to find $w_k^{(i)} = p_{\bar{\theta}}(z^{(i)} = k | x^{(i)})$:
``` math
w_k^{(i)} = p_{\bar{\theta}}(z^{(i)} = k | x^{(i)}) = \frac{\bar{\pi_k} \mathcal{N}(x^{(i)} | \bar{\mu_k}, \bar{\Sigma_k})}{\sum_{j=1}^K \bar{\pi_j} \mathcal{N}(x^{(i)} | \bar{\mu_j}, \bar{\Sigma_j})}
```

## M-step
* In the M-step, we need to find $\theta$ that maximizes the complete data log-likelihood:
``` math
\begin{aligned}
\max_\theta Q(\theta, \bar{\theta}) &= E_{z \sim p_{\bar{\theta}}(\cdot | x)} \left[ \log \left( p_\theta(x, z) \right) \right] \\
	& = \sum_{i=1}^n \sum_{k=1}^K w_k^{(i)} \left( \log \pi_k + \log \mathcal{N}(x^{(i)} | \mu_k, \Sigma_k) \right)
\end{aligned}
```
* We can find the maximum likelihood estimator of $\theta$ by setting the gradient of the Langragian wrt $\theta$ to zero.
``` math
\begin{aligned}
\nabla_\theta \left ( Q(\theta, \bar{\theta}) + \lambda \left( 1 - \sum_{k=1}^K \pi_k \right) \right) &= 0 \\
\end{aligned}
```
* We get the following results for the updated param estimates:
``` math
\begin{gathered}
n_k = \sum_{i=1}^n w_k^{(i)}, \; \bar{\pi_k} = \frac{1}{n} n_k \\
\bar{\mu_k} = \frac{1}{n_k} \sum_{i=1}^n w_k^{(i)} x^{(i)}\\
\bar{\Sigma_k} = \frac{1}{n_k} \sum_{i=1}^n w_k^{(i)} (x^{(i)} - \bar{\mu_k})(x^{(i)} - \bar{\mu_k})^T
\end{gathered}
```
