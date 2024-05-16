# Functional Programming

## What is Functional Programming?
* Functional programming is a programming paradigm that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

## Key Concepts
* First class citizens can be assigned to a variable, passed as a param, or returned from a function. In functional programming, functions are first class citizens.
* Pure functions have no side effects and is deterministic. Same input gives same output. 

## Recursion
* Recursion is a technique where a function calls itself with "smaller" input to solve a problem. 
    ```haskell
    factorial :: Integer -> Integer
    factorial 0 = 1
    factorial n = n * factorial (n - 1)
    ```
