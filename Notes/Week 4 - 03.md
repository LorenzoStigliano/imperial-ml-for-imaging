### Segmentation Algorithms and Techniques

#### Intensity-based segmentation

##### Thresholding

Simple Thresholding 
- Select a threshold on the intensity range
UL Thresholding 
- Select a lower and upper threshold

- Advantages 
	- simple 
	- fast 
- Disadvantages 
	- regions must be homogeneous and distinct 
	- difficulty in finding consistent thresholds across images 
	- leakages, isolated pixels and ‘rough’ boundaries likely

##### Region Growing

- Start from (user selected) seed point(s), and grow a region according to an intensity threshold

- Advantages 
	- relatively fast 
	- yields connected region (from a seed point) 
- Disadvantages 
	- regions must be homogeneous 
	- leakages and ‘rough’ boundaries likely 
	- requires (user) input for seed points

##### Graph Cuts
- Segmentation based on max-flow/min-cut algorithm
- We define a graph for each pixel in the image, each node has 4 neighbours
- Define 2 new nodes s and t and then goal is to find the nodes that are connected to s and t nodes 
- We use brush strokes to define what the foreground and the background are of interest 
- Extension: multi-label graph cuts 

Advantages 
- accurate
- reasonably efficient, interactive 
Disadvantages 
- semi-automatic, requires user input 
- difficult to select tuning parameters

##### Atlas-Based Segmentation
What is an atlas?
- An map or chart of the anatomy 
- Atlases usually have 
	- geometric information about points, curves or surfaces, or 
	- label information about voxels (anatomical regions or function)
- Atlases are usually constructed from example data 
	- single subjects 
	- populations of subjects, e.g. by averaging to produce probabilistic atlases

Segmentation using Registration![[Screenshot 2023-02-03 at 18.22.31.png]]
![[Screenshot 2023-02-03 at 18.23.01.png]]
 ![[Screenshot 2023-02-03 at 18.24.46.png]]
Label Fusion
- Simple Majority Voting to determine the new label
Effect of Number of Atlases
- Initially helps and then levels off

Advantages 
- robust and accurate (like ensembles) 
- yields plausible segmentations 
- fully automatic 

Disadvantages 
- computationally expensive 
- cannot deal well with abnormalities 
- not suitable for tumour segmentation

##### Random Forests

- Very popular for tumour segmentation
- We use a multiple channel input and then we segment the tumour tissues 
- This is difficult to create an atlas for tumours since all of them are different

Training: Growing the Trees
- We don't know what the decision is at the start
- At each node we find a feature that separate the training examples further and further until we cluster the examples into subgroups which are consistent![[Screenshot 2023-02-03 at 18.31.15.png]]

Testing: Traversing the Trees
- We get the feature and then determine where to go based on this

We build many of these trees to increase the predictive power.

Advantages 
- ensemble classifiers are robust and accurate 
- computationally efficient 
- fully automatic 
Disadvantages 
- shallow model, no hierarchical features 
- no guarantees on connectedness