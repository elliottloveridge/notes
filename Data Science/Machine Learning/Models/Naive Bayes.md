- To make classifications, we need to use $X$ to predict $Y$;
$$P(Y=y|X=(x_1, x_2, ..., x_n))$$
$$\text{Prediction} = argmax_y (Y=y|x=...)$$
## Bayes Theorem
- Bayes theorem can be defined as;
$$P(Y|X) = \frac{P(X|Y)P(Y)}{P(X)}$$
Or more simply;
$$\text{Posterior} = \frac{\text{Likelihood} \times \text{Prior}}{\text{Evidence}}$$
- We cannot infer $P(Y|X)$ directly, but we can get $P(X|Y)$ and $P(Y)$ from the training data
- For example, say you have (discrete) features of;
	- Outlook
	- Temperature
	- Humidity
	- Windy
- You also have a target variable Play (Yes/No binary value)
- You aren't able to determine $P(Y=\text{Play}|Outlook=\text{Sunny})$
	- You can determine the following;
		- $P(Y=Play) = \frac{N_{Play}}}{N_{Play} + N_{\text{Not Play}}}$
		- $P(X = sunny|Y = Play) = \frac{\text{Play and Sunny}}{\text{Play}}$
- Theoretically, it is not hard to find $P(X|Y)$ however it becomes harder in reality as the number of features grows
	- $P(x_0, x_1, ..., x_k|Y=y)$
		- This is known as a parameter in Naive Bayes