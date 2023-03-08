### Hypothesis Testing
- _Hypothesis Testing_ is a systematic way to make inferences from sample data
- A sample has the following properties:
	- Sample size, $n$
	- Sample statistic, $\hat{\theta}$
		- Can be calculated from the sample
	- Sample distribution
		- If creating a yes/no survey, it would follow a binomial distribution for example
- In hypothesis testing we always assume the null hypothesis to be true with the aim to see if we have enough evidence from the data to find that it is in fact false

#### Null and Alternative Hypothesis
- Every hypothesis test has two outcomes
	- Null hypothesis, $H_0$
	- Altenative hypothesis, $H_a$
- Usually, the two hypotheses involve seeing if some statistic $\hat{\theta}$ is different from a value, denoted $\theta{}_0$

#### Example
- Say you wanted to test if people prefer coffee to tea
- You would set up the following test
	- $H_0 : p \le 0.5$
	- $H_a : p \gt 0.5$
	- Where $p$ is the sample statistic or proportion of people in the sample set that prefer coffee to tea
- The idea behind hypothesis testing is that you can never *really* know if an assumption is true from data but you can show how unlikely it would be to get the data we currently have if the assumption was false
	- For example, if out of 20 people, 13 said that they preferred coffee, you can't really say that this definitely shows more people like coffee than tea
		- But you *can* calculate how likely it would be to get this result if, in reality, only 50% of people prefer coffee to tea (null hypothesis is true)

![[Hypothesis Calculation.png]]

- From this probability we can make informed conclusions about our data
	- We might say that, because there is only a 13% chance of getting the result we got if the split was 50/50, it probably isn't 50/50
		- In reality too small a sample size to say this






## Hypothesis Testing
Steps to Hypothesis testing:  
1. State the null and alternative hypothesis  
2. Determine the test size and duration; is it a one or two-tailed test?  
3. Compute the test statistic and the probability value  
4. Analyse the results and either reject or do not reject the null hypothesis (_if the p-value is greater than the alpha, do not reject the null!)_

**P-value:** the probability of obtaining the observed results of a test, assuming that the null hypothesis is correct; a smaller p-value means that there is stronger evidence in favor of the alternative hypothesis.

**Alpha:** the significance level; the probability of rejecting the null hypothesis when it is true — also known as **Type 1 error**

Confidence Interval: 1 - p-value: A confidence interval is the [mean](https://www.scribbr.com/statistics/mean/) of your estimate plus and minus the variation in that estimate. This is the range of values you expect your estimate to fall between if you redo your test, within a certain level of confidence.

**Beta:** type 2 error; failing to reject the null hypothesis that is false

Confidence Interval





## Statistical Concepts

### Statistical Significance
* Comparing mean values from a test would not be useful as you would fail to understand the statistical significance of the test (how likely this outcome is)
	* Assess how likely it is that the observed difference between the two samples originates from chance
* To do this, use a two-sample hypothesis test
* Null hypothesis ($H_0$) - no change in efficacy of the two website designs
	* They produce an equivalent click-through rate, etc.
* The statistical significance is measured by the *p-value*
	* The probability of observing a difference between the experimental and control group (samples) at least as strong as we actually observed
$$p_{val} = p(\text{data at least as extreme as actual observation}|H_0)$$
* Your alternate hypothesis, $H_1$ is an important choice
	* This choice corresponds to the choice between a one and two-tailed test
* Two-tailed test - preferable when you want to measure a change (either direction)
* One-tailed test - direction dependent (greater than or less than)