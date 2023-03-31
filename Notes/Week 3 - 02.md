### Image Classification

### Ensemble Classifiers

- Boosting 
- Decision/Random forests

##### Where does classification error come from?

*Bias error*
	- how much, on average, predicted values are different from the actual value.
	- high bias error means we have an under-performing model, which misses important trends.

*Variance error* 
	- how much predictions made from different samples vary from one other. 
	- high variance error means the model will over-fit and perform badly on any observation beyond training.
![[Screenshot 2023-01-23 at 18.40.35.png]]
![[Screenshot 2023-01-23 at 18.42.22.png]]

#### Ensemble Learning
- Aggregate the predictions of a group of predictors (either classifiers or regressors)
- A group of predictors is called an ensemble
- A learning algorithm which uses multiple models, such as classifiers or experts, is called Ensemble Learning (so called meta-algorithms)
- We can achieve better results if we assume that the classifiers are all independent (uncorrelated)![[Screenshot 2023-01-23 at 18.49.12.png]]

#### Types of Ensemble Learning
- Homogenous: Combine predictions made from models built from the same ML class (weak learners); each with slightly different subsets of the data
- Heterogenous:  Combine predictions made from models built from different ML classes
- Sequential: base (ML) learners are added one at a time; mislabelled examples are upweighted each time, Decreases bias
- Parallel: many independent base learners are trained simultaneously and then combined, Decreases variance

#### Weak Learners
- A weak learner is defined to be a classifier that is only slightly correlated with the true classification (it can label examples slightly better than random guessing). We want to find a way to split the data. ![[Screenshot 2023-01-23 at 18.51.49.png]]
- In contrast, a strong learner is a classifier that is arbitrarily well correlated with the true classification.

Example
![[Screenshot 2023-01-23 at 18.52.41.png]]
![[Screenshot 2023-01-23 at 18.52.52.png]]
Decision Stump
- A classic weak learner is a decision stump 
- It is a one-level decision tree that is axis-aligned![[Screenshot 2023-01-23 at 18.53.57.png]]

### Bagging and Boosting

##### Bootstrap Aggregation (Bagging)
- Reduce model variance through averaging
- For $n$ independent samples: $var(\hat{X})= \frac{var(X)}{n}$
- But: only one training dataset, so where do samples come from?![[Screenshot 2023-01-23 at 19.05.00.png]]
- For large enough samples Bootstrap sampling will closely approximate any sampling distribution estimated from the full population![[Screenshot 2023-01-23 at 19.05.51.png]]

##### Out-of-Bag (OOB) error
- How to evaluate error of a bootstrapped ensemble approach such as bagging?
	- With each training set we automatically get a left-out set
	- We can use this as a validation set and compute the mean prediction error

##### Boosting
- build weak learners in serial
- but adaptively reweight training data prior to training each new weak learner in order to give a higher weight to previously misclassified examples![[Screenshot 2023-01-23 at 19.10.05.png]]
- Several variants:
	- Adaboost (adaptive boosting)
	- Gradient Tree Boosting 
	- XGBoost
##### Adaboost
Algorithm:
![[Screenshot 2023-01-23 at 19.12.54.png]]
![[Screenshot 2023-01-23 at 19.13.09.png]]
![[Screenshot 2023-01-23 at 19.14.09.png]]
![[Screenshot 2023-01-23 at 19.14.24.png]]
- What to use as weak learners?
	- Decision stumps
- How to weight the examples?
	- ![[Screenshot 2023-01-23 at 19.12.02.png]]
- Example: Face Detection using Adaboost Non-maximal suppression (NMS)
##### Decision Forests
- Decision trees used generally are of two main types: 
	1. Classification tree analysis when the predicted outcome is the class to which the data belongs. 
	2. Regression tree analysis when the predicted outcome can be considered a real number (e.g. the price of a house, or a patient's length of stay in a hospital).
![[Screenshot 2023-01-23 at 19.30.54.png]]

Decision Tree Optimisation
![[Screenshot 2023-01-23 at 19.31.49.png]]
![[Screenshot 2023-01-23 at 19.33.26.png]]
![[Screenshot 2023-01-23 at 19.39.26.png]]
![[Screenshot 2023-01-23 at 19.39.54.png]]
- Information Gain must be maximised
![[Screenshot 2023-01-23 at 19.41.08.png]]
- Gini index must be minimised 
##### Decision Trees as Weak Learners
- Single Decision Trees are prone to overfitting, particularly if tree depth is not controlled, but robustness can be significantly increased by combining trees in ensembles 
- Decision trees are among the most popular weak learners for homogenous ensemble learning
- Random forests form an ensemble of uncorrelated classifiers by exploiting random subsampling of the 
	- training data used to build each tree 
	- set of features that are used for selection of the splits 
	- set of feature values that are used for splitting
![[Screenshot 2023-01-23 at 19.35.10.png]]
- Tree Ensembles (Forests): Image Classification, ‘Bike’ visual words for different images. The brightness denotes the posterior probability for the visual word at the given image position to be labelled ‘bike’.