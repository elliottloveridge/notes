# Logistic Regression

- Logistic Regression is a supervised machine learning #classification algorithm
- There are multiple types of logistic regression:
	- *Binary*
	- *Multinomial/Multiple* - The target variable takes on more than two possible categorical values
	- *Ordinal* - Same as multiple except the target variables are ordered 
- It follows on from the [[Linear Model|LPM]] but solves the following problems of this:
	* It is non-linear (in terms of probability)
		* $Y$ is dependent on $X$'s and the slope coefficients
	* The range of values of $Y$ is restricted between 0 and 1
	* Logistic regression does not require homoscedasticity
		* Errors unrelated to the independent variables
* Logistic regression can be evaluated by the following;
	* Accuracy
	* ROC AUC
		* Preferable to accuracy, especially in multi-class prediction or when there is a class imbalance problem

## Theory
- For [[Linear Regression]] (with the case of one independent variable) we had the linear model defined as;
$$y = \text{B}_0 + \text{B}_1 \times x_1$$
- Logistic regression maps this linear model to outcome probabilities bounded between 0 and 1
	- The aim of training a logistic regression model is to find the best weights for the linear model
- The logistic regression curve, seen below, uses a sigmoid function with a formula defined as;
$$S(x) = \frac{1}{1 + e^{-x}} = \frac{e^x}{e^x + 1}$$
- Where, if we have one independent variable (same as the linear model above);
$$x = \text{B}_0 + \text{B}_1X$$
![[Logistic Regression Graph.png]]

### Cost Function
- The cost function is a formal representation of an objective that the algorithm is trying to achieve (minimise in this case)
- For logistic regression, the cost function used is Log Loss (Cross-Entropy Loss)
$$J(\theta)\\ = -\frac{1}{m}\sum\limits_{i=1}^m[y^i\log(h_\theta x^i) + (1 - y^i)\log(1-h_\theta x^i)]$$
- To minimise this cost function we use [[Gradient Descent]]
	- Could also use [[MLE]]

### Coefficients
* The coefficients for logistic regression are interpreted as *log odds*
	* The natural log transform applied to odds ratio
* An odds ratio (OR) can be written as;
$$OR = \frac{P}{1 - P}$$
* Where $P$ is the probability of success given the values of $X$
* Applying a natural log transform gives us;
$$\log({\frac{P}{1 - P}})$$
