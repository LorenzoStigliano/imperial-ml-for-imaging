#### Common Image Analysis Tasks

- Image classification: Given an image what is the categoy of the image
- Object detection: Find the location of objects find coordinates
- Object localisation: Find bounding boxes
- Object recoginition: Object recoginition you have a found the object and you pass the image in boundining box to identify the object
- Sematic segmentation: input image into a labelmap, each point is segmentated into a semantic group
- Object tracking: track objects in videos, time series data
- Image Registration: Correspondence between two images, used in panormic images
- Point Correspondences: Match pair of points between two images

#### Image Computing

- Digit recoginition: basic problem in imaging, goal we want to find a feigit reogintion algorithm to detect the digit
- What is an image? An array of numbers, for each pixel
- Naive solution: binary images, plot histrograms, we have distrbution for different types of digits to decide which image belongs to which image -> cannot generalize to all the digits

#### ML overview

##### Supervised Learning
Given a vector of input features $\mathbf{x}$, we want to learn a predictor $h_{\Theta}(\mathbf{x})$, that outputs an accurate prediction $y$
$$
h_{\Theta}(\mathbf{x})=y
$$
Using a training set $T=\left\{\left(\mathbf{x}^{(i)}, y^{(i)}\right)\right\}_{i=1}^m$ with $m$ examples, the predictor is trained (somehow) such that
$$
\forall i\left[h_{\Theta}\left(\mathbf{x}^{(i)}\right) \approx y^{(i)}\right]
$$
##### Linear Regression
Given input vector $\mathbf{x}$ and output $\mathbf{y}$
$$
\begin{aligned}
h_{\Theta}(\mathbf{x}) & =\Theta^{\top} \mathbf{x} \\
& =\Theta_0 x_0+\Theta_1 x_1+\Theta_2 x_2+\cdots+\Theta_n x_n
\end{aligned}
$$

cost function $\eta(\theta)$: $\min _{\Theta} \frac{1}{m} \sum_{i=1}^m\left(h_{\Theta}\left(x^{(i)}\right)-y^{(i)}\right)^2$

##### Gradient Descent

Given a hypothesis $h_{\Theta}$ and a cost function $J(\Theta)$
- Take an initial guess for the parameters $\Theta$
- Keep changing $\Theta$ to minimise $J(\Theta)$ until convergence
$$\begin{aligned}
& \text { repeat until convergence } \\
& \qquad \Theta_j:=\Theta_j-\alpha \frac{\partial}{\partial \Theta_j} J(\Theta)
\end{aligned}$$
- $\alpha$ is the learning rate 

##### Classification

We look at logisitic regression. Fit a line across binary values and then normalize between 0 and 1 to find a threshold using the logistic sigmoid function - classification.

Hypothesis
$$
h_{\Theta}(\mathbf{x})=\frac{1}{1+e^{-\Theta^{\top} \mathbf{x}}} \in[0,1]
$$

Prediction
$$
\begin{aligned}
& h_{\Theta}(\mathbf{x}) \geq 0.5 \rightarrow y=1 \\
& h_{\Theta}(\mathbf{x})<0.5 \rightarrow y=0
\end{aligned}
$$
Decision Boundary, we can also have non-linear boundaries where the data is not seperable

$h_{\Theta}(\mathbf{x})=g\left(\Theta_0+\Theta_1 x_1+\Theta_2 x_2\right)$
$\theta=\left[\begin{array}{c}-3 \\ 1 \\ 1\end{array}\right] \rightarrow-3+\underbrace{x_1+x_2}_{x_1+x_2 \geq 3} \geq 0$ so the decision boundary for this problem is at: $x_1+x_2=3$

Cost function

![[latexImage_ce78a85155262e5285f2b97869a51aec.png]]

##### Overfitting/Underfitting

- Underfitting = high bais
- Overfitting = high variance

To diagnose this we plot the error against the degree of polynominal on the training and the validation sets![[Screenshot 2023-01-18 at 18.56.33.png]]

##### Regularisation

Add a penalty term on the coefficients to reduce the model complexity, L2 ridge penalty and L1 regularization lasso, lambdas become hyperparameters we need to tune.

##### Learning Curves

Plot errors vs training size
- High bais: high training, high test error (more training will not help)
- High variance: you could improve the error by including more trainig data

![[Screenshot 2023-01-18 at 19.02.55.png]]

