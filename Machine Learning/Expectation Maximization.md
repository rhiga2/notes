The Expectation Maximization Algorithm
======================================

# Latent Variable Models
* Latent variables models are probability models that have both observed $X$ and unobserved (latent) variables $Z$. 
* Adding latent variables to a model can make it more expressive, but also more difficult to fit.

# Mixture Models
* A mixture model is an example of latent variable model where the latent variables are discrete $( Z \sim \text{Cat}(\pi_1, ..., \pi_K))$.
$$
\begin{aligned}
p_\theta(X) &= \sum_{k=1}^K p_\theta(X | Z=k) \underbrace{p_\theta(Z=k)}_{\pi_k} \\
	&= \sum_{k=1}^K \pi_k p_\theta(X | Z=k)
\end{aligned}
$$
* Maximum likelihood estimation of mixture models is difficult because the likelihood is a sum of densities, which is difficult to optimize.
$$
\max_\theta \log p_\theta(X) \equiv \max_\theta \log \left( \sum_{k=1}^K \pi_k p_\theta(X | Z=k) \right) 
$$

# Evidence Lower Bound
* Instead of maximizing the likelihood directly, we can maximize a lower bound on the likelihood. The intuition is that if we find a tight lower bound that is easier to maximize we can maximize the likelihood indirectly.  
$$
\begin{aligned}
l(\theta) &= \log( p_\theta(X) ) = E_{Z \sim q} \left[ \log(p_\theta(X)) \right] \\
	&= E_{Z \sim q} \left[ \log \left( p_\theta(X) \frac{q(Z)}{q(Z)} \right) \right] \\
 	&= E_{Z \sim q} \left[ \log \left( \frac{p_\theta(X, Z)}{p_\theta(Z | X)} \frac{q(Z)}{q(Z)} \right) \right] \\
  	&= \underbrace{E_{Z \sim q} \left[ \log \left( \frac{p_\theta(X, Z)}{q(Z)} \right) \right]}_{F(q, \theta)} +  \underbrace{E_{Z \sim q} \left[ \log \left( \frac{q(Z)}{p_\theta(Z | X)} \right) \right]}_{D_{KL}(q || p_\theta(\cdot | X))} \\
   	&= F(q, \theta) + D_{KL}(q || p_\theta(\cdot | X)) \\
	& \ge F(q, \theta)
\end{aligned}
$$
* The quantity $F(q, \theta)$ is called the Evidence Lower Bound (ELBO), because it is a lower bound on the log-likelihood. 

# Expectation Maximization Algorithm
The goal of the EM algorithm is to maximize ELBO by performing iterative coordinate ascent wrt $q$ and $\theta$.
