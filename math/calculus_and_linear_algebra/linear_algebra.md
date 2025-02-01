Linear Algebra
==============
# System of Linear Equations
## Pivots and Free Columns
## Existence and Uniqueness
## Rank

# Vector Spaces and Subspaces
* Vector spaces define two operations (addition and scalar multiplication).
* Subspaces are closed over addition and scalar multiplication. 

## Four Fundamental Subspaces
* Nullspace $N(A)$: The set of all vectors $x$ such that $Ax = 0$
* Column space $C(A)$: The span of columns in $A$ or the image of linear transformation $A$. 
* Left Nullspace space $N(A^T)$
* Row space $C(A^T)$

# Orthogonality
* Two vectors are orthogonal if $x^T y= 0$
* Two subspaces are orthogonal if any vector in $V$ is ortho to any vector in $W$.
* Orthogonal complement of $A$ is the space of all vectors orthogonal to $A$. 

## Fundamental Theorem of Linear Algebra
* Column space is orthogonal to left nullspace. For any $x \in C(A)$ and $z \in N(A^T)$, we have 
```math
x^T z = (Ay)^T z = y^T (A^T z) = 0
```
* Not only are subspaces orthogonal, but they are orthogonal complements.
* Likewise nullspace and row space are orthogonal complements.

## Projections
* Projections are linear transformations $P$ that map a vector into the same or smaller subspace.
* They are idempotent $P^2 = P$.
* An orthogonal projection means that $P = P^T$

### Mapping Vector into 1D Subspace
* Given 1D subspace defined by $y$, we want to find a projection $P$ such that
  * Projection is in the subspace $Px = ay$
  * Minimize distance between projection and original input

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
