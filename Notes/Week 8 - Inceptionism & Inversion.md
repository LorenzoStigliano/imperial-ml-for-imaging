### DeepDream / Inceptionism

- Attempt to understand the inner workings of the network 
- Optimize with respect to image
- Idea
	- Arbitrary image or noise as input 
	- Instead of adjusting network parameters, tweak image towards high “X” where “X” can be 
		- Neuron/Activation map/Layer 
		- Logits/Class probability 
	- Search for images that are “interesting” 
	- Different layers enhance different features
- Find an image $x$ such that the activation $\phi_n(x)$ at layer $n$ is high![[Screenshot 2023-02-25 at 14.17.51.png]]
- Algorithm 
	- Forward propagate to layer $n$, the current estimation of image $x$
	- No minimization of loss. Instead maximize L2 norm of activations of a particular NN layer 
	- Backpropagate to input layer

## Inversion
-  Inversion attempts to construct an image from a layer activation $\hat{y}$![[Screenshot 2023-02-25 at 14.20.38.png]]
- We get the image that produces the activation $\hat{y}$
- Deep networks as encoders![[Screenshot 2023-02-25 at 14.22.11.png]]![[Screenshot 2023-02-25 at 14.24.20.png]]![[Screenshot 2023-02-25 at 14.25.03.png]]
- Idea is we move to the space of the pre image, we iteratively move to this space
- Natural pre-images by adding regularisation term ![[Screenshot 2023-02-25 at 14.26.20.png]]
- Different ways to achieve pseudo-natural pre-images![[Screenshot 2023-02-25 at 14.28.08.png]]

