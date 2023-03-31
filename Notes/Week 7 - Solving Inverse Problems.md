![[Screenshot 2023-02-20 at 10.05.40.png]]
- $n$ is noise 
- $A$ is an operator 
- We need to recover $x$ from $y$
 ![[Screenshot 2023-02-20 at 10.07.47.png]]
- Ill conditioned matrix for the least squares solution
 ![[Screenshot 2023-02-20 at 10.08.14.png]]
- For better solutions we use the following set up
![[Screenshot 2023-02-20 at 10.11.21.png]]
## Regularisation in inverse problem
- Instead of choosing ℛ a-priori based on a simple (geometric or other) model of image, learn ℛ from **training data**![[Screenshot 2023-02-20 at 10.14.08.png]]

## Forward model/Inverse model
- Forward model is easy to compute but the inverse model is extremely hard to get back ![[Screenshot 2023-02-20 at 10.15.14.png]]
