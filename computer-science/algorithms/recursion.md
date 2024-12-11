# Recursion
## Binary Search
* Given a sorted array search if a value exists in the array.
1. If array is empty, we are done as there is nothing to search. 
2. Get the middle of the array
3. If query is equal, then done
4. If query is less, then recursively search left side of the array.
5. Else, then recursively search right side of the array.
* Runtime: Let $T_n$ be the time it takes to search a sorted array of size $n$.
```math
\begin{aligned}
T_n &= T_{n/2} + c \\
  &= (T_{n/4} + c) + c = T_{n/4} + 2*c \\
  &= T_{n/2^k} + k * c \\
  &= T_1 + \log n * c
\end{aligned}
```
* Thus runtime is $O(\log n)$

## MergeSort
1. Split array down the middle.
2. Recursively sort left side
3. Recursively sort right side
4. Merge sides: compare heads of arrays, iteratively pop the lower value and add it to the merged array.
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
1. Choose a pivot in the array. This can be any value.
2. Partition the array so that values lt pivot are left of it and values gt pivot are right of it.
3. Recursively partition values left of pivot
4. Recurisvely partition values right of pivot
* Worst case: we choose the min or max val to be pivot.
* Best case: we choose median to be pivot.
* Assuming best case our runtime is same as mergesort $O(n \log n)$ 

## Master's Theorem
* Given a recursive runtime of the form. We can generalize the runtime. 
```math
T_n = b T_{n/b} + g(n)
```
* $b$ is the branching factor, $g(n)$ is how much work we do at every branch.
