# Statistical Distance and Divergences
* The key idea behind statistical distances and divergences is to measure how close two probability distributions resemble each other. 

## What is a Statistical Distance?
* Distance metric $d$ on set $X$ must satisfy the following properties (let $x, y, z \in X$)
    * Non-negativity: $d(x, y) \ge 0$ where equality holds iff $x = y$.
    * Symmetry: $d(x, y) = d(y, x)$.
    * Triangle inequality: $d(x, z) \le d(x, y) + d(y, z)$.
* A statistical distance is a distance metric between two probability distributions.

## Total Variation Distance
* The total variation distance is the largest difference between the probabilities the the probabilites assigned to the same event. We can define this as:
```math
\Delta(p, q) = \sup_{A \in \mathcal{F}} |p(A) - q(A)|
```
* This graphically is equvalent to the area where $p(x) > q(x)$. By symmetry, this is half the absolute area between $p(x)$ and $q(x)$. 
```math
\Delta(p, q) = \frac{1}{2} \sum_{x \in X} |p(x) - q(x)| 
```

## Kullback-Leibler Divergence
* KL divergence measures the difference between two probability distributions $P$ and $Q$ defined as:
```math 
D_{KL}(p || q) = E_{x \sim p} \left[ \log \frac{p(x)}{q(x)} \right]
```
* Note this is not a distance metrics as it is not symmetric. 
* KL divergence is non-negative by Jensen's inequality (note $\log$ is concave). 
```math
\begin{aligned}
-D_{KL}(p || q) & = E_{x \sim p} \left[ \log \frac{q(x)}{p(x)} \right]  \\
    & \le \log E_{x \sim p} \left[ \frac{q(x)}{p(x)} \right] \\
    & = \log \sum_x q(x) = 0
\end{aligned}
```

## Jension-Shannon Divergence
* JS diveregence is a symmetrized version of KL divergence. By symmetrizing KL divergence, we get a distance metric.
```math
D_{JS}(p, q) = \frac{1}{2} D_{KL}(p || m) + \frac{1}{2} D_{KL}(q || m)
```
* We can define $m$ by the equation $m = \frac{1}{2} (p + q)$.

## Wasserstein Distance
* Wasserstein distance is a distance metric that measures the minimum cost of transforming one distribution to another.
* Wasserstein distance of order $k$ is defined as:
```math
W_k(p, q) = \inf_{\gamma \in \Pi(p, q)}( E_{(x, y) \sim \gamma} [d(x, y)^k])^{1/k}
```
* $\Pi(p, q)$ is the set of all joint distributions with marginals $p$ and $q$.
* Wasserstein distance where $k=1$ is also known as the Earth Mover's distance (EMD). 
* The intuition behind EMD is that you are trying to find the minimum work (mass * distance) needed to transform one pile of dirt to the other. 
* $\gamma$ is how much mass is moved from $x$ to $y$.
* $d(x, y)$ is the distance between the two points.
* Thus we have the following equation:
```math
W_1(p, q) = \inf_{\gamma \in \Pi(p, q)} \int_{X \times Y} d(x, y) \gamma(x, y) dxdy
```