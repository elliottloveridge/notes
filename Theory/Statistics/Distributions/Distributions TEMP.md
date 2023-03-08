### Distributions
#### Discrete Metrics
* Consider a discrete metric such as click-through rate
	* Say we have collected the following information;
		* $n_X$ visitors saw ad $A$ and 7 of them clicked on it
		* $n_Y$ visitors saw ad $B$ and 15 of them clicked on it
	* Looks like ad $B$ was more effective, but need to measure how significant this is

![[Example Test.png]]

##### Fisher's Exact Test
* Creating a **contingency table** of the data (above), you can use Fisher's exact test to compute an exact p-value to test our hypothesis
* First notice that you can keep the 4 sub totals fixed whilst changing the values in the table a finite number of times
* The key observation is that, under the null hypothesis, $H_0$, ad A and B have the same efficacy
	* Therefore, the probability of observing any of the possible outcomes is given by the hypergeometric distribution

![[Hypergeometric Distribution.png]]

* Using this formula you obtain:
	* The probability of seeing our actual observation is ~4.5%
	* The probability of seeing an even more unlikely observation in favour of B is ~1.0% (left tail)
	* The probability of seeing an even more unlikely observation in favour of A is 2.0% (right tail)
	* Therefore, p-value ~7.5%

* Fisher's exact test has the advantage of computing exact p-values
	* If we have a large sample size, this may be computationally inefficient
	* In this case we acn use a chi-squared test

##### Pearson's Chi-Squared Test
* If you have a contingency table of size $I\times{}J$, the observed value at a given position is defined as $O_{ij}$
* Under the null hypothesis of independence of rows and columns (assuming A and B have the same efficacy), you can compute the corresponding expected value $E_{ij}$
	* If observations are normally distributed then the $\chi{}^2$ statistic follows exactly a chi-square distribution with one degree of freedom

![[Chi-Square Distribution.png]]

* This test can also be used with non-normal observations if the sample size is large enough thanks to the central limit theorem (CLT)

#### Continuous Metrics
* Consider the continuous metric average revenue per user
	* Want to determine which website layout is preferable based on how much revenue each user generates in a month

##### Z-Test
* The Z-test can be applied under the following assumptions:
	* Observations are normally distributed (or the sample size is large)
	* The sampling distributions have known variance $\sigma{}_X$ and $\sigma{}_Y$
* Under these assumptions, the Z-test exploits the fact that the following Z statistic has a standard normal distribution

![[Z-Test Statistic.png]]

##### Student's T-Test
* Unfortunately, in most real applications the standard deviations are unknown and must be estimated
	* Therefore a T-test is preferable
* A T-test can be applied under the following assumptions:
	* The observations are normally distributed (or the sample size is large)
	* The sampling distributions have similar variances
		* $\sigma{}_X \approx{} \sigma{}_Y$

![[T-Test Statistic.png]]

Where;
* $S_P$ is the pooled standard deviation
	* Obtained from the sample variances