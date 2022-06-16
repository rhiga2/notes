# Probability
## Axioms
### Probability Space
* Sample Space $\Omega$
* Event Space $\mathcal{F}$
* Probability Measure $\mathcal{P}$
### Kolmogorov's Axioms

### Sigma Algebra and Borel Sets

## Conditioning

## Discrete Random Variables
### Probability Mass Function
### Expectation, Moments, and Variance
### Bernoulli Distribution and Indicator Random Variables
* Coin flip with probability of heads equal to $p$.
### Binomial Distribution
* Number of heads in $n$ in independent and identical coin flips.

$$
X \sim \text{Binom}(n, p)
$$

### Geometric Random Variable
* Number of coin flips until the first head

### Poisson Random Variable
* Number of customers entering store in one hour given the average number of customers that enter the store in an hour is $\lambda$.

## Continuous Random Variables
### Probability Density Function 
### Expectation, Moments, Variance, and MGFs / CFs


## Convergence of Random Variables
### Almost Surely
$$
P\left(\lim_{n \rightarrow \infty} X_n = X\right) = 1
$$
### LP Convergence 
$$
\lim_{n \rightarrow \infty} E\left[|X_n - X|^p\right] = 0
$$
### Probability
$$
\lim_{n \rightarrow \infty} P(|X_n - X| \ge \epsilon) = 0
$$
### Distribution
* Convergence in distribution means that the CDFs of $X_n$ and $X$.

$$
\lim_{n \rightarrow \infty} F_{X_n}(x) = F_X(x)
$$

## Limit Theorems
### Law of Large Numbers
* Let $\bar{X_n}$ be the mean of $n$ iid random variables with distribution equal to random variable $X$.
* Let $\mu = E[X]$ 

$$
\begin{gather*}
\bar{X_n} \xrightarrow[]{p} \mu & \text{weak law} \\
\bar{X_n} \xrightarrow[]{as} \mu & \text{strong law} \\
\end{gather*}
$$

### Central Limit Theorem
$$
\sqrt{n} \frac{X_n - \mu}{\sigma} \xrightarrow[]{d} N(0, 1)
$$

## Inequalities 
### Markov Inequality
