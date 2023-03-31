- Satellite Imaging to see differences between images
	- Align images and then see the differences
- Panoramic image stitching - want to find spatial correspondances  
- Optical flow registration 
	- There are many datasets, Middlebury and KITTI vision benchmark suite
	- Sintel based on a movie
- Estimating motion in health care
	- cardiac motion and thus we can see health
	- respiratory motion 
	- See how effective an intervention is
	- Multi modal image fusion, joining together the images from different scans together and thus get more information
- Intra-subject registration
	- Contrasted and non-contrasted images and thus we help see the difference more accurately to compensate the difference and this we can localise better the legion
- Inter-subject registration
	- Atlas construction - to see the average pixel
	- 20 random subjects from ‘normal CT’ database
	- One selected as 'target'
	- Iterative registration
		1. Rigid - to roughly align the brains
		2. Affine - to take into account differences between differences in patients
		3. Nonrigid - better alignment