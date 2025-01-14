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
\begin{gathered}
S_{n+1} = 1 + r + r^2 + ... + r^n = r S_n + 1  \\
S_{n+1} - S_n = r^n
\end{gathered}
```
* Solve the sys of eqs gives
```math
S_n = \frac{1 - r^n}{1 - r}
```
* As $n \rightarrow \infty$ and $|r| < 1$,
```math
S = \frac{1}{1-r}
```

## Convergence of Sequences and Series
* Necessary condition: sequence must converge to $0$. 

## Power Series

## Taylor Series
