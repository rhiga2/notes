# Differentiation
## Limits and Continuity
### Epsilon-Delta Definition

## Derivatives
### Instantaneous Rate of Change
* Average rate of change
```math
\frac{\Delta y}{\Delta x} = \frac{f(x + \Delta x) - f(x)}{\Delta x}
```
* Instantaneous rate of change is the limit of the average rate of change when $\Delta x \rightarrow 0$.
```math
f'(x) = \frac{dy}{dx} = \lim_{\Delta x \rightarrow 0} \frac{f(x + \Delta x) - f(x)}{\Delta x}
```
### Geometric Interpretation
* Average rate of change is a secant to the curve $y = f(x)$
* Instantaneous rate of change

## Applications of Derivatives
### Linear Approx
* For small change in $x$, the derivative approximates the average rate of change
```math
\begin{gathered}
\frac{y - f(a)}{x - a} \approx f'(a) \\
y = f(a) + f'(a) (x - a)
\end{gathered}
```
## Mean-Value Theorem
* Rolle's Theorem
* Mean-Value Theorem: Given $f$ is differentiable in the interval $[a, b]$, there is a point $c$ in the interval such that
```math
\frac{f(b) - f(a)}{b - a} = f'(c)
```

