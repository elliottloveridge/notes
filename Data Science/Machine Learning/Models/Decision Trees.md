# Decision Trees

* Decision trees are a #non-parametric #supervised-learning method used for both #regression and #classification tasks
* The goal of a decision tree is to create a model that predicts the value of a target variable by learning simple decision rules inferred from the features
	* The decision tree algorithm builds decision trees using a top-down, greedy approach

## What is a Decision Tree
* A decision tree is a tree-like graph with;
	* Nodes that represent choosing an attribute and asking a question
	* Edges that represent the answer to a question
	* Leaves that represent the output or class label
* When splitting the dataset at a given node, the steps are;
	- Select the best attribute, $A$, by potential information gain (IG)
		- A decision tree partitions the feature space such that the dependent values are grouped together to allow for regression or classification
	- Assign $A$ as the decision attribute for the node
	- Split the data by attribute $A$
- Recursively, for every node of the tree, calculate the best split until a criteria is reached
	- The criteria can be a fixed limit on tree depth or minimising some cost function (see Impurity Functions below)

### Decision Stump Process
- Consider a node $m$
- Let the train data at node $m$ be represented by $Q$ with $n$ observations
- For each feature, $\theta$, partition the data into left and right subsets, $Q_l(\theta)$ and $Q_r(\theta)$, with the number of observations $n_l$ and $n_r$ respectively
- The quality of the feature (split candidate) at node $m$ is computed using an impurity function, $H$
- The optimal split, $\theta^*$, is one that minimizes the weighted impurities
$$\theta^* = argmin_\theta \left( \frac{n_l}{n}H(Q_l(\theta)) + \frac{n_r}{n}H(Q_r(\theta))\right)$$
## Information Gain
- When splitting at a node based on some feature/characteristic of the data we look to understand the potential information gain from a given split
	- In this context, *information gain is a measure of the reduction in entropy when splitting the data*
		- We therefore want to make a split that maximises information gain

### Entropy
- We can think about the entropy of a dataset in terms of the probability distribution of observations in the dataset belonging to one class or another (for the case of binary classification anyway)

> Entropy specifies the minimum number of bits of information needed to encode the classification of an arbitrary member of S (a member of S drawn at random with uniform probability)

- Entropy can be defined as;
$$Entropy = - \sum\limits_{i=1}^n \text{P}(x_i)\log{}\text{P}(x_i)$$
- Where $\text{P}(x_i)$ is the probability of drawing class $i$ given the split
	- Equivalent to the proportion of data points belonging to this class within the dataset
- An entropy of 0 would indicate a dataset contains only one class (corresponding to maximum information gain)

#### Impurity Function
- Entropy is one example of an impurity function used when building a decision tree

##### Classification
- If the target variable $y$ is a discrete outcome taking on values;
	- $k \in \{0, 1, ..., K-1\}$
- The proportion of class $k$ observations in node $m$ is given by;
$$p_k = \frac{1}{n}\sum\limits_{y \in Q}I(y=k)$$
- Where $I$ is the impurity criterion
	- Common measures for impurity for classification are;
		- Gini: $H(Q) = \sum\limits_k p_k(1-p_k)$
		- Entropy: $H(Q) = -\sum\limits_k p_k \log(p_k)$
		- Where $p_k$ is the proportion of data points belonging to class $k$ with the proposed split
##### Regression
- If the target variable $y$ is a continuous outcome let the average of all target variables in node $m$ be defined as;
$$\bar{y} = \frac{1}{n}\sum\limits_{y \in Q} y$$
- Common measures of impurity for regression are;
	- Mean Squared Error: $H(Q) = \frac{1}{n}\sum\limits_{y \in Q} (y - \bar{y})^2$ 
	- Half Poisson Deviance: $H(Q) = \frac{1}{n}\sum\limits_{y \in Q} (y \log \frac{y}{\bar{y}} - y + \bar{y})$
		- Useful if target variable is a count or frequency (count per unit)
	- Mean Absolute Error: $H(Q) = \frac{1}{n}\sum\limits_{y \in Q} |y - \text{median}(y)|$ 

## Example - Classification

### Dataset
| Height | Weight | Class  |
|--------|--------|--------|
| 1.8    | 80     | Male   |
| 1.5    | 60     | Female |
| 1.7    | 70     | Male   |
| 1.9    | 85     | Male   |
| 1.4    | 55     | Female |

### Gini Index
- For classification, Gini Impurity is a common choice of impurity function
- Say we decided to split the data for *weight = 75*
	- Left Split - Male: 1 / 3
	- Left Split - Female: 2 / 3
	- Right Split - Male: 2 / 2
	- Right Split - Female: 0 / 2
- Gini (Left Split): sum(proportion(1-proportion))
- = 
