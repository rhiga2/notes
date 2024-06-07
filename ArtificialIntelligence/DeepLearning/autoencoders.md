# Autoencoders
## Variational Autoencoders
* Instead of treating the encoder-decoder as a deterministic function, we can treat it as a probabilistic function $p_\theta(z | x)$ and $q_\phi(x | z)$ respectively.
* We assume that $p_\theta(z | x)$ is a Gaussian distribution with mean $\mu_\theta(x)$ and variance 
$\sigma_\theta(x)$.
```math
p_\theta(z | x) = \mathcal{N}(z | \mu_\theta(x), \sigma_\theta(x)) 
```
* In the forward pass, we sample $z$ from $p_\theta(z | x)$ and pass it through the decoder $q_\phi(x | z)$ to get the reconstructed output.
* The loss function is the negative ELBO:
```math 
\begin{aligned}
J(\theta, \phi) & = -F(p_\theta, \phi) \\
    & = -E_{z \sim p_\theta(\cdot | x)} \left[ \log q_\phi(x | z) \right] + D_{KL}(p_\theta(z | x) || p(z)) 
\end{aligned}      
```
* $p(z)$ is a standard Gaussian distribution.

### The Reparameterization Trick
* In the forward pass, we sampled from a Gaussian distribution. How do we backpropagate through sampling?
* We instead sample from a standard Gaussian distribution $\epsilon \sim \mathcal{N}(0, 1)$ and transform it to $z$ using the mean and variance output by the encoder:
```math
z = \mu_\theta(x) + \sigma_\theta(x) \epsilon
```
* Sampling in this way decouples the randomness from direct dependence on the parameters.




