- Upsample low-resolution (LR) image to high-resolution (HR or SR) image
- Forward model (going from high- to low-resolution) is straightforward and involves some image degradation followed by downsampling
- Inverse model: e.g. interpolation-based models

## Super-resolution framework: Post-upsampling super-resolution

- Directly upsamples LR image into SR
- Requires learnable upsampling layers
![[Screenshot 2023-02-20 at 10.45.45.png]]
- Advantages: 
	- Fast and low memory requirements 
- Disadvantages: 
	- Network has to learn entire upsampling pipeline 
	- Network typically limited to a specific up-sampling factor

## Super-resolution framework: Pre-upsampling super-resolution

Two stage process: 
1. First use traditional upsampling algorithm (e.g. linear interpolation) to obtain SR images 
2. Then refining upsampled using a deep neural network (usually a CNN)
![[Screenshot 2023-02-20 at 10.47.35.png]]
- Advantages:
	- Upsampling operation is performed using interpolation, then correct smaller details
	- Can be applied to a range of upscaling factors and image sizes 
- Disadvantages: 
	- Operates on SR image, thus requires more computation and memory

## Super-resolution framework: Progressive upsampling super-resolution

- Multi-stage process: 
	- Use a cascade of CNNs to progressively reconstruct higher-resolution images.
	- At each stage, the images are upsampled to higher resolution and refined by CNNs
![[Screenshot 2023-02-20 at 10.48.15.png]]
- Advantages: 
	- Decomposes complex task into simple tasks 
	- Reasonable efficiency 
- Disadvantages: 
	- Sometimes difficult to train very deep models

## Super-resolution framework: Iterative up-and-down sampling super-resolution

- Approach: 
	- Alternate between upsampling and downsampling (back-projection) operations
	- Mutually connected up- and down-sampling stages
	![[Screenshot 2023-02-20 at 10.49.26.png]]
Advantages: 
- Has shown superior performance as it allows error feedback 
- Easier training of deep networks

## How to implement upsampling?

- Traditional interpolation-based upsampling (NN, bi-linear) can be implemented as a convolutional layer with fixed weights:
- Or using learnable weights as transpose convolution

## Loss functions for super-resolution
![[Screenshot 2023-02-20 at 10.51.01.png]]
![[Screenshot 2023-02-20 at 10.52.31.png]]
![[Screenshot 2023-02-20 at 14.07.16.png]]
![[Screenshot 2023-02-20 at 14.08.08.png]]
