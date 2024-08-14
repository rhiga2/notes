Autoencoders and GANs
==============
# Autoencoders
* An autoencoder is a neural network that learns to replicate the input as the output. 
* Autoencoders consist of an encoder and a decoder. The encoder $f_\phi$ maps the input to a latent space representation, and the decoder $g_\theta$ maps the latent space representation to the output.
* We want the latent space to be a lower dimension $d$ than the input space dimension $m$. This assumes that the input data has some underlying structure that can be captured in a lower dimension.
* The loss function of the autoencoder (also known as reconstruction loss) measures how well the output resembles the input. 
```math
J(\phi, \theta) = E[ \mathcal{L}(x, g_\theta(f_\phi(x)))]
```
* Normally this loss is measure by the mean squared error between the input and output.
```math
J(\phi, \theta) = E[ \Vert x - g_\theta(f_\phi(x)) \Vert_2^2]
```

## Why Encode Information?
* Representation learning: Learn a representaiton of input data that can be useful for downstream tasks.
* Dimensionality reduction: Reduce the number of features in the input data.
* Generative modeling: Learn an underlying distribution of the data. This is often done by imposing a distribution on the latent space (as in the case of variational autoencoders VAEs). We can then sample from the imposed distribution and pass it through the decoder to generate new data.
* Denoising: Learn a representation of the input data that is robust to noise.
* Anomaly detection: Spot anomalies by detecting when data deviates from the underlying distribution.
* Multimodality: Represent different inputs in the same latent space. 
* Decoupling: Allows for disentangled representations of the input data for example separating style and content in images. 


# Variational Autoencoders
* Instead of treating the encoder-decoder as deterministic functions, we can treat them probabilistic functions $q_\phi(z | x)$ and $p_\theta(x | z)$ respectively.
* We assume that $q_\phi(z | x)$ is a Gaussian distribution with mean $\mu_\phi(x) \in \mathbb{R}^d$ and standard deviation $\sigma_\phi(x) \in \mathbb{R}^d$.
```math
q_\phi(z | x) = \mathcal{N}(z | \mu_\phi(x), \text{diag}(\sigma_\phi(x)))
```
* Note that standard deviation is positive so we can have the encoder predict the log variance $\psi_\phi(x)$ and exponentiate it to get the standard deviation. 
```math
\sigma_\phi(x) = \exp(0.5 \psi_\phi(x))
```
* In the forward pass, we sample $z$ from $q_\phi(z | x)$ and pass it through the decoder $p_\theta(x | z)$ to get the reconstructed output.
* The loss function for data $x$ is the negative ELBO:
```math 
\begin{aligned}
J(\phi, \theta) & = -F(q_\phi, \theta) \\
    & = -E_{z \sim q_\phi(\cdot | x)} \left[ \log p_\theta(x | z) \right] + D_{KL}(q_\phi(\cdot | x) \Vert q) 
\end{aligned}      
```
* Note that in practice $q$ is a standard Gaussian distribution $\mathcal{N}(0, I)$.
* KL divergence of two Gaussian distributions is given by:
```math
D_{KL}(p \Vert q) = \frac{1}{2} \left( \text{tr}(\Sigma_q^{-1} \Sigma_p) + (\mu_q - \mu_p)^T \Sigma_q^{-1} (\mu_q - \mu_p) - d + \log \frac{\text{det}(\Sigma_q)}{\text{det}(\Sigma_p)} \right)
```
* Plugging in the values for $q_\phi(z | x)$ and $q(z)$, we get:
```math
D_{KL}(q_\phi \Vert q) = \frac{1}{2} \left( \sum_{j=1}^d (\sigma_{\phi, j}^2(x) - 1 + \mu_{\phi, j}^2(x) - \log \sigma_{\phi, j}^2(x))  \right)
```

## The Reparameterization Trick
* In the forward pass, we sampled from a Gaussian distribution. How do we backpropagate through sampling?
* We instead sample from a standard Gaussian distribution $\epsilon \sim \mathcal{N}(0, I)$ and transform it to $z$ using the mean and variance output by the encoder:
```math
z = \mu_\theta(x) + \sigma_\theta(x) \odot \epsilon
```
* With the reparametrization trick, we decoupled randomness from the forward pass. This allows us to backpropagate.

    ```mermaid
    flowchart LR
        A(X) --> B(Encoder Block)
        B --> C(mu)
        B --> D(sigma)
        F(z) --> E 
        C --> E(mu + sigma * z)
        D --> E
        E --> G(Decoder)
        G --> H(Y)
    ```

## Advantages of VAEs
* VAEs have continous latent space meaning that we can interpolate between points in the latent space. 
* Since the latent space is continuous, we can sample from the latent space and pass it through the decoder to generate new data. 

# Generative Adversarial Networks (GANs)
* GANs consist of two neural networks: a generator $g_\theta$ and a discriminator $f_\phi$. 
* The generator is similar to the decoder in VAEs. It takes a sampled input from latent space and generates data.
* The discriminator is a binary classifier that distinguishes between real data and generated data.
* Both networks are trained simultaneously in a min-max game:
```math
\begin{aligned}
V(\phi, \theta) & = E_{x \sim p_{\text{data}}} \left[ \log f_\phi(x) \right] + E_{z \sim p(z)} \left[ \log (1 - f_\phi(g_\theta(z))) \right] \\
\end{aligned}
```


