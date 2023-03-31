### Neural Networks

![[Screenshot 2023-01-24 at 10.49.58.png]]
- Training a perceptron means to iteratively updating the weights associated with each of its inputs 
- This allows to progressively approximate the underlying relationship in the given training dataset 
- Once properly trained, it can be used to classify entirely new samples
![[Screenshot 2023-01-24 at 10.50.57.png]]
![[Screenshot 2023-01-24 at 10.53.54.png]]
![[Screenshot 2023-01-24 at 10.54.08.png]]

### Learning with NN

NN with K class outputs
![[Screenshot 2023-01-24 at 11.10.13.png]]
![[Screenshot 2023-01-24 at 11.09.15.png]]
The Loss function used for training
![[Screenshot 2023-01-24 at 11.09.37.png]]
![[Screenshot 2023-01-24 at 11.13.11.png]]

#### Computational Graphs

- These are the same as the ones seen in MML, see MML notes for more explanation. Example:
![[Screenshot 2023-01-24 at 11.19.44.png]]
![[Screenshot 2023-01-24 at 11.16.18.png]]
#### Backpropagation main idea
![[Screenshot 2023-01-24 at 11.17.10.png]]

### Activation functions and Optimisation

- Each node in the neural network passes its computation through activation function
- Typically, all nodes in the neural network have the same activation function for each class of neurons but – activation functions for hidden nodes and output nodes can be different

Types:
1. ![[Screenshot 2023-01-24 at 11.30.31.png]]
2. The derivative will be 0 for large values of $x$ and so cannot compute back-propagation step![[Screenshot 2023-01-24 at 11.30.40.png]] 
3. ![[Screenshot 2023-01-24 at 11.30.51.png]]
4. ![[Screenshot 2023-01-24 at 11.30.59.png]] 
5. ![[Screenshot 2023-01-24 at 11.31.08.png]]
6. ![[Screenshot 2023-01-24 at 11.31.29.png]]

#### Stochastic Gradient Descent

![[Screenshot 2023-01-24 at 11.37.28.png]]
![[Screenshot 2023-01-24 at 11.38.00.png]]
![[Screenshot 2023-01-24 at 11.38.33.png]]
![[Screenshot 2023-01-24 at 11.39.36.png]]

### Tips and Tricks for Training NN

- But: neural networks can have vast number of parameters 
	- Modern (convolutional) NN architectures can have 100M+ parameters
	- There is no such thing as having enough training data 
- Acquiring more training data is 
	- Costly and time-consuming 
	- Labelling data is even more difficult

#### Techniques

1. Data augmentation
	- Generate new training instances from existing ones – Artificially boosting the size of the training set
	- Generate new instances, e.g. 
		- Geometric transformations such as rotation, shift, resizing, flip, etc.
		- Pixel transformations such as brightness or color changes 
		- Noise
	- Use domain specific information for data augmentation
2. Regularisation
	- Early stopping: 
		- Interrupt training when its performance on the validation set starts dropping![[Screenshot 2023-01-24 at 11.44.24.png]]
		- Easy to implement: Requires during training to evaluate the model on the validation set at regular intervals (say every 50 steps) and save snapshot result for next comparison
	- $L^2$ Regularisation: 
		- Also known as ridge regression or Tikhonov regularisation
		- Update cost function by adding another term (regularization term):![[Screenshot 2023-01-24 at 11.45.31.png]]
		- New optimum in red point
	- $L^1$ Regularisation :
		- Lasso regression 
		- Update cost function by adding another term (regularization term):![[Screenshot 2023-01-24 at 11.46.49.png]]
	- Max-norm Regularisation: 
		- ![[Screenshot 2023-01-24 at 11.48.07.png]]
	- Dropout:
		- At every training step, every neuron (input or hidden) has a probability p of being temporarily “dropped out”:![[Screenshot 2023-01-24 at 11.49.06.png]]
		- Prevents overfitting to one neuron 
3. Weight initialization
	- ![[Screenshot 2023-01-24 at 11.50.28.png]]
4. Batch normalisation
	- Simple trick to enable a wider ranger of hyperparameters for training
	- Simplifies training of deep networks
	- We can normalize the inputs
	- We can also normalize the output values at each layer![[Screenshot 2023-01-24 at 11.51.52.png]]
	- Zero centred and standard variance ![[Screenshot 2023-01-24 at 11.52.13.png]]

