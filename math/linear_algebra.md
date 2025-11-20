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
* Given $A$ and $y$ find $x$ in $Ax=y$
* System of linear equations can have:
  * No solution
  * Exactly one solution
  * Infinitely many solutions
 
## Gaussian Elimination
* Gaussian elimination is a method used to solve a system of linear equations by reducing matrix $A$ to a reduced form.
* Row echelon form:
  * All-zero rows are at the bottom.
  * The leading non-zero entry in a row called the pivot is to the right of pivots in bottom rows.
* Reduced row echelon form:
  * Matrix is in row echelon form.
  * Pivots are one.
  * All entries to the left of pivot are zero. 
* Elementary row operations: Gaussian elimination uses the following operations
  * Permute two rows.
  * Scale a row.
  * Add scaled row to another row.
  * We transform bpth $A$ and $y$ simulataneously. 
* Existence and uniqueness
  * Solution does not exist if a row of all zeros corresponds to a non-zero entry in transformed $y$
  * Solution is unique if every column in reduced form has a pivot
  * Solution is non-unique if there are columns without pivots
* Rank: Number of pivots in reduced form. A matrix has full rank if every column and every row contains a pivot. 

## Invertibility and Determinants 
* Invertibility: If $A$ is square and fully ranked, then we know that A have an inverse such that $AA^{-1} = A^{-1}A = I$.
  * A non-invertible matrix is called singular.
* If $A$ is invertible, $Ax = y$ has a unique solution given by $A^{-1}y$.
* Determinant is a unique quantity of any matrix $A$ such that $\det{A} = 0$ implies that $A$ is singular.
* Determinants are hard to compute usually but there are special cases
  * Two by two matrices
  * Diagonal matrics: determinant is equal to product of diagonals.  

# Vector Spaces and Subspaces
* A vector space has two operations scalar multiplication and vector addition. 
* A vector subspace is closed is closed under scalar multiplcation and addition.
* Spans are linear combination of vectors. Span form a vector subspace.
## Basis and Dimension
* Basis of a subspace $V$ = minimum set of vectors whose span forms $V$.
* Basis is non-unique but the number of vectors in a basis will always stay the same.
* Dimension = number of basis vectors.  
## Subspaces Defined by Matrics 
* Column space $C(A)$: span of columns. Also known as range space since it's the set of outputs formed by multiplying by $A$. 
* Null space $N(A)$: all $x$ such that $Ax = 0$.
* Row space: column space of $A^T$
* Left null space: column space of $A^T$ 

# Orthogonality
* Two vector are orthogonal if their inner product is $0$.
* Two subspaces are orthogonal if the inner product of any vector in one subspace is orthogonal to any vector in the other subspace.
## Orthogonality of Subspaces
* Column space is orthogonal to left nullspace
  * Not only are these spaces orthogonal, but they are orthogonal complements, meaning that the left null space contains all vectors orthogonal to the column space.  
* If we replace $A$ by $A^T$, we also see that row space is orthogonal to nullspace. 
## Orthogonal Projections
* A projection is a mapping of a vector onto a subspace. Note that any vector already in the subspace is mapped to itself, meaning that projections are idempotent
since once you project a vector onto a subspace applying the same projection will get you the same result.
* Orthogonal projections is a mapping of a vector onto a subspace such that the difference between the projection and the original vector (projection error) is orthogonal to the subspace.
* Orthogonality rule: Minimum projection error between a vector and subspace is orthogonal to the subspace. 
* 1D example: orthogonally project vector $x$ onto $y$
  * We also know that the projection $Px$ lies along $y$. In other words, there is a constant $a$ such that $Px = ay$.
  * By orthogonality, $\langle y, x - ay \rangle = 0$.
  * Solve for $a$ gives: $a = \frac{\langle y, x \rangle}{\lVert y \rVert^2}$
  * Thus $Px = \frac{\langle y, x \rangle}{\lVert y \rVert^2} y = \frac{yy^T}{\lVert y \rVert^2} x$.
* nD example: orthogonally project vector $x$ onto subspace $U$.
  * Let $A$'s columns be the basis for $U$. In other words, $C(A)=U$.
  * Project $Px$ is in $C(A)$. Thus $Px=Ab$ for some vector $b$.
  * By orthogonality, $x - Px \in N(A^T)$. $A^T(x - Px) = A^T(x - Ab) = 0$.
  * Solve for $b$, $b = (A^TA)^{-1}A^Tx$.
  * Thus $Px = A(A^TA)A^T x$
