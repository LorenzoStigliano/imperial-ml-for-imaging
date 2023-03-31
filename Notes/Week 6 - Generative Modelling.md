
## Generative Modelling

- Model the process through which data is generated 
- Capture the structure in the data e.g., dependencies, causal links… 
- Mostly subsumes other tasks: clustering, dimensionality reduction…
- Introduce *latent* (≜ unobserved, unknown) parameters if necessary. Since they are unknown, assign probability distributions to them 
- Bayesian framework allows to 
	- Model probabilistically, manipulate probabilistic variables (= distributions)
	- make optimal predictions in the presence of unknown
- We learn the underlying latent variables and then we can learn the distribution to generate from the latent variable

![[Screenshot 2023-02-13 at 15.02.06.png]]
- We learn the parameters of the generative model
- At test time we want to learn encoding or a clustering of the model 
- We can also generate new samples![[Screenshot 2023-02-13 at 15.06.11.png]]
- Also we can do outlier detection ![[Screenshot 2023-02-13 at 15.06.27.png]]
### Example 1: PCA as a linear generative model
![[Screenshot 2023-02-13 at 15.07.48.png]]
- The above is to generate new data 
- Notice that $\mu$ and $U$ are generated via PCA ![[Screenshot 2023-02-13 at 15.10.12.png]]
- The first one is the true model 
- The second is the PCA without noise 
- Third is PCA with noise - we can see that the fitted model is worse![[Screenshot 2023-02-13 at 15.12.21.png]]
- Very high penalty for the loss when using a gaussian distribution, thus high cost to the mean
- We use a student-t distribution thus more robust to outliers

### Example 2: GMM generative model (1D data)
![[Screenshot 2023-02-13 at 15.14.59.png]]

## Fully Bayesian GMMs
How many clusters? Don’t choose, use hyperpriors! 
- Dirichlet hyperprior on 𝝅 can favour few (≤ 𝐾max) non-zero cluster proportions 
- Normal-inverse-Wishart hyperprior on 𝜇, Σ avoids degenerate clusters that shrink to zero-variance
![[Screenshot 2023-02-13 at 15.19.40.png]]

## ‘Black-box’ Generative Modelling
DL notes: [[Week 5 - Generative Models]]

- Use generic architectures (NNs) 
- Automatically capture the structure / learn factors responsible for the variation in the data
- Pixel CNN used for interpolation between two images 
- Shape interpolation and arithmetic 

### Variational Auto-encoder (VAE)
DL notes: [[Week 5 - VAE Basics]]
![[Screenshot 2023-02-13 at 15.33.45.png]]
![[Screenshot 2023-02-13 at 15.34.13.png]]
Generating new samples 
![[Screenshot 2023-02-13 at 15.34.25.png]]
![[Screenshot 2023-02-13 at 15.38.50.png]]

### Generative Adversarial Networks (GANs)
DL notes:  [[Week 5 - GANs]]

- GANs = Generator + Discriminator
- GANs optimize a minimax objective designed to encourage high-quality samples Generator tries to fool discriminator.
- Discriminator learns to classify generated vs. real data samples![[Screenshot 2023-02-13 at 15.40.38.png]]

### GANs vs VAE
![[Screenshot 2023-02-13 at 15.41.10.png]]
Active area of research 
- Countless applications: style transfer, image-to-caption, fake news, image inpainting, NLP, sketch-to-photorealistic 
- Coupling VAE- and GAN-like designs, rich learnable priors on the latent space, better network architectures, etc. 
- Disentangling & Data invariances: decoupling and understanding appearance, shape, pose, etc. automatically 
- Adapting models to complex data: proteins, chemical molecules, graphs, shapes