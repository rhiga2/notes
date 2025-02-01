Linear Algebra
==============
# System of Linear Equations
## Pivots and Free Columns
## Existence and Uniqueness
## Rank

# Vector Spaces and Subspaces

# Orthogonality
* Two vectors are orthogonal if $x^T y = 0$
* Two subspaces are orthogonal if any vector in $V$ is ortho to any vector in $W$.

## Fundamental Theorem of Linear Algebra

# Eigenvalues and Eigenvectors
* A transformation $A$ has eigenvector $x \ne 0$ if $A$ applied to $x$ returns a scaled version of $x$. The scaling factor is called an eigenvalue.  
```math
Ax = \lambda x
```
* Find eigvecs and eigvals using equation for $\lambda$ and $x$
```math
(A - \lambda I) x = 0
```
1. Since we assume a non-zero solution, we know that $A - \lambda I$ is singular: $\det(A - \lambda I) = 0$. We can solve for $\lambda$'s.
2. For each $\lambda$, find nullspace of $A - \lambda I$. 

# Singular Value Decomposition 
