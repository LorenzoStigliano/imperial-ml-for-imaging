### Feature Extraction

Classical machine learning pipeline in CV, Images to features to ML model.
![[Screenshot 2023-01-23 at 15.19.59.png]]

#### What is $x$? In other words what form should be $f(I)$ ?
Features should be:
- Distinctive and discriminative 
- Local (to enable establishing correspondences) 
- Invariant to viewpoint changes or transformations (translations/rotations)
- Invariant to illumination changes 
- Efficient to compute
- Robust to noise and blurring 
- Hierarchical to allow abstraction 

#### Different Techniques
1. Intensity 
	- Pixel-level : non discriminative, localised but single pattern does not represent any local patterns
	- Patch-level: more discriminative, not rotation invariant, semi-localised, we can convolve them to extract more features, such as edges, corners, gradients, ....
	- We can use multiple filters to describe a patch as a column vector.![[Screenshot 2023-01-23 at 15.25.13.png]]
	- Image-level: Discriminative, Not necessarily rotation invariant, Not localised. We slide a filter across an image to get a feature map.![[Screenshot 2023-01-23 at 15.25.40.png]]
	- We can also use a histogram level, for each pixel intensity to describe an image.
2. SIFT
	- One of the most popular feature descriptors (over 60000+ citations) 
	- Robust to viewpoint, illumination changes and noise 
	- Transforms image into a "large collection of local feature vectors” • Four stages: 
		1. Scale-space Extrema Detection ![[Screenshot 2023-01-23 at 15.28.26.png]]
		2. Keypoint Localisation ![[Screenshot 2023-01-23 at 15.28.47.png]]
		3. Orientation Assignment ![[Screenshot 2023-01-23 at 15.29.08.png]]
		4. Keypoint Descriptor ![[Screenshot 2023-01-23 at 15.29.24.png]]
3. HoG - Histogram of Gradients
	1.  Preprocessing: Crop and resize image
	2. Calculate Gradient Images
	3. Calculate Histogram of gradients in 8x8 cells - we can get gradient magnitude and directions. So for each direction we add a count with strength of the magnitude.
	4. 16x16 Block Normalization
	5. Calculate the HoG feature vector
4. SURF - Speeded-Up Robust Features
	- ![[Screenshot 2023-01-23 at 15.36.38.png]]
	- ![[Screenshot 2023-01-23 at 15.36.52.png]]
5. Binary Robust Independent Elementary Features (BRIEF)
	- ![[Screenshot 2023-01-23 at 15.38.02.png]]
	- ![[Screenshot 2023-01-23 at 15.38.19.png]]
7. Local binary patterns (LBP)
	- Contrast insensitive 
	- Fast to compute
	- Small neighbourhood patch, compare to the neighbours, if center intensity is greater than pixel 1 or other wise 0, then to we get a bit-string, and then get a number which describes the pixel intensity in that patch. 
8. Haar features 
	- Inspired by wavelet analysis 
	- Can be thought if convolution operators![[Screenshot 2023-01-23 at 15.41.22.png]]![[Screenshot 2023-01-23 at 15.41.45.png]]![[Screenshot 2023-01-23 at 15.42.21.png]]
	- This is the main idea, we sum the intensities then we can do a sum over the box.