Dynamic Programming
==================

# Introduction
## Elements of Dynamic Programming
1. Define how to solve a problem recursively, meaning that you want to break up a larger problem in smaller subproblems.
2. Store the solutions to subproblems in a data structure.
3. Evaluate the solution to subproblems in a bottom-up manner. Meaning subproblems are solved before the larger problem.

# 1D Array Examples
## Fibonacci Sequence
* Given a number $n$, find the $n$th Fibonacci number.
1. Define recursion. Let $F(n)$ be the $n$th Fibonacci number.
$$
F(n) = \begin{cases}
    0 & \text{ if } n = 0 \\
    1 & \text{ if } n = 1 \\
    F(n - 2) + F(n - 1) & \text{ otherwise} \\
\end{cases}
$$
2. We can only need $F(n-2)$ and $F(n-1)$ to calculate $F(n)$. We can store store solution of these subproblems in two variables `prev1` and `prev2` respectively. 
3. Evaluate the solution to subproblems from left to right.
```python
def fibonacci(n):
    prev1, prev2 = 0, 1
    if n == 0:
        return prev1
    elif n == 1:
        return prev2
    
    for i in range(n - 1):
        curr = prev1 + prev2 
        prev1, prev2 = prev2, curr
    return curr
```

## Largest Consecutive Sum (Kadane's Algorithm)
* Given an array of integers, find the largest sum of consecutive elements in the array.
1. Define recursion. Let $A$ be the input array and $S(j)$ be the largest sum of consecutive elements ending at $A[j]$.
$$
S(i) = \begin{cases}
    A[0] & \text{ if } i = 0 \\
    \max(S(i - 1) + A[i], A[i]) & \text{ otherwise} \\
\end{cases}
$$
2. We only need to store $S(i - 1)$ to calculate $S(i)$. We store $S(i-1)$ in variable `local_max`. 
3. Evaluate subproblems from left to right. 
```python
def largest_consecutive_sum(A):
    global_max = None
    local_max = 0
    for i in range(len(A)):
        local_max = max(local_max + A[i], A[i])
        if global_max is None or local_max > global_max:
            global_max = local_max
    return global_max
```

# Relationship to DFS
* Dynamic programming depends on a recursive structure of subproblems. 
* We can create a directed acyclic graph where each node represents a subproblem and edges represent dependencies. For example, `A -> B` indicates subproblem `A` dependengs on subproblem `B`.
* DP solves subproblems before going to problems that depend on them. Thus we need to solve problems in a reverse topological order.