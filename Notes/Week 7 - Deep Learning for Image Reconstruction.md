Medical Imaging: 
- X-ray computed tomography (CT)
- We collect a series of slices through the human anatomy
- Then we can reconstruct a 3D image of the anatomy
- CT imaging ![[Screenshot 2023-02-20 at 14.13.17.png]]
	- high contrast 
	- high spatial resolution 
	- fast acquisition
	- but ionising radiation
![[Screenshot 2023-02-20 at 14.13.37.png]]
- We can convert the forward problem with a radon transform.
- In practice we have less radiation for the patient as a result we have less resolution sinograms which means we cannot do an inverse radon transform![[Screenshot 2023-02-20 at 14.15.13.png]]

- Magnetic Resonance (MR) - also benefits from image reconstruction
- MR imaging: 
	- high contrast
	- high spatial resolution 
	- no ionising radiation
	- visualize dynamic processes
- but slow acquisition process 
- Slow acquisition is 
	- ok for static objects (e.g. brain, bones, etc) 
	- problematic for moving objects (e.g. heart, liver, fetus) 
- Options for MR acquisition: 
	- real-time MR: fast, but 2D and relatively poor image quality 
	- gated MRI fine for period motion, e.g. respiration or cardiac motion but requires gating (ECG or navigators) leading to long acquisition times (30-90 min).
- MRI acquisition is performed in k-space by sequentially traversing sampling trajectories![[Screenshot 2023-02-20 at 14.17.02.png]]
- We measure all the different frequencies and then we apply Inverse transform, it is an algebraic transform ![[Screenshot 2023-02-20 at 14.18.02.png]]
- We would like to get less data so we can acquire less frequencies so the image aquisicion is faster, but the image quality is lower

## Deep learning for image reconstruction
![[Screenshot 2023-02-20 at 14.19.24.png]]
- Get the reconstructed image and then use a deep learning model to reconstruct the image with higher resolution 
![[Screenshot 2023-02-20 at 14.20.07.png]]
- We can also use an unrolling optimisation approach 
- Green layers ensure the image is consistent with the measurement we have made
- Each cascade is one step of optimisation problem![[Screenshot 2023-02-20 at 14.22.10.png]]
- 

