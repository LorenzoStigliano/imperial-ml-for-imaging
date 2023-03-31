- Estimation of transformations parameters is driven by the appearance of the images
- Images are registered when they appear similar
- By looking at the differences between two images we can see that at some points the intensity images look similar
- How do we find non rigid transformations?

### Objective function
- $C(T) = D(IoT, J)$ 
- where $T$ is the transformation $IoT$ is the moving image and $J$ is the fixed target image, $D$ is a dissimilarity measure 
- Problem is $\hat{T} = argmin C(T)$

### Mono-modal vs Multi-modal 

Mono-modal registration 
- mage intensities are related by a (simple) function, they come from the same type of scanner
Multi-modal registration 
- Image intensities are related by a complex function or statistical relationship

### (Dis)similarity Measures

- Sum of square distance (SSD)![[Screenshot 2023-02-07 at 15.13.02.png]]
- Problems - not robust to outliers, artefacts cause problems here 
- Sum of absolute differences (SAD)![[Screenshot 2023-02-07 at 15.13.23.png]]
	- Assumption: identity relationship between intensity distributions 
	- Application: mono-modal registration (e.g. CT-CT)
- Correlation coefficient (CC)![[Screenshot 2023-02-07 at 15.15.44.png]]
	- Assumption: linear relationship between intensity distributions 
	- Application: (mainly) mono-modal registration (e.g. MR-MR)

- For **different modalities** we cannot use the above since the type of scan/image don't map to the same thing it is not a linear relationship
- So we want to see a statistical relationship
- 2D intensity histograms![[Screenshot 2023-02-07 at 15.19.40.png]]
- We go through the pixel locations, so we have pixel pairs and then plot them in the 2D histogram
- We end up with a distribution of the pairs of pixels
- We define bins in which count the number of pairs in each bin to discretise the space
- What happens with the same image when they are registered and miss registered, we see more dispersion as we register worse![[Screenshot 2023-02-07 at 15.22.56.png]]
- More off diagonal measurements worse registration
- Different modalities ![[Screenshot 2023-02-07 at 15.24.43.png]]
- We know want to quantify the dispersion in the patterns 
- It is relative to what the truth is, we can see that the best has the least dispersion
- Also we can look at the compactness of the plots
- Intensity distributions
	- Probability of observing i and j ![[Screenshot 2023-02-07 at 15.27.01.png]]
	- We can then calculate the marginal probabilities![[Screenshot 2023-02-07 at 15.27.30.png]]
	- ![[Screenshot 2023-02-07 at 15.28.07.png]]
	- We can now evaluate the metric: Shannon entropy![[Screenshot 2023-02-07 at 15.28.50.png]]
	- Joint entropy![[Screenshot 2023-02-07 at 15.29.07.png]]
	- Does not work well but :
	- The mutual information works better ![[Screenshot 2023-02-07 at 15.30.54.png]]
	- Normalised mutual information ![[Screenshot 2023-02-07 at 15.37.49.png]]
		- Assumption: *statistical* relationship between intensity distributions 
		- Application: (mainly) multi-modal registration (e.g. CT-MR)
- We can use a translation experiment, they are locally convex functions and are smooth functions thus we can achieve the minimas
- In Multi-modal SSD and CC landscapes are not appropriate ![[Screenshot 2023-02-07 at 15.42.49.png]]

## Image Overlap

- (Dis)similarity measures are evaluated in the overlapping region of the two images
- Problem: if the overlap is very small then the transformation is hard to find with many solutions
- ![[Screenshot 2023-02-07 at 15.43.36.png]]

## Capture Range

- Limitation - Capture range is defined as as we change the alignment with the two images, there is a range for which we can find a solution
- If we are outside the capture range the registration will not work 
- The functions are generally not convex
- Limitation - We need to think of how to initialise the methods such that they converge and that they are inside the capture range ![[Screenshot 2023-02-07 at 15.45.31.png]]
- Limitation - Many local optimas![[Screenshot 2023-02-07 at 15.46.26.png]]

## Multi-scale, hierarchical Registration

- Deals with the above problems
- Successively increase degrees of freedom 
- Gaussian image pyramids, down sample and then blur the image 

## Interpolation

- We are moving one image and not the other 
- The transformations result in coordinates which are off the grid, we need to interpolate at these values ![[Screenshot 2023-02-07 at 15.49.17.png]]

## How do we do the search?
![[Screenshot 2023-02-07 at 15.50.34.png]]
- Optimisation Strategies:  ▪ Gradient-descent ▪ Stochastic optimisation ▪ Bayesian optimisation ▪ Discrete optimisation ▪ Convex optimisation ▪ Downhill-simplex
- Repeat until convergences