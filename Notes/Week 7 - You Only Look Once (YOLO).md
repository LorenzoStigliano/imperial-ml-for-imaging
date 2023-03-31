- Need more speed for self driving cars decision making  ![[Screenshot 2023-02-20 at 15.23.36.png]]
- Avoid region proposal step 
- We run whole image and then we find object thresholds
- Image is only passed once

Steps:
1. Split the image into a grid 
2. Each cell predicts boxes and confidence P(object)
3. Force grid cell to make 2 bounding box predictions, we given them predictions and confidence 
4. Each cell also predicts a class probability - coarse segmentation of the image, probability of P(x|object)
5. Combine the box and class predictions 
6. Preform NMS (non maximum suppression)and threshold detections

How to train?
![[Screenshot 2023-02-20 at 15.29.01.png]]
- For a fixed image it will always produce a fixed tensor size
- Easily trained in end to end fashion![[Screenshot 2023-02-20 at 15.30.43.png]]

During training:
1. Match an example to the right cell, with a ground truth bounding box
2. Adjust the cells prediction class
3. The cell will make 2 prediction, adjust it, increase the confidence
4. Decrease the confidence of other boxes, to 0
5. Do for all the cells - Some cells don’t have any ground truth detections
	1. Decrease the confidence of these boxes both
	2. We don't adjust the class probabilities on the cells with no truth of the cell
![[Screenshot 2023-02-20 at 15.33.46.png]]
