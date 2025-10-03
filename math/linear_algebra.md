Linear Algebra
=================
# Vectors, Matrices, and Linear Transformations
* Matrices: 2D grid of numbers
* Basic Matrix Operations
  * Matrix Addition: $C_{ij} = A_{ij} + B_{ij}$. Addition is elementwise.  
  * Matrix Multiplication: $C_{ij} = \sum_k A_{ik}A_{kj}$ where $C=AB$.
    * The identity matrix $I$ is such $AI = A$ and $IA = A$ (given dimensions work out) 
  * Transpose: Switch rows and columns in a matrix.
  * Trace (tr): For square matrices, the trace is the sum of diagonal elements.  
* A linear transformation $T$ has the following properties
  * Scalar multiplication is interchangable: $T(\alpha x) = \alpha Tx$
  * Vector Addition is interchangeable: $T(x + y) = Tx + Ty$.
  * Any linear transformation $T$ can be expressed as matrix multiplication. 

# System of Linear Equation $Ax = y$. 
* Given $A$ and $y$ find $x$.
* System of linear equations can have:
  * No solution
  * Exactly one solution
  * Infinitely many solutions
## Gaussian Elimination
* Pivot and free columns
* Rank of $A$: the number of pivot columns in $A$.
## Invertibility and Determinants 
* Invertibility: If $A$ is square and fully ranked, then we know that A have an inverse such that $AA^{-1} = A^{-1}A = I$.
  * A non-invertible matrix is called singular.
* If $A$ is invertible, $Ax = y$ has a unique solution given by $A^{-1}y$.
* Determinant is a unique quantity of any matrix $A$ such that $\det{A} = 0$ implies that $A$ is singular.
* Determinants are hard to compute usually but there are special cases
  * Two by two matrices
  * Diagonal matrics: determinant is equal to product of diagonals.  

## Vector Spaces and Subspaces
* A vector space has two operations scalar multiplication and vector addition. 
* A vector subspace is closed is closed under scalar multiplcation and addition.
* Spans are linear combination of vectors. Span form a vector subspace.
### Basis
* Basis of a subspace $V$ = minimum set of vectors whose span forms $V$. 
### Subspaces Defined by Matrics 
* Column space $C(A)$: span of columns. Also known as range space since it's the set of outputs formed by multiplying by $A$. 
* Null space $N(A)$: all $x$ such that $Ax = 0$.
* Row space: column space of $A^T$
* Left null space: column space of $A^T$ 

## Orthogonality
* Two vector are orthogonal if their inner product is $0$.
* Two subspaces are orthogonal if the inner product of any vector in one subspace is orthogonal to any vector in the other subspace.
### Orthogonality of Subspaces
* Column space is orthogonal to left nullspace
* Nullspace 
### Orthogonal Projections
* A projection is a mapping of a vector onto a subspace. Note that any vector already in the subspace is mapped to itself, meaning that projections are idempotent
since once you project a vector onto a subspace applying the same projection will get you the same result.
* Orthogonal projections is a mapping of a vector onto a subspace such that the difference between the projection and the original vector (projection error) is orthogonal to the subspace.
* Orthogonality rule: Minimum projection error between a vector and subspace is orthogonal to the subspace. 
* 1D example: orthogonally project vector $x$ onto $y$
  * We know that $\langle y, x - Px \rangle = 0$ where $Px$ is projection of $x$ onto $y$.
  *    
