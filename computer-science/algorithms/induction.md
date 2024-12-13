# Induction
## Weak Induction
* Method to prove proposition $P(n)$ is true for all natural numbers $0, 1, 2, ..., n$
* We split induction into two steps:
  * Base case: Prove $P(0)$ is true.
  * Inductive step: Prove if $P(k)$ is true, $P(k+1)$ follows.

### Example: Prove $1 + 2 + 4 + ... + 2^{k-1} = 2^k - 1$
* Base case
```math
2^0 = 2^1 - 1 = 1
```
* Inductive step
```math
(1 + 2 + 4 + ... + 2^{k-1}) + 2^k = (2^{k} - 1) + 2^k = 2^{k+1} - 1
```

## Strong Induction
* Similar to weak case, but the inductive step assumes P(m) for all natural numbers $m < k$. 

