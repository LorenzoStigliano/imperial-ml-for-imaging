### Convolutional Neural Networks (CNN)

#### Introduction [[Deep Learning/Notes/Week 2]]
- Deep learning pipeline in Computer Vision
![[Screenshot 2023-01-24 at 12.18.24.png]]
- Problem with NN for image classification
	- Each neuron detects a different pattern. 
	- Too many weights for each neuron/pattern. 
		- Example: 512 x 512 image = more than 260,000 weights/pattern.
- Locally connected networks
	- Each neuron detects a different pattern.![[Screenshot 2023-01-24 at 12.23.03.png]]
	- Kernel of a neuron: Spatially limited connections  
		- Example: If kernel = 10x10, 100 weights/pattern.Ea ch neuron only detects a pattern at a certain location.
- The same feature may appear anywhere in the image
	- Locally connected networks with **shared weights**![[Screenshot 2023-01-24 at 12.23.58.png]]![[Screenshot 2023-01-24 at 12.24.33.png]]
- Convolutional Layer: ![[Screenshot 2023-01-24 at 12.26.31.png]]
	- Multiple Feature Maps - Detect multiple features per layer. 
	- A layer can be perceived as a multi-channel image (similar to RGB channels)
	- Deeper layers process FMs (channels) of previous layer. 
	- Combine previous features to extract more complex representations

#### Convolutional layers
- What is the size of the feature map?
	- ![[Screenshot 2023-01-24 at 12.29.34.png]]
	- Note if we have a filter of shape 5x5xN of Channels then we reduce the output to 1 channel.
	- If we have a 5x5x1 then we apply this filter to each channel so we have the same number of outputs
	- If we apply N number of Channels filters of shape 5x5xN then we get N number of Channels.
	- ![[Screenshot 2023-01-24 at 12.44.48.png]]
	- ![[Screenshot 2023-01-24 at 12.45.04.png]]
	- ![[Screenshot 2023-01-24 at 12.45.14.png]]
	- As we have seen we can learn multiple kernels (or feature maps) at the same time by stacking & output feature maps![[Screenshot 2023-01-24 at 12.46.00.png]]
	- However, the input to a convolutional layer may also have ' input channels, e.g. for a RGB image ' = 3. ![[Screenshot 2023-01-24 at 12.46.37.png]]![[Screenshot 2023-01-24 at 12.47.02.png]]
- Downsampling via Pooling
	- Reduce size (memory) of deeper layers 
	- Invariance to small translations 
	- Contraction forces network to learn high-level features![[Screenshot 2023-01-24 at 12.51.04.png]]
	- Convention stride = kernel size, so there are no overlapping regions
	- We can use max or mean pooling
- Upsampling
	- Deconvolution / transposed convolution: Learn to upsample![[Screenshot 2023-01-24 at 12.53.09.png]]
	- Fill with 0s + blur with kernel, we can learn the kernel

#### Architectures
1. LeNet [[Imperial/Spring Term/Deep Learning/Notes/Week 3 - 03]]  
	- First architecture![[Screenshot 2023-01-24 at 12.55.22.png]]
	- Uses convolution layers, pooling layers and fully connected layers for classification.
	- 60k parameters![[Screenshot 2023-01-24 at 12.56.41.png]]
2. AlexNet [[Imperial/Spring Term/Deep Learning/Notes/Week 3 - 04]]  
	- Winner of the the ImageNet 2012 Challenge![[Screenshot 2023-01-24 at 12.59.23.png]]
	- Max-pooling and ReLU 
	- Stacked convolutional layers directly on top of each other, instead of stacking a pooling layer on top of each convolutional layer
	- Dropout regularization 
	- Uses data augmentation (random transformation, random intensity variation) 
	- Trained on two GPUs for a week
	- 60M parameters
3. VGGNet [[Imperial/Spring Term/Deep Learning/Notes/Week 3 - 05]]  
	- Very Deep Convolutional Networks for Large-Scale Visual Recognition![[Screenshot 2023-01-24 at 13.01.16.png]]
	- Rigorous evaluation of networks of increasing depth, up to 16-19 weight layers 
	- Very small 3×3 filters in all convolutional layers (the convolution stride is set to 1). 
	- Trained on 4 GPUs for 2–3 weeks

Changing fully connected layers to convolutional layers, since this would reduce the number of parameters we need to learn.![[Screenshot 2023-01-24 at 13.04.35.png]]
- Size of receptive field remains the same! 
- Each prediction is only influenced by its own receptive field. NOT the whole input!

#### Advanced CNN Architectures

- Network in network![[Screenshot 2023-01-24 at 13.07.12.png]]
- Introduce fully connected layers between convolution layers, we can represent these fully convolutions by 1x1 convolutions.![[Screenshot 2023-01-24 at 13.08.21.png]]
- 1x1xNumber of channels, left image. Integrates information across the channels.
- Useful to create deep networks without parameters to explode.

GoogLeNet![[Screenshot 2023-01-24 at 13.10.55.png]]
- 22 layers + global average pooling as final layer
- Auxiliary classifiers (only used during training) side branches
- Inception modules main body of the network

#### Inception modules
- Makes extensive use of 1 x 1 convolutions![[Screenshot 2023-01-24 at 13.12.41.png]]
- Reduces number of parameters but same output
- (14x14x16) is the shape of the image, 16 is the channels, and the size of the kernel is 1x1x480 (channel)
- We allow the network to *learn* which filter size is the best.![[Screenshot 2023-01-24 at 13.14.55.png]]
- **We use the 1x1 convolutions before to reduce the cost** 
- With increasing depth features get increasingly abstract
- Inception networks, there are several variants to reduce the number of variants, we can use different strides,...![[Screenshot 2023-01-24 at 13.18.18.png]]
- As we go deeper we see an improvement in the imagenet challenge![[Screenshot 2023-01-24 at 13.19.46.png]]

#### Is learning better networks as simple as stacking more layers?
- We can see that it could be the case that deeper networks preform worse ![[Screenshot 2023-01-24 at 13.20.41.png]]
- They should have the same representational power as a shallow network![[Screenshot 2023-01-24 at 13.21.49.png]]
- The problems come from the difficulty in optimising these networks

#### ResNet helps this problem
![[Screenshot 2023-01-24 at 13.22.48.png]]
![[Screenshot 2023-01-24 at 13.23.31.png]]
- The difference between the input and the output
- We can see lower error when using ResNet:![[Screenshot 2023-01-24 at 13.24.03.png]]
- We can see that we get better performance when networks preform more computations than smaller ones. More large and deep better accuracy.