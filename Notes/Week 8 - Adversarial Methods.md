## Adversarial attacks
![[Screenshot 2023-02-25 at 15.05.26.png]]

### Perturbation
![[Screenshot 2023-02-25 at 15.07.52.png]]
![[Screenshot 2023-02-25 at 15.09.56.png]]
- Why does this work?![[Screenshot 2023-02-25 at 15.10.32.png]]![[Screenshot 2023-02-25 at 15.10.54.png]]
- $m$ is average the magnitude of the parameters
- $n$ is the number of pixels in the image
- This means that the change in activation given by the perturbation increases linearly with respect to $n$ (or the dimensionality).
- If $n$ is large, one can expect even a small perturbation capped at $\epsilon$ to produce a perturbation big enough to render the model susceptible to an adversarial attack. 
- Such perturbed examples as referred to as adversarial examples

### Fast Gradient Sign Method
- ![[Screenshot 2023-02-25 at 15.14.44.png]]
- Gradient loss w.r.t to the input image 

- How can you use adversarial attacks for defense? Adversarial data augmentation 
	1. Generate adversarial examples 
	2. Add the generated adversarial examples to the training set
	3. Retrain model using training set

