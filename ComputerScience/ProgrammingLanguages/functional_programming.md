Functional Programming
======================

# What is Functional Programming?
* Functional programming is a programming paradigm that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

# Key Concepts
* First class citizens can be:
    * Assigned to a variable
    * Passed as arguments to other functions
    * Returned as values from other functions
* Pure functions have no side effects and are deterministic. 

# Recursion
* Recursion is a technique where a function calls itself with "smaller" input to solve a problem. 
* Structured similar to induction proofs where we have a base case and an inductive step, which we call the recursive case. 
    ```haskell
    factorial :: Integer -> Integer
    factorial 0 = 1
    factorial n = n * factorial (n - 1)
    ```

## Tail Recursion
* Tail recursion is a special form of recursion where the returned subexpression is either a base case or a recusive call only.
* Tail recursion can be optimized by the compiler.
```haskell
factorial :: Integer -> Integer
factorial n = aux n 1
    where aux 0 a = a
            aux n a = aux (n - 1) (n * a)
```

## Continuations
* Continuations are functions that represent the future of a computation.
* Continuation passing style (CPS) programs pass continuations as an argument to each function.
* Programs in CPS are tail recursive and can be optimized by the compiler. 
* CPS can manipulate the control flow of the program whereas regular tail recursion does not. For example, CPS can similate multitasking and exceptions. 
* Converting functions from direct style to CPS involves passing a continuation $k$ as an argument to the function. 
* Conversion cases:
    1. Expressions with no function calls: apply continuation to expression.
    2. Expressions with single, outer function call: pass the continuation to the function call.
    3. Other expressions: create a new continuation that applies the original continuation to the result of the expression.
* Example convert the following function to CPS:
```haskell
foo :: Int -> Int
foo 0 = 0
foo n | n < 0 = foo (n+1)
      | otherwise = inc(foo (n - 1))
```
* Converted to CPS:
```haskell
foo :: Int -> (Int -> Int) -> Int
foo 0 k = 0
foo n | n < 0 = foo (n+1) k
      | otherwise = foo (n - 1) (\v -> inc v k)
```

## Higher Order Functions
* Higher order functions are functions that take other functions as arguments or return functions as results.

## Map Function
* The `map` function applies a function `f` to each element of a list.
```haskell
map :: (a -> b) -> [a] -> [b]
map f [] = []
map f (x:xs) = f x : map f xs
```

## Foldr Function
* The `foldr` function reduces a list to a single value by applying a function `f` to each element of the list.
```haskell
foldr :: (a -> b -> b) -> b -> [a] -> b
foldr f z [] = z
foldr f z (x:xs) = f x (foldr f z xs)
```

# Algebraic Data Types
## Product Types
* Product types are types that contain multiple values. Examples include tuples and records. The `Point` class is an example of a record. 
```haskell
data Point = Point { x :: Int, y :: Int }
```

## Sum Types
* Sum types are types that can have multiple forms. The following example shows how to implement a linked list and a binary tree.
```haskell
data List a = Nil 
            | Cons a (List a)
data BTree a = Nil
            | Node a (BTree a) (BTree a)
```

### Maybe Type
* The `Maybe` type is a sum type that represents a value that may or may not exist.
    ```haskell
    data Maybe a = Nothing
                 | Just a
    ```

### Either Type
* The `Either` type is a sum type that represents a value that can be one of two types. The left side usually has error messages, and the right side usually has the results of successful computation.
    ```haskell
    data Either a b = Left a
                    | Right b
    ```

# Continuation Passing Style (CPS)
* Continuation passing style (CPS) is a programming style where functions take an extra argument, the continuation, which is a function that represents the future of the computation.
* CPS can be used to implement control flow constructs like exceptions and coroutines.

# Type Classes
* Polymorphism in Haskell is achieved through type classes.
* Type classes define a set of functions (similar to interfaces) that can be implemented for a type. Thus different types can have different implementations of the same function. 

# Functors, Applicatives, and Monads
## Functors
* Functors define the `fmap` function that unwraps the container, applies a function to the value, and wraps the result back in the container.
```haskell
class Functor f where
    fmap :: (a -> b) -> f a -> f b

instance Functor Foo where
    fmap f (Foo x) = Foo (f x)
```

## Applicatives
* Applicatives define two functions:
    * `pure` which wraps a value in a container
    * `<*>` which applies a function within a container to a value within a container.
```haskell
class Functor f => Applicative f where
    pure :: a -> f a
    (<*>) :: f (a -> b) -> f a -> f b

instance Applicative Foo where
    pure x = Foo x
    (Foo f) <*> (Foo x) = Foo (f x)
```

## Monads
* Monads define two functions:
    * `return` which wraps a value in a container. This is usually the same as `pure`.
    * `>>=` (bind) which applies a function that returns a container to a value within a container.
```haskell
class Applicative m => Monad m where
    return :: a -> m a
    (>>=) :: m a -> (a -> m b) -> m b

instance Monad Foo where
    return x = Foo x
    (Foo x) >>= f = f x
```
* Note that monads are more powerful than applicatives since `f` has control over how the computation is wrapped.

## Representing State with Monads 

