# Functional Programming

## What is Functional Programming?
* Functional programming is a programming paradigm that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

## Key Concepts
* First class citizens can be:
    * Assigned to a variable
    * Passed as arguments to other functions
    * Returned as values from other functions
* Pure functions have no side effects and are deterministic. 

## Recursion
* Recursion is a technique where a function calls itself with "smaller" input to solve a problem. 
* Structured similar to induction proofs where we have a base case and an inductive step, which we call the recursive case. 
    ```haskell
    factorial :: Integer -> Integer
    factorial 0 = 1
    factorial n = n * factorial (n - 1)
    ```

### Tail Recursion
* Tail recursion is a special form of recursion where the returned subexpression is either a base case or a recusive call only.
* Tail recursion can be optimized by the compiler.
    ```haskell
    factorial :: Integer -> Integer
    factorial n = aux n 1
        where aux 0 a = a
              aux n a = aux (n - 1) (n * a)
    ```

### Higher Order Functions
* Higher order functions are functions that take other functions as arguments or return functions as results.

### Map Function
* The `map` function applies a function `f` to each element of a list.
    ```haskell
    map :: (a -> b) -> [a] -> [b]
    map f [] = []
    map f (x:xs) = f x : map f xs
    ```

### Foldr Function
* The `foldr` function reduces a list to a single value by applying a function `f` to each element of the list.
    ```haskell
    foldr :: (a -> b -> b) -> b -> [a] -> b
    foldr f z [] = z
    foldr f z (x:xs) = f x (foldr f z xs)
    ```

## Algebraic Data Types
### Product Types
* Product types are types that contain multiple values. Examples include tuples and records.
    ```haskell
    data Point = Point { x :: Int, y :: Int }
    ```
    The `Point` class is an example of a record. 

### Sum Types
* Sum types are types that can have multiple forms.
    ```haskell
    data List a = Nil 
                | Cons a (List a)
    data BTree a = Nil
                | Node a (BTree a) (BTree a)
    ```
    Example of recursive data structures: linked lists and binary trees.

#### Maybe Type
* The `Maybe` type is a sum type that represents a value that may or may not exist.
    ```haskell
    data Maybe a = Nothing
                 | Just a
    ```

#### Either Type
* The `Either` type is a sum type that represents a value that can be one of two types. The left side usually has error messages, and the right side usually has the results of successful computation.
    ```haskell
    data Either a b = Left a
                    | Right b
    ```
