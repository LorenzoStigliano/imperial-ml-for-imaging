- Constrained optimisation problem 
- ![[Screenshot 2023-02-25 at 14.41.15.png]]

## Parameterizing images via generative networks

- Consider a generator network $Ψ$ with a fixed input $z_o$ 
- The network parameters $w$ can be thought as a parameterization of images$w \rightarrow x =Ψ(z_o;w)$![[Screenshot 2023-02-25 at 14.43.57.png]]
- ![[Screenshot 2023-02-25 at 14.44.40.png]]
- This is used to learn a parameterisation of the image $x$
- For most generative networks fitting naturally looking images is easier/faster than fitting others![[Screenshot 2023-02-25 at 14.46.05.png]]

### Deep image prior: Application to inpainting
![[Screenshot 2023-02-25 at 14.47.07.png]]
![[Screenshot 2023-02-25 at 14.48.03.png]]

### Inverting codes via deep image priors

![[Screenshot 2023-02-25 at 14.48.51.png]]
- We want to invert the layer by applying a deep image prior 
- We want to minimise the loss of the L2 prior and then we get the inversion result
- $z_0$ is fixed during the optimisation process

### Learning the inverter from data
![[Screenshot 2023-02-25 at 14.52.55.png]]
- This idea is so the inverter can learn what a natural image looks like 

### Diagnostic vs aesthetic value
![[Screenshot 2023-02-25 at 14.56.06.png]]
