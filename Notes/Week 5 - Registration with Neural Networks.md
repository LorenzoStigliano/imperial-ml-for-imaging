
## Supervised Learning Approaches 

- FlowNet: Learning Optical Flow with Convolutional Networks
	- FlowNetSimple:
		- Input 6 channel RGB image (2 images)
		- Then several convolutional layers 
		- Optical flow image field ![[Screenshot 2023-02-07 at 16.06.45.png]]
	- FlowNetCorr:
		- Operating with two different convolutional layers and then join together with corr map![[Screenshot 2023-02-07 at 16.07.49.png]]
	- They do upsampling with transpose convolution at each convolution and they tried to predict the flow field in intermittent layers and added these to further help the output![[Screenshot 2023-02-07 at 16.09.21.png]]
- Problem: what data do we train on? This was trained on flying chair and then was able to generalise well 
- FlowNet 2.0: Evolution of Optical Flow Estimation with Deep Networks
	- Problems in 1.0
		- Large displacements are hard to estimate them,  capture ranges![[Screenshot 2023-02-07 at 16.11.26.png]]
		- The blue network tries to correct the residuals in the first errors and so on, they are trying to correct the errors
		- For small displacements new architecture![[Screenshot 2023-02-07 at 16.12.46.png]]
		- Then you fuse everything together![[Screenshot 2023-02-07 at 16.13.05.png]]
- Other works: Optical Flow with Semantic Segmentation and Localized Layers
	- You can combine object segmentation with more information can give us better estimation on optical flow
- Nonrigid Image Registration Using Multi-scale 3D CNNs Medical imaging
	- ![[Screenshot 2023-02-07 at 16.15.35.png]]
	- Higher and lower resolution split for high and low level features
	- They use synthetic deformations, with a ground truth transformation
	- How does one do a synthetic deformation?
## Unsupervised Learning Approaches

- Spatial Transformer Networks
	- NN component that you can plugin anywhere in a NN, is a small NN itself
	- Then they produce a vector parameters of a transformation $T$
	- As a result it learns a transformation during training before classification![[Screenshot 2023-02-07 at 16.19.56.png]]
	- The transform learnt to normalise the digits and straighten the digits!
- Now we can use this in image registration
- End-to-End Unsupervised Deformable Image Registration with a CNN![[Screenshot 2023-02-07 at 16.21.39.png]]
	- We use intensity based registration, we want to make the two images look the same
	- Then we predict transformation control points and then we get a warped image
	- Then we see if it is the same as the fixed image 
- An Unsupervised Learning Model for Deformable Image Registration![[Screenshot 2023-02-07 at 16.24.05.png]]
	- They used it with variant of networks, for example a U net
	- They replicate a dense registration field
## Other Learning Approaches 

- VoxelMorph: A Learning Framework for Deformable Image Registration
	- You can use auxiliary information such as segmentation and see how well they agree with one another after a transformation![[Screenshot 2023-02-07 at 16.26.19.png]]
	- Only needed at training time 
- Learning Conditional Deformable Templates
	- Learning different templates / atlases 
	- We have a generative model, that learns a template ![[Screenshot 2023-02-07 at 16.28.31.png]]
	- In this case a is the age and then we can get different templates and see the difference in the anatomy of the brain 

## Template Registration 

- TeTrIS: Template Transformer Networks for Image Segmentation
- Idea: learn how to deform an input template given an input image so we can learn how to warp the map so we can get good segmentations 
- And so with missing data we can get a transformation that best gets the output ![[Screenshot 2023-02-07 at 16.42.43.png]]![[Screenshot 2023-02-07 at 16.39.07.png]]

## Structure-Guided Registration
- ISTNs: Image-and-Spatial Transformer Networks
	- Idea: we incorporate more information at training stage and then can understand what to register ![[Screenshot 2023-02-07 at 16.41.09.png]]
	- Here we are extracting FM from the moving image and then learns a transforms on new images that come out of an image to image transformer network 
	- ITN - produces an explicit output which is optimised for registration combining segmentation techniques 
	- Once you do this, you can run iterative representation so you can produce better accuracy on registration 

## Atlas-ISTNs
- Joint Segmentation, Registration and Atlas Construction
- Taking the above one step further ![[Screenshot 2023-02-07 at 16.46.21.png]]
- Learn at the same time an atlas which gets better over time 
- And map an atlas to an image 
- Given a new input image we want to segment 
- We are also registering to an atlas so we can do an population wide analysis