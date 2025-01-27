Deep Learning
=============
# Computational Graphs
# Fully-Connected NNs
* FC networks have an affine (linear) layer followed by a non-linear activation function.
```math
\begin{gathered}
z = w^T x + b \\
y = g(z)
\end{gathered}
```
* Activation $g$ must be non-linear since we often compose layers. Composition of linear layers can only express linear functions.  

# Convolutional NNs

# Recurrent NNs
* RNNs are networks with skip connections. A skip connection on block $g$ adds $g$'s input with $g$'s output.
```math
y = g(x) + x
```

# Transformers
## Scaled Dot Product Attention
* Inputs are three tensors key $K$, query $Q$, and value $V$. Each key and query vector has dimension $d$
```math
\begin{gathered}
S = \frac{Q K^T}{\sqrt d} \\
A = \text{softmax}(S)V
\end{gathered}
```
## Self-Attention
* Self-attention means that key, query, and value are derived from the same source of data X. 
```math
\begin{gathered}
K = W_K X \\
V = W_V X \\
Q = W_Q X
\end{gathered}
```

## Multi-Headed Attention 
* Each attention head takes input $X$ and produces triplet $(K, Q, V)$. Thus each head has it's own set of three weight matrices. 
* Intuition is that each attention head focuses on different aspects of the input.

## Masked Attention
* Given a sequence keys and values. We sometimes don't want a later key-value to be retrieved by query.
* We want to mask out scores before normalization with softmax. 
```math
S_{ij} = \begin{cases}
q_i k_j^T & i >= j\\
-\infty & \text{else} 
\end{cases} 
```  

