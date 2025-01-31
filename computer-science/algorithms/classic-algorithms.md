Classic Algorithms
===================
# Divide and Conquer
## Binary Search
* Given a sorted array $A$ search if a value exists in the array.
```
BinarySearch(A, x):
  m = middle of A
  if x < m:
    BinarySearch(A's left side, x)
  elif x > m
    BinarySearch(A's right side, x)
  else:
    we found x
```
* Runtime: Let $T_n$ be the time it takes to search a sorted array of size $n$.
```math
\begin{aligned}
T_n &= T_{n/2} + c \\
  &= (T_{n/4} + c) + c = T_{n/4} + 2*c \\
  &= T_{n/2^k} + k * c \\
  &= T_1 + \log n * c
\end{aligned}
```
* Thus runtime is $O(\log n)$, which is faster than going though each element one-by-one.

## MergeSort
```
Mergesort(A):
  MergeSort(A's left half)
  MergeSort(A's right half)
  Merge(left half, right half)

Merge(L, R):
  result = empty
  while L and R are non-empty:
    compare the first elements of L and R
    add smaller element to result
  if one array is empty:
    add the other array to the result
```
* Runtime: Let $T_n$ be the time it takes to mergesort an array of size n.
```math
\begin{aligned}
T_n &= 2*T_{n/2} + cn \\
  &= 2*(2 * T_{n/4} + c \frac{n}{2}) + c*n = 4*T_{n/4} + 2cn \\
  &= 2^k T_{n/k} + kcn \\
  &= n T_1 + c n \log n
\end{aligned}
```
* Thus runtime is $O(n\log n)$

## QuickSort
```
QuickSort(A):
  p = choose pivot value in A
  partition A so that values < p are left of pivot and values > p are right of pivot
  QuickSort(left of pivot in A)
  QuickSort(right of pivot in A)
```
* Worst case: we choose the min or max val to be pivot.
* Best case: we choose median to be pivot.
* Assuming best case our runtime is same as mergesort $O(n \log n)$. 

## Master's Theorem
* Given a recursive runtime of the form. We can generalize the runtime. 
```math
T_n = b T_{n/b} + g(n)
```
* $b$ is the branching factor, $g(n)$ is how much work we do at every branch.

# Trees Algorithms
## Terminology
* A tree is composed of nodes. Each node has a value and a list of child nodes.
* Binary trees only have two children.

## Binary Search Tree
* Binary search trees 

# Graph Algorithms
## Terminology
* Graphs have a set of vertices $V$ and edges $E$. Edges are pairs of vertices.
* If pair is an ordered pair, then graph is directed. Otherwise graph is undirected.
* Degree is the number of edges connecting to a vertex. Directed graph have an inbound and outbound degree.

## Whatever First Search
```
WhateverFirstSearch(s):
  add s to bag
  mark s as visited
  while bag is non-empty:
    n = pop node from bag
    for children of n:
      if n has not been visited:
        add n to bag
```
* The bag type controls what type of graph search.
| Bag        | Type of Search | 
| ---------- | -------------- |
| Queue      | Breadth First  |
| Stack      | Depth First    |
| Priority Q | Djikstra       |

## Depth-First Search

## Minimum Spanning Tree

# Dynamic Programming
## Dynamic Programming
* Dynamic programming algorithms have the following:
  * Recursive relation: Problems can be broken into subproblems.
  * Data structure memorizing the results of subproblems
  * Ordered evaluation of subproblems   

## Relationship to DFS
* Dependency Graph: If problem $A$ has a directed edge to $B$, then that means that $A$ depends on $B$.
* Recursive relations in dynamic programming form a acyclic dependency graph.
* DP = DFS (specifically reverse topological traversal) on the dependency graph 

