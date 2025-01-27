Calculus
========
# Differentiation
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
* Geometrically, the average rate of change is a secant line to curve, whereas the derivative is tangential to the curve. 

## Applications of Derivatives
### Linear Approx
* For small change in $x$, the derivative approximates the average rate of change
```math
\begin{gathered}
\frac{y - f(a)}{x - a} \approx f'(a) \\
y = f(a) + f'(a) (x - a)
\end{gathered}
```

# Intergration
## Definite Integrals
## Fundamental Theorem of Calculus
* Intuition: integration is the inverse operation to the antiderivative.

# Series
## Terminology
* Sequence: ordered values $x_1, x_2, x_3, ...$
* Infinite Series: sum of infinite sequence $\sum_{i=1}^{\infty} x_i$
* Partial Sum: sum up to $n$ values $S_n = \sum_{i=1}^n x_i$

## Geometric Series
```math
S = 1 + r + r^2 + ... = \sum_{i=1}^{\infty} r^{i-1}
```
* Calculating closed form
```math
\text{Solve sys of eqs }
\begin{cases}
S_{n+1} = 1 + r + r^2 + ... + r^n = r S_n + 1  \\
S_{n+1} - S_n = r^n
\end{cases}

\text{Solution } S_n = \frac{1 - r^n}{1 - r}
```
* As $n \rightarrow \infty$ and $|r| < 1$,
```math
S = \frac{1}{1-r}
```

## Convergence of Sequences and Series
* Necessary condition: sequence must converge to $0$. 

## Power Series

## Taylor Series



