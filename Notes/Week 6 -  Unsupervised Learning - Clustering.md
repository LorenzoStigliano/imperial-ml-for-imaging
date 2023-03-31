- We have no labels for our data and so we try to achieve the following tasks
	- Clustering Dimensionality 
	- Reduction 
	- Anomaly Detection
- Unsupervised Learning aims to understand the structure in data

## Clustering 

- Given some data we are interested automatic semantic indexing 
- Sometimes gathering annotations / “ground truth” can be costly or cumbersome 
- Clustering could also identify novel ways to group subsets of data semantically

Goal: MR soft tissue segmentation, unsupervised image segmentation ![[Screenshot 2023-02-13 at 10.24.45.png]]

### K-means clustering 
![[Screenshot 2023-02-13 at 10.25.13.png]]
- Bad initialisation can yield bad clustering

#### Does K-Means optimize a cost function?

- Solves initialization problem: multiple reinitializations, pick the best cost 
- Explains some properties of K-Means → new ways to improve it
![[Screenshot 2023-02-13 at 10.26.26.png]]
- $z_{nk}$  assignment of data point to centroid

#### K-Means caveats
- Prefers ≃ same size clusters 
- Cost function is greedy and is dependant on the initial state
- K-Means handles anisotropic data and non-linearities poorly
	- Crosses intuitive low-density splits

### Gaussian Mixture Model (GMM)

- To represent 1 cluster, use a statistical model (e.g. multivariate Gaussian) 
- Use a mixture thereof for several clusters / the data
- Weighted sum of normal distributions ![[Screenshot 2023-02-13 at 10.36.06.png]]
- Robust to choosing right number of clusters

### Expectation-Maximization (optimization)
![[Screenshot 2023-02-13 at 10.40.29.png]]

### How do we choose number of clusters?

1. “Elbow” method![[Screenshot 2023-02-13 at 10.44.44.png]]
2. Application-based rationale - if you know from before hand 
3. Other methods
	1. Bayesian Mixture Models: don’t choose, use priors! 
	2. Persistence diagrams / persistent homology

### Data geometry: non-linearities

- K-Means handles anisotropic data and non-linearities poorly
- Idea 1. Lift data to a feature space where it can be described in linear terms
	- Kernel methods • e.g., support vector clustering, kernel k-Means (for clustering) 
	- Neural Networks
- Idea 2. Geometry-inspired formulation, “manifold of data”
	- "Manifold Learning”, “nonlinear dimensionality reduction” (e.g. MDS, Isomap, LTSA, t-SNE, UMAP) 
	- Well-suited to data visualisation