- Find image regions that are likely contain objects (e.g. interesting image areas) 
- Must be fast to run, e.g. selective search gives around 2000 region proposals in a few seconds
- Selective Search for Object Recognition - popular method for selective search
	- First segments image using super pixels
	- Then groups neighbouring super pixels together and across different scales
	- We use features within a region to decide if it contains an object of interest

## (Slow) R-CNN
![[Screenshot 2023-02-20 at 14.49.40.png]]
- 2014 paper
- 1st uses a region of interest proposal method
- 2 for each region we wrap them 
- then we pass through them a ConvNet to classification each region
- And then we also apply bounding box regressors 

Problems:
- Ad-hoc training objectives
	- Fine-tune network with softmax classifier (log loss) 
	- Train post-hoc linear SVMs (hinge loss) 
	- Train post-hoc bounding-box regressors (squared loss) 
- Training is slow (84h), takes a lot of disk space
- Inference (detection) is slow 
	- 47s / image with VGG16

## Spatial Pyramid Pooling (SPP-net)

- Fixes the slow inference problem![[Screenshot 2023-02-20 at 14.53.30.png]]
- We use the whole image through ConvNet and then we do the regions of interest on the feature maps produced by the ConvNet![[Screenshot 2023-02-20 at 14.54.32.png]]
- Spatial Pyramid Pooling (SPP) layer ![[Screenshot 2023-02-20 at 14.55.22.png]]
- Inherits the rest of R-CNN’s “problems” 
	- Ad-hoc training objectives 
	- Training is slow (though faster), takes a lot of disk space
- Introduces a new problem: 
	- cannot update parameters below SPP layer during training![[Screenshot 2023-02-20 at 14.56.44.png]]

