# Linear Regression

## What is Linear Regression
- Linear [[Theory/Machine Learning/Regression|Regression]] is a model that assumes a linear relationship between the input variables ($X$) and the single output variable ($y$)

- This can be denoted as
$$
y = \text{B}_0 + \text{B}_1 \times x_1 + \text{...} + \text{B}_n \times x_n
$$
- Where;
	- $\text{B}_{0\rightarrow n}$ are regression coefficients
		- $\text{B}_0$ is normally termed bias ($b$) and $\text{B}_{1\rightarrow n}$ weights ($w$)
	- $x$ values are the independent (explanatory) variables
	- $y$ is the dependent variable

- The case of one explanatory variable is called simple linear regression
	- $y = \text{B}_0 + \text{B}_1 \times x_1$
	- For more than one explanatory variable, the process is called multiple linear regression

## Why Linear Regression
- Suppose we want to model a dependent variable $Y$ in terms of three predictors; $X_1, X_2,$ and $X_3$
- That is, we want to define a function $f$ such that;

$$Y = f(X_1, X_2, X_3)$$

- Typically there is not enough data to try and directly estimate $f$
	- Therefore we usually have to make the assumption that it is of a restricted form such as linear

## Simple Linear Regression
$$
y = \text{B}_0 + \text{B}_1 \times x_1
$$
- This is equivalent to $y = mx + c$

## Solutions

### Simple Linear Regression
- Linear regression can be solved by estimating some statistical properties of the dataset
	- Need to find the values $\text{B}_0$ and $\text{B}_1$ from;
		- $y = \text{B}_0 + \text{B}_1 . x$
- $\text{B}_0$ can be defined as;
	- $\bar{y} - \text{B}_1 . \bar{x}$
- $\text{B}_1$ can be defined as;
	- $\frac{\mathrm{Cov}(x, y)}{\mathrm{Var}(x)}$
	- Where $\mathrm{Cov}$ is the covariance of the data

### Closed Form Solution
- Linear regression has an algebraic solution
	- Preferable to an iterative process such as [[Gradient Descent]] as it is a more direct way of reaching the optimal solution
- Can be found by taking the derivative (w.r.t weights/regression coefficients) of the loss function and setting this to zero to solve for regression coefficients
- Written as;
	- $X^T . X . b = X^T . y$
- Re-written to solve for $b$ as;
	- $b = (X^T . X)^{-1} . X^T . y$

### Decomposition
- The direct solution seen above has a computationally expensive inverse calculation
	- This [article]([https://machinelearningmastery.com/solve-linear-regression-using-linear-algebra/) goes through two decomposition techniques to improve upon this

### Other Solutions
- It is also possible to solve linear regression iteratively via an optimisation algorithm (e.g. via [[Gradient Descent]]) with the least square error as the cost function to minimise

## Assumptions
- There are several assumptions of linear regression
	- If any of them are violated then model predictions and interpretation may be worthless or misleading

-  **Linear relationship** between each independent variable and the dependent (target) variable
- **Additivity** means that the effect of changes in one of the features on the target variable does not depend on values of other features
	- For example, a model for predicting revenue of a company using two features - the number of items _a_ sold and the number of items _b_ sold
		- When company sells more items _a_ the revenue increases and this is independent of the number of items _b_ sold
		- If customers who buy _a_ stop buying _b_, the additivity assumption is violated
- Features are not correlated (**non-collinearity**) since it can be difficult to separate out the individual effects of collinear features on the target variable
- Errors are independently and identically normally distributed
	- No correlation between errors (consecutive errors in the case of time series data)
	- Constant variance of errors - **homoscedasticity**
		- For example, in case of time series, seasonal patterns can increase errors in seasons with higher activity
    * Errors are normally distributed, otherwise some features will have more influence on the target variable than to others
	    * If the error distribution is significantly non-normal, confidence intervals may be too wide or too narrow

## Pros and Cons

### Pros
1. **Simple model:** Simplest equation to define the relationship between multiple predictor variables and target variable
	- This means it is more easily explainable
2. **Computationally efficient:** There is a closed form solution to linear regression meaning the modeling speed is fast for initial findings
3. **Interpretability of the output:** The ability of linear regression to determine the relative influence of one or more predictor variables (via weighting) to the predicted value when the predictors are independent of each other is one of the key reasons of the popularity of Linear regression. The model derived using this method can express what change in the independent variable causes a given change in the dependent variable

### Cons
1. **Simplistic:** Assumes a linear relationship which often does not capture real world complexity
2. **Linearity assumption:** Linear regression makes strong assumptions that the independent variable(s) and dependent variable are linearly separable
	- On some plane you could separate the data in theory
3. **Severely affected by outliers:** Outliers can have a large effect on the output as the function tries to minimise the cost function for all points
4. **Independence of variables:** Assumes that the predictor variables are not correlated which is rarely true
	- It is important to remove multi-collinearity using dimensionality reduction techniques
	- In cases of high multi-collinearity, two features that have a high correlation will influence each others weights and result in an unreliable model
		- *Would be unable to determine feature importance*
1. **Assumes Homoskedacity :** Linear regression looks at a relationship between the mean of the dependent variable and the independent variable(s) and assumes constant variance around the mean which is unrealistic in most cases

### Summary
- Despite shortcomings, remains useful due to its simplicity and explainability/interpretability
- Can be improved with;
	- Regularization techniques (L1 and L2)
	- Data pre-processing to handle outliers
	- Dimensionality reduction to remove multi-collinearity for preliminary analysis

## Questions
- [[linear-regression-questions]]