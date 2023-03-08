# Gradient Boosting
- Gradient boosting is another boosting model
	- The aim of a boosting model is to learn from previous mistakes (residual error)
- You pass in the residual error of the previous decision tree prediction as the new target variable
	- The final prediction is made by summing up the predictions of all trees

## Error and Residual Error
- Error of an observation is the deviation of the observed value from the true value
	- Population mean
- Residual error is the difference between the observed value and the estimated value
	- Sample mean

- Why does fitting new models to the residuals of the current model increase the performance of the complete model?
	- Take the gradient (derivative) of the sum of squared error loss function for a single training instance
		- So the residual is the negative gradient of the loss function for this training instance
			- Therefore, training on residuals is actually a gradient descent algorithm on the squared error loss function
				- Minimises until it reaches a local minima