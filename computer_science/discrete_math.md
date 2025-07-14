Discrete Mathematics
====================
# Predicate Logic (First Order Logic)
## Components
* Predicates are expressions that evaluate to true or false aka boolean expressions. (i.e. $P(x) = x > 5$)
* Basic Boolean Operations
  * AND (Conjunction): $P \land Q$ evaluates to true when $P$ and $Q$ are true
  * OR (Disjunction): $P \lor Q$ evaluates to true when $P$ or $Q$ are true or both are true.
  * NOT (Negation): $\neg P$ evaluates to true when $P$ is false.
  * Order of operations: PARENS, NOT, AND, OR
  * Truth tables can be used to exhaust all cases of evaluations. Two expressions are equal if they have the same truth table. 
  
    | $P$ | $Q$ | $P \land Q$ |
    | --- | --- | ----------- |
    | F   | F   | F           |
    | F   | T   | F           |
    | T   | F   | F           |
    | T   | T   | T           |

* Quantifiers
  * Universal: $\forall x P(x)$ evaluates to true if $P(x)$ is true for all values of $x$
  * Existential: $\exists x P(x)$ evaluates to true if 

## Combining Boolean Operations 
* DeMorgan's Law
  * $\neg (P \land Q) = \neg P \lor \neg Q$
  * $\neg (P \lor Q) = \neg P \land \neg Q$
* IF, Converse, Contrapositive, IFF, and XOR
  * IF: $P \rightarrow Q$ reads as "if P then Q". Equivalent to $\neg P \lor Q$, which means that $P \rightarrow Q$ is false only when $P$ is true while $Q$ is false.
  * Converse: $\neg P \rightarrow \neg Q$. Common pitfall is to believe the converse is equivalent to $P \rightarrow Q$, but that is not true.
  * Contrapositive: $\neg Q \rightarrow \neg P$. Actually equivalent to $P \rightarrow Q$, by De Mogan's Law
  * IFF: $P \leftrightarrow Q$ reads $P$ if and only if (iff) $Q$. Conjunction of $P \rightarrow Q$ and $Q \rightarrow P$.
  * XOR (Exclusive or): $P \oplus Q$ is true if $P$ is true or $Q$ is true, but not both. Negation of IFF. 

    | $P$ | $Q$ | $P \rightarrow Q$ | $\neg P \rightarrow \neg Q$ | $P \leftrightarrow Q$ | 
    | --- | --- | ----------------- | --------------------------- | --------------------- |
    | F   | F   | T                 | T                           | T                     |
    | F   | T   | T                 | F                           | F                     |
    | T   | F   | F                 | T                           | F                     |   
    | T   | T   | T                 | T                           | T                     |

* Negating Quantifiers
  * $\neg \forall P(x) = \exists \neg P(x)$. (i.e. "not all rectangles are squares" = "there exists a rectangle that is not square")
  * $\neg \exists P(x) = \forall \neg P(x)$. (i.e. "there does not exist a horse that can fly" = "all horses cannot fly")
  
