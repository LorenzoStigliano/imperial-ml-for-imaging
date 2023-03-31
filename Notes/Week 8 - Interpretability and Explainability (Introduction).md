## Why is this important?

This is not a new problem, so why now? 
- Complexity and prevalence! 
- Safety and robustness is critical 
- Generating knowledge

- Debugging machine learning 
	- Why does my model not train? 
	- Why does my model exhibit unexpected/unintuitive behaviour?

- To use machine learning responsibly we need to ensure that 
	- Our values are aligned 
	- Our knowledge is reflected

### Use cases
- Detecting bias - geographical, racial, gender. Depending on what dataset we use

## Common misunderstandings
- Simple ML models (e.g. linear models or decision trees are interpretable) - simple models can become very complex
- Trust, fairness and interpretability are all the same thing - this is not the case![[Screenshot 2023-02-25 at 12.07.27.png]]
- We don’t always care about interpretability:
	- No significant consequences or when predictions are all you need
	- Sufficiently well-studied problem 
	- Prevent gaming the system

### Types of methods

- Before building ML model
- During building ML model
- After building ML model

## How can we interpret an existing ML model?

- Ablation test: How important is a data point or feature?
	- Train without certain data or features and observe/study the impact 
	- Difficult and expensive
- Fit functions to the data (use first derivatives)
	- Sensitivity analysis - local analysis showing contradictory explainations 
	- Saliency maps
![[Screenshot 2023-02-25 at 12.21.05.png]]
- We can do a sensitivity analysis:![[Screenshot 2023-02-25 at 12.21.30.png]]
- We are back-propagating output probability w.r.t the input pixels