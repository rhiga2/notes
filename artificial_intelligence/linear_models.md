# Linear Models
## Linear Regression
### Supervised Learning
* In supervised learning we are given pairs $(x, y)$ where $x$ is the input and $y$ is the target we are trying to model. The goal is to find a mapping $f$ (known as the hypothesis) from $x$ to $y$ given data $D = \set{ (x^{(i)}, y^{(i)}) \}_{i=1}^n$ 
* We often times parameterize our hypothesis (i.e. $f_\theta$ or $f_w$). Thus finding the best hypothesis boils down to choosing the best params.
* The best params is determined by minimizing or maximizing an objective function. 

### Linear Regression Models
* A linear regresion model has the following form
```math
f_{w, b} = b + w_1 x_1 + w_2 x_2 + ... + w_n x_n = b + w^T x
```
* Often times we combine weights $w$ and bias $b$ into one vector such that $w_0 = b$ and $x_0 = 1$.
```math
f_w = w^T x
```

### Cost Function and Normal Equation
### Probabilistic Interpretation
### Geometric Interpretation

## Logistic Regression
### Binary Classification
* Given $d$ dimensional vector, we want to train a classifier to predict $0$ or $1$ (sometimes $1$ and $-1$).

### Sigmoid Function and Logistic Regression Models
* Sigmoid function outputs values between $0$ and $1$
```math
\sigma(z) = \frac{1}{1 + e^{-z}} 
```
* Logistic regression models are of the form:
```math
f_w(x) = \sigma(w^Tx)
```

### Probabilistic Interpretation of Logistic Regression
* $y | x$ is modelled as a Bernoulli dist parameterized by $f_w(x)$.
* Maximize likelihood
```math
\begin{gathered}
p_w(y| x) = f_w(x)^y * (1 - f_w(x))^{1-y} \\
\ell(w) = y \log f_w(x) +  (1 - y) \log (1 - f_w(x))
\end{gathered}
```
* The log-loss cost function is the negative log likelihood.
```math
J(w) = -\frac{1}{n} \sum_{i=1}^n \left[ y^{(i)} \log f_w(x^{(i)}) +  (1 - y^{(i)}) \log (1 - f_w(x^{(i)})) \right]
```
* Minimizing log-loss has no closed form solution. 

### Formulation with -1 and 1
* Using the followng identity: $\sigma(-z) = 1 - \sigma(z)$, we can reformulate the likelihood as:
```math
\ell(w) = \log (y f_w(x)) 
```
