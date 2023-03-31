- How to encode high dimensional data:
	- Idea 1. Exploit redundancies in image 
	- Idea 2. Exploit redundancies in dataset

Applications
- Data visualisation
- Image compression
- Modelling

## PCA 
![[Screenshot 2023-02-13 at 14.15.49.png]]
![[Screenshot 2023-02-13 at 14.16.44.png]]

Example: Dataset with 200 spines, 26 points

- We have 3d coordinates of the spine
- We want to understand the spine anatomy ![[Screenshot 2023-02-13 at 14.24.01.png]]
- Above we plot the spines in 3 dimensions and we can see the variation within the data set
- PCA:![[Screenshot 2023-02-13 at 14.24.48.png]]
	- Black line is the mean spine across all samples
	- The first principal component shows the length of the spine

### PCA image model
![[Screenshot 2023-02-13 at 14.27.09.png]]

### Active Appearance Model (AAM)
![[Screenshot 2023-02-13 at 14.29.31.png]]
- Points model expression 
- Shape-free patch - intensity based image which is normalised
- Testing (new image): iterative optimization of the AAM “PCA parameters” to minimize reconstruction error
	- Difference between initial and target image 
	- Now we know the representation of the target image 

### PCA Interpretations
![[Screenshot 2023-02-13 at 14.32.59.png]]
![[Screenshot 2023-02-13 at 14.35.09.png]]
## Auto-encoders
![[Screenshot 2023-02-13 at 14.35.22.png]]
![[Screenshot 2023-02-13 at 14.38.12.png]]
How do autoencoders not just learn the identity map? 
1. Bottleneck in the code: dim(𝑧) ≪ dim(𝑥)
2. Add regularization: ℒ𝜙,𝜃 + 𝜆 ⋅ ℛ(𝜙, 𝜃) e.g. Regularized AE, Sparse AE, Contractive AE 
3. By training on corrupted input 𝑥 (Denoising AE): ex. Gaussian noise, “dropout” (randomly set 𝑝% network activations to 0)

Unlike PCA, non trivial to: 
- visualize data in the latent space of Autoencoders
- generate new samples![[Screenshot 2023-02-13 at 14.39.35.png]]
