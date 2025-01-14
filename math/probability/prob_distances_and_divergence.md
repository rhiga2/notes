# Probability Distributions Distances
## Total Variation Distance
* TV distance measures the difference in mass between $P$ and $Q$ on the interval where $P > Q$.
* Although it may not look symmetric, TV distance is symmetric since if the mass for  

## KL Divergence and JS Divergence
### KL Divergence 
* KL divergence is defined as: 
```math
\text{KL}(P, Q) = -E_{X \sim P}\left[ \log \frac{Q(X)}{P(X)} \right] 
```
* Jensen's inequality: expectation of convex func $\ge$ convex func applied to the expectation. Since negative log is strictly convex,
```math
\begin{aligned}
\text{KL}(P, Q) &= -E_{X \sim P}\left[ \log \frac{Q(X)}{P(X)} \right] \\ 
  &\ge  -\log E_{X \sim P}\left[ \frac{Q(X)}{P(X)} \right] \\
  &= -\log \sum_{x} Q(x) = -\log 1 = 0
\end{aligned}
```
* Thus KL divergence is always non-neg
* KL divergence is not a distance cause it's not symmetric. 

### JS Divergence
* Symmetric version of KL divergence

## Earth-Mover's Distance and Wasserstein Distance 
### Earth-Mover's Distance
* EMD measures the amount of work (distance * mass) needed to transform distribution $P$ into $Q$. 
```math
\text{EMD}(P, Q) = \inf_{\gamma \sim \Pi(P, Q)} E_{(X, Y) \sim \gamma} \left[ d(X, Y) \right]
```
* $\Pi$ is the space of joint distributions whose marginals are $P$ and $Q$, $\gamma$ is the amount of mass that we move between $X$ and $Y$, and $d$ is the distance we are moving that mass.  
