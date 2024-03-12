Probability Introduction
======================================

# Probability Space 
* A probability space is a triple $(\Omega, \mathcal{F}, P)$ where $\Omega$ is the sample space, $\mathcal{F}$ is a $\sigma$-algebra of subsets of $\Omega$, and $P$ is a probability measure on $\mathcal{F}$.

# Aside on $\sigma$-Algebras
* Not all subsets in $\Omega$ are measurable (can be assigned a probability). For example in the case of real numbers, the cardinality of $2^\mathbb{R}$ is greater than the cardinality of $\mathbb{R}$. Thus we must consider a smaller collection of subsets of $\Omega$ that are measurable called a $\sigma$-algebra.
* A $\sigma$-algebra $\mathcal{F}$ is a collection of subsets of $\Omega$ that satisfies the following properties:
1. $\Omega \in \mathcal{F}$
2. If $A \in \mathcal{F}$, then $A^c \in \mathcal{F}$
3. If $A_1, A_2, ... \in \mathcal{F}$, then $\cup_{i=1}^\infty A_i \in \mathcal{F}$
 

# Kolmogorov's Axioms
* Kolmogorov's axioms are a set of three axioms that define a probability measure $P$ on a $\sigma$-algebra $\mathcal{F}$.
1. $P(A) \ge 0$ for all $A \in \mathcal{F}$
2. $P(\Omega) = 1$
3. If $A_1, A_2, ... \in \mathcal{F}$ are disjoint, then $P (\cup_{i=1}^\infty A_i) = \sum_{i=1}^\infty P(A_i)$

# Properties of Probability Measures
* $P(A^c) = 1 - P(A)$
``` math
1 = P(\Omega) = P(A \cup A^c) = P(A) + P(A^c)
```

* $P(\emptyset) = 0$
``` math
P(\empty) = 1 - P(\Omega) = 1 - 1 = 0
```

* If $A \subset B$, then $P(A) \le P(B)$
``` math
P(B) = P(A \cup (B \cap A^c)) = P(A) + P(B \cap A^c) \ge P(A)
```

* $P(A \cup B) = P(A) + P(B) - P(A \cap B)$
``` math
\begin{aligned}
P(A \cup B) &= P(A \cup (B \cap A^c)) = P(A) + P(B \cap A^c) \\ 
&= P(A) + P(B) - P(A \cap B)
\end{aligned}
```

# Conditional Probability
* Definition of conditional probability: probability $A$ given $B$ is defined as 
``` math
P(A | B) = \frac{P(A \cap B)}{P(B)}
```

# Chain Rule 
* Based on the definition of conditional probability, we can derive the chain rule:
``` math
P(A) = P(A | B) P(B)
```

# Bayes' Rule
``` math
P(A | B) = \frac{P(B | A) P(A)}{P(B)}
```
* $P(A)$ is called the prior. It represents our belief about $A$ before observing $B$.
* $P(A | B)$ is called the posterior. It represents our belief about $A$ after observing $B$.
* $P(B | A)$ is called the likelihood.
* Bayes Rule tells us how to update our beliefs about $A$ after observing $B$.

# Independence
* Two events $A$ and $B$ are independent iff
``` math
P(A \cap B) = P(A) P(B)
```
* If $A$ and $B$ are independent, then $P(A | B) = P(A)$ and $P(B | A) = P(B)$. Namely observing either event does not change our beliefs about the other.


