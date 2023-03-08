# Machine Learning Introduction

## What is Machine Learning
- **Programming** - computer does **exactly** what you tell it to
- **Artificial Intelligence** - computer uses optimisation to find an optimal solution to a given problem
- **Machine Learning** - computer learns from examples (data) and generalises to all inputs

- There are three main areas of machine learning:
	1. Supervised learning - uses a labeled dataset with input ($x$) and output ($y$)
	2. Unsupervised learning - there is no labeled output ($y$) - finds patterns in data
	3. Reinforcement learning - actions in an environment with some delayed reward
- There is also semi-supervised learning
	- It is cheap to collect data but expensive to label, so this works by having a minority of labeled examples
	- Weakly-supervised is similar as accurate labels are expensive and so you learn strong (accurate) labels from weak (inaccurate) ones

## The process
1. Find a problem
2. Obtain required data
3. Choose or design a model
4. Fit model to data using optimisation
	1. Learn $y = f(x)$ from data
5. Measure performance

> Machine learning is discovering the rule, using the rule is just programming

## Problem types
- The majority of machine learning is either classification or regression
- **Classification** - the output ($y$) is a discrete label
	- Multi-label classification: $y$ is a set
		- e.g. identifying objects in an image
- **Regression** - the output ($y$) is continuous
- **Structure Prediction** (another type of supervised learning) - $y$ is anything else
	- Sentence tagging - $y$ is a sequence

### What kinds of problem can an ML algorithm solve?
#### Supervised learning
Learn a function $y=f(x)$ from many examples of input ($x$) output ($y$) pairs

#### Unsupervised learning
Learn a function to represent unknown patterns within data

##### Examples
- Clustering
	- Groups *similar* data points
		- This similarity definition is arbitrary and dependent on each problem
- Density estimation
	- Learns the distribution of data - i.e. $x_i \sim P$
- Dimensionality reduction
	- Also called manifold learning
	- Reduce dimensions whilst preserving information
		- Useful for visualisation - important for verification

---
- You can also classify ML algorithms by accuracy:
- Point estimate (definite)
- Probabilistic
- Bayesian



