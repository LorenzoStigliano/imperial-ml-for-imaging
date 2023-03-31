
## Images 
- $d$-dimensional arrays with scalar/vector values
- Meta information - we also get this extra information, very important for medical imaging to understand what a pixel represents, where we are measuring from, typically stored in header information
	- Scale: element spacing (e.g. in mm)
	- Orientation: directions of main axes 
	- Position: image origin

## Medical Image Registration
- Establish spatial correspondences between images![[Screenshot 2023-02-07 at 13.57.08.png]]
- We want to find correspondences between pairs of images
- Not always a linear mapping we need to find this transformation

## Coordinates Systems

- Image coordinate system 
	- Array which defines the position of the pixel values
	- we also have a mapping from the pixels to the locations in the physical world and are discrete
	- We also have the image coordinate system which define how to read the pixels
- World coordinate system 
	- Images are taken with respect to a world coordinate system, arbitrary define but fixed![[Screenshot 2023-02-07 at 14.02.32.png]]
- Image to world - In homogenous coordinates![[Screenshot 2023-02-07 at 14.03.06.png]]
	- $s_x$ and $s_y$ is the scaling of the pixel coordinates
	- $d_{ii}$ is the rotation matrix, the direction vectors
	- red is the shift translation 

We typically register in world coordinates:
- This is because we want to relate images from different coordinate systems![[Screenshot 2023-02-07 at 14.06.41.png]] ![[Screenshot 2023-02-07 at 14.06.51.png]]
- ![[Screenshot 2023-02-07 at 14.07.16.png]]
- We need to find the transformation from B to A in world coordinates
- Note the two outer transformations are given to us 

## Transformation Models
 ![[Screenshot 2023-02-07 at 14.09.39.png]]
![[Screenshot 2023-02-07 at 14.23.50.png]]
- Sheering is scaling plus rotation
- We can put all of them together to get one matrix that represents all the transformations
![[Screenshot 2023-02-07 at 14.24.46.png]]

### Free-Form Deformations
- Low-dimensional deformation model using a parameterised model
- We define a grid to and apply displacements and translation and thus deform the image underneath
- We can calculate a dense deformation by using basis functions to defined by the control points $x_1$, these allow us to interpolate between the control points
- Called control point based models![[Screenshot 2023-02-07 at 14.26.49.png]]
- Popular because you have low number of parameters 
- We can also use dense displacement fields, and each pixel has a displacement parameter, very flexible but a lot of parameters
- https://core.ac.uk/download/pdf/295548582.pdf