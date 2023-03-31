## Classes of methods
- Model agnostic (ignores forward model)
- Decoupled (First learn, then reconstruct)
- Unrolled optimisation

## 1. Model agnostic 
![[Screenshot 2023-02-20 at 10.27.17.png]]
- We ignore what we did in the forward model
- We directly use a NN to train a the backward model

Partly model agnostic 
- We upsample the image and then train NN to remove artefacts, notice that we know that down-sampling exisits so we incorporate this information![[Screenshot 2023-02-20 at 10.30.13.png]]

## 2. Decoupled
![[Screenshot 2023-02-20 at 10.31.00.png]]
- We replace the second step to de-noise the $z^k$ solution we calculated using traditional methods.
- Can be trained offline - train after iterative gradient descent DC![[Screenshot 2023-02-20 at 10.32.55.png]]
- We want to learn an image manifold for natural images ![[Screenshot 2023-02-20 at 10.33.46.png]]
- To learn this manifold we use GANs
- D(x) represents the probability that x came from the real data rather than from G.
- D is trained to maximize the probability of assigning the correct label to both real examples and samples from G (fake).
- Simultaneously train F to minimize log(1 − D(G(z)), e.g. D and G play a two-player minimax game:![[Screenshot 2023-02-20 at 10.36.03.png]]
- Once the GAN is learn we have the following: ![[Screenshot 2023-02-20 at 10.36.41.png]]![[Screenshot 2023-02-20 at 10.36.59.png]]
- This forces the image to be realistic 

## 3. Unrolled optimisation

- Let’s assume that ℛ(x) is differentiable![[Screenshot 2023-02-20 at 10.40.40.png]]
- We replace the gradient on the regulariser with a learned neural network 
- Top branch is the gradient descent on data consistency 
- Bottom is on the regularisation term 