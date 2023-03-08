# Random Forest

## What is a Random Forest
- A random forest (RF) consists of multiple random decision trees
	- Each tree is built upon a random sample from the original data
	- At each tree node, a subset of features are randomly selected to generate the best split
- Large number of individual decision trees that operate as an ensemble
	- The class with the most votes of all decision trees is the classification of the model
- A large number of relatively uncorrelated models (trees) operating as a committee will outperform and of the individual constituent models
	- The low correlation between models is key
	- Helps to reduce the variance

### Bagging
- Bagging (Bootstrap Aggregation)
	- Decision trees are sensitive to the data they are trained on
	- Each tree randomly samples from the dataset with replacement
	- We still give each tree data of size N, just sampling with replacement

#### Bootstrap
- Bootstrap is a powerful statistical method for estimating a quantity from a data sample
- Say you had 100 samples, you could calculate the sample mean directly
	- Or you could sample these 100 samples n times and calculate these means
	- Then taking the mean of the mean

### Feature Randomness
- In a normal decision tree, when it is time to split a node, we consider every possible feature and pick the one that produces the most separation between the observations in the left node vs those in the right node
- Each node in a random forest can only pick from a random subset of features
