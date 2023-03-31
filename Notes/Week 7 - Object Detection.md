- Semantic Segmentation - what does each pixel belong to
- Localisation and classification
- ![[Screenshot 2023-02-20 at 14.35.53.png]]![[Screenshot 2023-02-20 at 14.36.52.png]]
- We are trying to detect multiple objects in the image, and we have segmented it correctly
- ![[Screenshot 2023-02-20 at 14.38.29.png]]
- Problem: how do we formulate this as a regression problem? Depending on the image, we will need different number of outputs but NN are fixed!![[Screenshot 2023-02-20 at 14.40.36.png]]

Methods to overcome this problem:
1. Object Detection as Classification: Sliding Window
	- Apply CNN to every possible crops of the image, CNN classifies each crop a object or background
	- Problem too slow
	- We would like to do this in real time with continuous images
2. Object Detection using Region Proposals
	- Find image regions that are likely contain objects (e.g. interesting image areas) 
	- Must be fast to run, e.g. selective search gives around 2000 region proposals in a few seconds