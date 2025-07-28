Probability
=============
# Axioms of Probability and Random Variables
## Probability Space 
* A probability space consists three components. 
1. A sample space $\Omega$ that describes all possible outcomes.
2. A event space $F$ consisting of subsets of $\Omega$.
3. A probability measure $P$ that map a subset to a real number in $[0, 1]$.

## Kolmogorov's Axioms
1. Non-negativity: $P(A) \ge 0$ for any event $A \in F$.
2. Unity: $P(\Omega) = 1$.
3. Additivity: If events $A_1, A_2, ...$ are mutually exclusive (no overlap), $P(\bigcup_{i=1}^{\infty} A_i) = \sum_{i=1}^{\infty} P(A_i)$.

## Derived Properties
* There are a number of imporatant properties that can be derived from axioms. 
* Complements: $P(A) = 1 - P(A^c)$. 
* Subsets: If $A \subseteq B$, then $P(A) \le P(B)$. 
* Upper limit: $P(A) \le 1$.
* Inclusion and Exclusion: If $A$ and $B$ are not mutually exclusive, $P(A \cup B) = P(A) + P(B) - P(AB)$.

## Intepretations of Probability
* Freqeuntist: $P(A)$ indicates the frequency that event $A$ occurs over repeated trials. Such as probability a coin is heads under repeated flips. 
* Bayesian: Sometimes we may not have a lot of repeated trials regarding an outcome. In Bayesian intepretation, $P(A)$ indicates our belief about the likehood of $A$ occurring. Once we observe data we can update our beliefs using Bayes rule. 

## Random Variables 
* A random variable is a function mapping an outcome to a real number.
* $X$ is a discrete random variable if the values of $X$ can be assigned probability.
  * The function that assigned probability to a random variable is called a mass function denoted as $p(x) = P(X=x)$
  * Note that summing over all values of $X$ equal to $1$. $\sum_x p(x) = 1$
* $X$ is a continuous random variable if all values of $X$ cannot be assigned probability.
  * In this case, we can only assign probabilities to intervals of values. Thus each value of $X$ is assigned a density given by density function $p(x) = P(x < X < \delta x)$.
  * For interval $I$, the probability assigned to that interval $P(X \in I) = \int_I p(x) dx$.
  * Not if $I$ is the entire real line, $\int_{-\infty}^{\infty} p(x) dx = 1$.
* The cumulative distribution function $P(x) = P(X \le x)$ shows the cumulative probability of all values less than $x$.
  * Unlike the mass or density functions, CDF is defined for both discrete and continuous random variables.
  * For discrete random variables, $P(x) = \sum_{i=\infty}^x p(u)$. 
  * For continuous random variables, $P(x) = \int_{\infty}^x p(u) du$. Note that by the fundamental theorem of calculus, the density function is the derivative of the CDF.
  * CDF is monotonically non-decreasing since it's a cumulative function.
  * CDF goes from $0$ to $1$.

# Joint and Conditional Distributions
## Joint Distributions
* The joint distribution is defined by $p(x, y) = p(X=x, Y=y)$ for discrete random variables.
* Likewise for continuous distributions: $p(x, y) = P(x < X < \delta x, y < Y < \delta y)$
* The sum rule (aka marginalization), says that we can sum (or integrate) a joint distribution of multiple variables to get the distribution of a single variable:
```math
p(x) = \sum_y p(x, y)
```

## Condtional Distributions
* $p(x | y)$ indicates the probability distribution of random variable $X$ given what we know about $Y$. 
```math
p(x | y) = \frac{p(x, y)}{p(y)}
```
* Product rule (aka chain rule) is just a algebraic manipulation of the definition $p(x, y) = p(x | y) p(y)$

## Bayes Rule
* In Bayesian interpretation, we mentioned that our belief about an outcome or random variable can be updated with evidence. The rule for updating is called Bayes Rule, which is a manipulation of the definition of conditional probability.
```math
p(y | x) = \frac{p(x|y) p(x)}{p(y)}
```
* Our initial belief before evidence (called prior) denoted as $p(y)$.
* After receiving evidence $x$, we update pur belief (called posterior) denoted as as $p(y | x)$.   

# Transformations of Random Variables (TODO)

# Information Theory
## Entropy
## Kullback-Leiber Divergence
* The KL divergence measures the dissimilarity between two distributions. 
* Non-negativity and Jensen's inequality
## Conditional and Joint Entropy
* Conditional entropy $H[Y|X]$ is the expected additional information needed to specify $Y$ given $X$. 
```math
H[X, Y] = H[Y | X] + H[X] 
```
## Mutual Information and Independence



