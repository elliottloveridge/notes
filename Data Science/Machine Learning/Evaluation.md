# Evaluation

## Regression

### Error Terms
- **Mean Absolute Error** (MAE) is the mean of the absolute value of the errors
	- $\frac{1}{n}\sigmai=1n|yi−ŷ i|$

**Mean Squared Error** (MSE) is the mean of the squared errors:

1n∑i=1n(yi−ŷ i)2

**Root Mean Squared Error** (RMSE) is the square root of the mean of the squared errors:

1n∑i=1n(yi−ŷ i)2‾‾‾‾‾‾‾‾‾‾‾‾‾‾⎷

## Classification

### Definitions
- **True Positive:** A model correctly classifies a positive sample
- **False Negative:** A model incorrectly classifies a positive sample as belonging to the negative class
- **False Positive:** A model incorrectly classifies a negative sample as belonging to the positive class
- **True Negative:** A model correctly classifies a negative sample

### Precision
- The ratio of correctly classified positive samples (true positives) to total number of classified positive samples (either correctly or incorrectly)
- Measures a models ability to classify positive samples in the model
- **Precision = True Positive / (True Positive + False Positive)**

### Recall
- The ratio between the numbers of true positives to the total number of positive samples
- Measures a models ability to detect positive samples
	- The higher the recall, the more positive samples detected
- **Recall = True Positive / (True Positive + False Negative)**

### ROC Curve
- A curve commonly used to measure performance of a binary classifier (two output classes)
	- For example, you build a classifier to predict if a research paper will be admitted to a journal based on a variety of factors
- A plot of the True Positive Rate (TPR) on the y axis vs the False Positive Rate (FPR) on the x axis
	- True Positive Rate = True Positives / All Positives
	- False Positive Rate = False Positives / All Negatives
- To get the curve you plot this for all possible classification thresholds (0 to 1)
- ROC Curves can be extended to problems with three or more classes
	- One vs all approach (i.e. for three classes you would have three curves)
		- Curve 1: Class 1 vs Classes 2 and 3
- Choosing a classification threshold is a decision related to the task you are working on
	- Do you want to minimise your FPR?

### AUC
- AUC or Area Under the Curve is just the percentage of area under the ROC Curve vs area above it
- AUC of 1 would be a perfect classifier
- AUC of 0.5 would be random guessing
