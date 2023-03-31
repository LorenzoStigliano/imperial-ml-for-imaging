## Fast R-CNN

- Fast test-time, like SPP-net 
- One network, trained in one stage 
- Higher mean average precision than slow R-CNN and SPP-net![[Screenshot 2023-02-20 at 15.10.05.png]]
- Rol Pooling:![[Screenshot 2023-02-20 at 15.10.42.png]]
- All together![[Screenshot 2023-02-20 at 15.11.21.png]]
- For training end-to-end fashion![[Screenshot 2023-02-20 at 15.12.31.png]]

## Faster R-CNN

- Make CNN do proposals! 
- Insert Region Proposal Network (RPN) to predict proposals from features 
- Jointly train with 4 losses: 
	1. RPN classify object / not object 
	2. RPN regress box coordinates 
	3. Final classification score (object classes) 
	4. Final box coordinates

- Good speed • Good accuracy • Intuitive • Easy to use

## Mask R-CNN

- Mask R-CNN = Faster R-CNN with FCN on RoIs, we label each pixel of the image
- This third branch is a fully convolutional network (FCN) that takes the proposed regions from the RPN and generates a mask for each object. The FCN generates a binary mask for each pixel in the region indicating whether the pixel belongs to the object or not.![[Screenshot 2023-02-20 at 15.15.58.png]]
- Cls = classification 