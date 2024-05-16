# The Expectation Maximization Algorithm

## Latent Variable Models
* Latent variables models are probability models that have both observed $X$ and unobserved (latent) variables $Z$. 
* Adding latent variables to a model can make it more expressive, but also more difficult to fit.

### Mixture Models
* A mixture model is an example of latent variable model where the latent variables are discrete $( Z \sim \text{Cat}(\pi_1, ..., \pi_K))$.
	``` math
	\begin{aligned}
	p_\theta(X) &= \sum_{k=1}^K p_\theta(X | Z=k) \underbrace{p_\theta(Z=k)}_{\pi_k} \\
		&= \sum_{k=1}^K \pi_k p_\theta(X | Z=k)
	\end{aligned}
	```
* Maximum likelihood estimation of mixture models is difficult because the likelihood is a sum of densities, which is difficult to optimize.
	``` math
	\max_\theta \log p_\theta(X) \equiv \max_\theta \log \left( \sum_{k=1}^K \pi_k p_\theta(X | Z=k) \right) 
	```

## Evidence Lower Bound
* Instead of maximizing the likelihood directly, we can maximize a lower bound on the likelihood. The intuition is that if we find a tight lower bound that is easier to maximize we can maximize the likelihood indirectly.  
	``` math
	\begin{aligned}
	l(\theta) &= \log( p_\theta(X) ) = E_{Z \sim q} \left[ \log(p_\theta(X)) \right] \\
		&= E_{Z \sim q} \left[ \log \left( p_\theta(X) \frac{q(Z)}{q(Z)} \right) \right] \\
		&= E_{Z \sim q} \left[ \log \left( \frac{p_\theta(X, Z)}{p_\theta(Z | X)} \frac{q(Z)}{q(Z)} \right) \right] \\
		&= \underbrace{E_{Z \sim q} \left[ \log \left( \frac{p_\theta(X, Z)}{q(Z)} \right) \right]}_{F(q, \theta)} +  \underbrace{E_{Z \sim q} \left[ \log \left( \frac{q(Z)}{p_\theta(Z | X)} \right) \right]}_{D_{KL}(q || p_\theta(\cdot | X))} \\
		&= F(q, \theta) + D_{KL}(q || p_\theta(\cdot | X)) \\
		& \ge F(q, \theta)
	\end{aligned}
	```
* The quantity $F(q, \theta)$ is called the Evidence Lower Bound (ELBO), because it is a lower bound on the log-likelihood. 

## Expectation Maximization Algorithm
* The goal of the EM algorithm is to maximize ELBO by performing iterative coordinate ascent wrt $q$ and $\theta$.

### E-Step
* In the E-step, we maximize the ELBO wrt to $q$:
	``` math
	\begin{aligned}
	\max_q F(q, \theta) &\equiv \max_q (l(\theta) - D_{KL}(q || p_\theta(\cdot | X))) \\	
		&\equiv \min_q D_{KL}(q || p_\theta(\cdot | X)) \\
	\end{aligned}
	```
* KL divergence is minimized when $q(Z) = p_\theta(Z || X)$. Thus the goal of the E-step is find the posterior distribution of the latent variables given the observed data.

### M-Step
* In the M-step, we maximize the ELBO wrt to $\theta$ given $q(Z) = p_{\bar{\theta}}(Z | X)$ where $\bar{\theta}$ is the current estimator of $\theta$ (we will find a new estimator in the M-step):
	``` math
	\begin{aligned}
	\max_\theta F(q, \theta) & \equiv \max_\theta E_{Z \sim q} \left[ \log \left( \frac{p_\theta(X, Z)}{q(Z)} \right) \right] \\
	& \equiv \max_\theta E_{Z \sim q} \left[ \log \left( p_\theta(X, Z) \right) \right] \\
	\end{aligned}
	```

* From the E-step, we have that $q(Z) = p_\theta(Z || X)$. Therefore, in the M-step, we need to find $\theta$ that maximizes the complete data log-likelihood:
``` math 
Q(\theta, \bar{\theta}) = E_{Z \sim p_{\bar{\theta}}(\cdot | X)} \left[ \log \left( p_\theta(X, Z) \right) \right]
```

## Gaussian Mixture Models
* In a Gaussian Mixtures Model, the log-likelihood is given by:
	``` math
	p_{\theta}(X) = \sum_{k=1}^K \pi_k \mathcal{N}(X | \mu_k, \Sigma_k)
	``` 
* $\theta = \{(\pi_k, \mu_k, \Sigma_k)\}_{k=1}^K$.
### E-step
* In the E-step, we need to find $w_k^{(i)} = p_{\bar{\theta}}(z^{(i)} = k | x^{(i)})$:
``` math
w_k^{(i)} = p_{\bar{\theta}}(z^{(i)} = k | x^{(i)}) = \frac{\bar{\pi_k} \mathcal{N}(x^{(i)} | \bar{\mu_k}, \bar{\Sigma_k})}{\sum_{j=1}^K \bar{\pi_j} \mathcal{N}(x^{(i)} | \bar{\mu_j}, \bar{\Sigma_j})}
```

### M-step
* In the M-step, we need to find $\theta$ that maximizes the complete data log-likelihood:
	``` math
	\begin{aligned}
	\max_\theta Q(\theta, \bar{\theta}) &= E_{Z \sim p_{\bar{\theta}}(\cdot | X)} \left[ \log \left( p_\theta(X, Z) \right) \right] \\
		& = \sum_{i=1}^N \sum_{k=1}^K w_k^{(i)} \left( \log \pi_k + \log \mathcal{N}(x^{(i)} | \mu_k, \Sigma_k) \right)
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
	```