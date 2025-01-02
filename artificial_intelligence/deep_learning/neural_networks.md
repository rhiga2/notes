# Neural Networks
## Computational Graphs
## Fully-Connected NNs
## Training Practices
## Convolutional NNs
### 1D Convolution

### 2D Convolution

## Recurrent NNs
## Transformers
### Scaled Dot Product Attention
* Inputs are three tensors key $K$, query $Q$, and value $V$. Each key and query vector has dimension $d$
```math
\begin{gathered}
S = \frac{Q K^T}{\sqrt d} \\
A = \text{softmax}(S)V
\end{gathered}
```
### Self-Attention
* Self-attention means that key, query, and value are derived from the same source of data X.
```math
\begin{gathered}
K = W_K X \\
V = W_V X \\
Q = W_Q X
\end{gathered}
```

### Multi-Headed Attention 

### Masking (or Causal) Attention
* Given a sequence keys and values. We sometimes don't want a later key-value to be retrieved by query that comes before it.
* We want to mask out scores before normalization with softmax. 
```math
S_{ij} = \begin{cases}
q_i k_j^T & i >= j\\
-\infty & \text{else} 
\end{cases} 
```  

