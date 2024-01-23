# Latent Variable Models
# Evidence Lower Bound


$$
\begin{aligned}
l(\theta) &= \log( p_\theta(X) ) = E_{Z \sim q} \left[ \log(p_\theta(X)) \right] \\
	&= E_{Z \sim q} \left[ \log \left( p_\theta(X) \frac{q(Z)}{q(Z)} \right) \right] \\
 	&= E_{Z \sim q} \left[ \log \left( \frac{p_\theta(X, Z)}{p_\theta(Z | X)} \frac{q(Z)}{q(Z)} \right) \right] \\
  	&= E_{Z \sim q} \left[ \log \left( \frac{p_\theta(X, Z)}{q(Z)} \right) \right] +  E_{Z \sim q} \left[ \log \left( \frac{q(Z)}{p_\theta(Z | X)} \right) \right] \\
   	&= F(q, \theta) + D_{KL}(q || p_\theta(\cdot | X))
\end{aligned}
$$


