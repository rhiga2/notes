# Lambda Calculus
## Syntax of Lambda Calculus
### Components of Lambda Calculus
* Lambda calculus consists of
    * Variables: Variables are represented by one letter $x, y, z$
    * Abstraction: Abstraction is a function definition that binds a variable to a function body. It is represented by $\lambda x. M$
    * Application: Application is the process of applying a function to an argument. It is represented by $M N$
* Variables can be bound or free. 
    * Bound variables are variables that are defined within a function. For example, $\lambda x.x$ has a bound variable $x$.
    * Free variables are variables that are not defined within a function. For example, $\lambda x.y$ has a free variable $y$.

### Operations in Lambda Calculus
* Lambda calculus has the following operations:
    * Beta reduction: Beta reduction is the process of applying a function to an argument. It is represented by $(\lambda x. M) N \rightarrow M[x := N]$
    * Alpha conversion: Alpha conversion is the process of renaming bound variables. It is represented by $\lambda x. M \rightarrow \lambda y. M[x := y]$.

## Representing Data Types in Lambda Calculus
### Church Numerals
* Church numerals are a way to represent natural numbers in lambda calculus.
 ```math
 \begin{align*}
 f_0 & = \lambda f. \lambda x. x \\
 f_1 & = \lambda f. \lambda x. fx \\
 f_2 & = \lambda f. \lambda x. f(fx) \\
 & ... \\
 f_n & = \lambda f. \lambda x. f^n x \\
 \end{align*}
 ```
* We can define arithmetic operations on Church numerals using lambda calculus. Let $m$ and $n$ be Church numerals.
 ```math
 \begin{gathered}
 f_{\text{add}} = \lambda m. \lambda n. \lambda f. \lambda x. m f (n f x) \\

 f_{\text{mult}} = \lambda m. \lambda n. \lambda f. m (n f) \\
 \end{gathered}
 ```

### Church Booleans
* Church booleans are a way to represent boolean values in lambda calculus.
 ```math
 \begin{aligned}
 T & = \lambda x. \lambda y. x \\
 F & = \lambda x. \lambda y. y \\
 \end{aligned}
 ```
* We can define logical operations on Church booleans using lambda calculus.
 ```math
 \begin{gathered}
 f_{\text{and}} = \lambda p. \lambda q. p q F \\
 f_{\text{or}} = \lambda p. \lambda q. p T q \\
 f_{\text{not}} = \lambda p. p F T \\
 \end{gathered}
 ```
 * A good way of visualize these operators is with a truth table:
   | a | b | c | abc |
   | --- | --- | --- | --- |
   | $F$ | $F$ | $F$ | $F$ (and)  |
   | $F$ | $F$ | $T$ | $T$ (not) |
   | $F$ | $T$ | $F$ | $F$ (and, or) |
   | $F$ | $T$ | $T$ | $T$ (or) |
   | $T$ | $F$ | $F$ | $F$ (and) |
   | $T$ | $F$ | $T$ | $F$ (not) |
   | $T$ | $T$ | $F$ | $T$ (and, or) |
   | $T$ | $T$ | $T$ | $T$ (or) |

### Representing ADTs with Lambda Calculus
* If an ADT, has $n$ constructors, we can represent it with a abstraction with $n$ arguments.
* A list type can be represented as:
```math
\begin{align*}
\text{Nil} & = \lambda cn.n \\
\text{Cons} \: x \: y & = \lambda cn.cxy \\
\end{align*}
```
* A maybe type can be represented as:
```math
\begin{align*}
\text{Nothing} & = \lambda jn.n \\
\text{Just} \: a & = \lambda jn.ja \\
\end{align*}
``` 

## Lambda Calculus and Recursion
### Y-Combinators
