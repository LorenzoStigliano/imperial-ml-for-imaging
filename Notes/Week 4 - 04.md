### Convolutional Neural Networks for Image Segmentation

Segmentation Via Dense Classification
- Very difficult with high resolution class
- So we need to learn features to learn dense classification
- We work with 3D images 
![[Screenshot 2023-02-03 at 18.58.38.png]]
- We look at the image patch for the central pixel and make a binary decision
- At training time we extract several patches to determine what each is each.
- At testing we use sliding window approach -> very inefficient 
- When implementing linear layers we need to predefine the input size
- So we can replace fully connected layers with convolutional layers, we have to match the kernels with the size of the FM![[Screenshot 2023-02-03 at 19.05.21.png]]
- In the example we have 2 (2x2 kernels 3 channels)![[Screenshot 2023-02-03 at 19.09.18.png]]
- We can now go beyond classification we know produce a feature map for each of the digits we have high responses in different areas ![[Screenshot 2023-02-03 at 19.09.41.png]]
![[Screenshot 2023-02-03 at 19.10.41.png]]
- We can see that there is a high response in the top right, which could be used to perhaps detect areas

#### Encoder Decoder Networks
![[Screenshot 2023-02-03 at 19.15.55.png]]
- Go down to nxn and then sample back up to the original shape of the image
- Long et al : they learn to upsample low level images

U-Net
![[Screenshot 2023-02-03 at 19.17.46.png]]
- Most common paper for image segmentation 
- Idea sample down and then back up for a full resolution of the input
- The grey lines are skip connections - they have been showed to help with accuracy and they share information across

#### Upsampling
![[Screenshot 2023-02-03 at 19.20.16.png]]
- You learn these weights 
- Different techniques to do transpose convolutions![[Screenshot 2023-02-03 at 19.20.53.png]]
We also need to consider:
- ![[Screenshot 2023-02-03 at 19.29.27.png]]
- We prefer valid convolutions![[Screenshot 2023-02-03 at 19.29.53.png]]

Going Deeper 
- Deeper networks can represent more complex functions 
- Just adding more layers is inefficient (too many parameters) 
- Idea: Use only layers with small kernels Simonyan et al. 2014![[Screenshot 2023-02-03 at 19.33.05.png]]

Multi-Scale Processing
- How can we make the network to “see” more context 
- Idea: Add more pathways which process downsampled images![[Screenshot 2023-02-03 at 19.34.41.png]]
- Additional spatial information enhances network’s localization capabilities![[Screenshot 2023-02-03 at 19.35.18.png]]
