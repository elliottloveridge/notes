# ML Models

- Machine learning is essentially learning a function ($f$) that maps input variables ($X$) to a given output variable ($Y$)
$$Y = f(x)$$

- The machine learns from training data to map the target function but the configuration of the function is unknown
	- However, ML algorithms are parameterised so that their behaviour can be tuned for a given problem

## Parametric Models
- In a parametric model, you know exactly which model you are going to fit in with the data
- Parametric models deal with discrete values
	- Non-parametric models deal use continuous values
- A _parametric_ algorithm is one that has a constant set of parameters, which is independent of the number of training samples. You can think of it as the amount of much space you need to store the trained classifier. An examples for a parametric algorithm is the Perceptron algorithm, or logistic regression. Their parameters consist of w,b, which define the separating hyperplane

## Non-parametric Models
- Non-parametric ML algorithms do not make specific assumptions about the type of mapping function
	- Non-parametric does not mean that the model lacks parameters existing in it (e.g. tree depth for a decision tree) but rather that the parameters are adjustable and can change
- In contrast, the number of parameters of a _non-parametric_ algorithm scales as a function of the training samples
- Non-parametric models are statistical models that do nor often conform to a normal distribution (as they rely upon continuous data rather than discrete values)