* Note about matrix $P$.
  * Projections are idempotent: $P^2 = A(A^TA)A^TA(A^TA)A^T = A(A^TA)^{-1}A^T = P$.
  * Orthogonal projections (for real matrices) are symmetric $P^T = P$.
## Orthonormality and Orthogonal Matrices
* Set of vectors $q_1, q_2, ..., q_n$ are orthonormal if they are orthogonal to one another and have norm $1$.
* If we put orthgonal vectors as columns in a matrix $Q$, we have that $Q^TQ=I$.
* A matric is orthogonal if the columns are orthonormal and $Q$ is square.
* Gram-Schmidt turns linearly independent vectors $x_1, x_2, ..., x_n$ into orthogonal vectors $q_1, q_2, ..., q_n$
  * First direction = $x_1$.
  * Second direction = $x_2$ - (projection of $x_2$ onto $y_1$)
  * kth direction = $x_k$ - (projections of $y_{j}$ for $j < k$)
  * Normalize each direction into a unit vector.

$$
\begin{align*}
y_1 = x_1 \\
y_2 = x_2 - \frac{y_1^T x_2}{\lVert y_1 \rVert^2} y_1 \\
... \\
y_k = x_k - \frac{y_1^T x_k}{\lVert y_1 \rVert^2} y_1 ... - \frac{y_{k-1}^T x_k}{\lVert y_{k-1} \rVert^2} y_{k-1}\\
q_j = \frac{y_j}{\lVert y_j \rVert} \\
\end{align*}
$$
* We can also express the Gram-Schmidt process as a decomposition. This is known as $QR$ decomposition. 

# Eigenvalues and Eigenvectors
* An eigenvector $x != 0$ and eigenvalue $\lambda$ satisfy the equation $Ax = \lambda x$
* Note this equation only makes sense if $A$ is a square matrix.
* The equation $Ax = \lambda x$ can be rewritten as $(A - \lambda I) x = 0$

* We can find eigenvectors and eigenvalues by the following process:
1. If $X \ne 0$, then $A - \lambda I$ is singular. We can solve $|A-\lambda I| = 0$ for $\lambda$'s.
2. For each $\lambda$ in step 1, we can find the basis of $N(A - \lambda I)$ to get $x$.
* Note eigenvectors are directions. Thus any scaling factors on the eigenvectors don't matter.
* Also note that eigenvectors and eigenvalues may not be real. 
## Diagonalization
* We can organize each eigenvectors of $A$ into columns of matrix $S$.
* Let $\Lambda$ be a diagonal matrix with eigenvalues in the diagonal. Note that the order of eigenvectors in $S$ must correspond to the order of eigenvalues in $\Lambda$.
* We have $AS = S \Lambda$.
* If $S$ is invertible (eigenvectors are linear independent, known as diagonalizability), then $A = S\Lambda S^{-1}$
### Diagonalization of Symmetric Matrics 
* Note eigenvectors and eigenvalues of real symmetric matrices are real. 
* Eigenvectors corresponding to different eigenvalues of a real symmetric matric are orthogonal.
  * Assume $\lambda_1 \ne \lambda_2$ and $A = A^T$.
  * Prove inner product of $x_1$ and $x_2$ is $0$. 
  
$$
\begin{align*}
\langle Ax_1, Ax_2 \rangle = (Ax_1)^T(\lambda_2 x_2) = \lambda_2 x_1^T A^T x_2 = \lambda_2^2 \langle x_1, x_2 \rangle \\
\langle Ax_1, Ax_2 \rangle = (\lambda_1 x_1)^T(A x_2) = \lambda_1^2 \langle x_1, x_2 \rangle \\
\langle x_1, x_2 \rangle = 0
\end{align*}
$$

* Since eigenvectors are orthonormal (scale does not matter), we know that the eigenvector matrix $Q$ is orthogonal. Thus $A = Q\Lambda Q^T$.
# Definite Matrice
* A symmetric matrix $M$ is positive definite if 
  * For any $x \ne 0$, $x^TMx > 0$
  

# Singular Value Decomposition
* Any matrix $A$ can be decomposed as $U\SigmaV^T$.
  * Matrix $U$  
