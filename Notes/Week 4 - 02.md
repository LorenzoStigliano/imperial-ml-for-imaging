### Evaluating Image Segmentation

#### Ground Truth
- Reference or standard against a method can be compared, e.g. the optimal transformation, or a true segmentation boundary 
- In practice, it is not available! 
- Instead, one makes one up

#### Gold Standard
- Expert (often referred to as gold standard) - Manual segmentation by human observer
- Disadvantage 
	- Requires training and is tedious and time-consuming 
	- Intra-observer variability (disagreement between same observer on different occasions)
	- Inter-observer variability (disagreement between observers) 
- Remedy 
	- Human observer can perform segmentation repeatedly
	- A number of experts can perform segmentations 
	- Agreement or disagreement can be quantified

#### How to Assess Performance?

Precision 
- is a description of random errors, a measure of statistical variability. 
- the repeatability, or reproducibility of the measurement 
Accuracy has two definitions
- More commonly, it is a description of systematic errors, a measure of statistical bias; as these cause a difference between a result and a "true" value, ISO calls this trueness. 
Robustness 
- refers to the degradation in performance with respect to varying noise levels or other imaging artefacts![[Screenshot 2023-02-03 at 17.28.03.png]]

#### Performance Measures
- Measure performance of an automated method in terms of agreement of its result with a reference gold standard![[Screenshot 2023-02-03 at 17.28.49.png]]![[Screenshot 2023-02-03 at 17.29.06.png]]

#### Confusion Matrix
![[Screenshot 2023-02-03 at 17.29.58.png]]
![[Screenshot 2023-02-03 at 17.30.28.png]]
- We are not interested in accuracy and specificity, this is because if we have a very high resolution pixel image then specificity will be relatively low since we do not make many mistakes away from the segment of interest.
- Precision and Recall is what we focus on, Recall high then we have more FP and then we get all of what is intended.
![[Screenshot 2023-02-03 at 17.30.43.png]]
#### Overlap
![[Screenshot 2023-02-03 at 17.31.03.png]]
#### Dice Similarity Coefficient
- Most widely used measure for evaluating segmentation 
- Assume 𝐴 is the reference, and 𝐵 the prediction![[Screenshot 2023-02-03 at 17.31.39.png]]
- Limitations of DSC
	- Not deformation invariant![[Screenshot 2023-02-03 at 17.32.04.png]]

#### Other Measures 
- Volume similarity ignores the location is only interested in the area/volume
![[Screenshot 2023-02-03 at 17.32.27.png]]

Surface Distance
- Tells you on average how far away you're from the other boundary
- We can turn the contours to distance maps for every pixel how far away it is from a countor
- Then we can look at pixels within a certain range from countor
- Swap the countors and then: Sum up distances along pixels on the boundaries of one contour overlaid on the distance map of the other![[Screenshot 2023-02-03 at 17.46.20.png]]
