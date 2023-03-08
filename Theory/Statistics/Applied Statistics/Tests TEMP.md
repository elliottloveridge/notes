

### Power/Significance Level
- The power or significance level of a test is denoted as;
	- $\alpha \in (0,1)$
- $\alpha$ is the number at which, if $\mathbb{P}(H_0) \lt \alpha$, we would reject $H_0$ in favour of $H_a$
	- $\mathbb{P}(H_0)$ is more commonly known as the $p$-value
	- You set the value of $\alpha$ before an experiment
- $\alpha$ can be thought of as the probability of rejecting $H_0$ when $H_0$ is true
	- We want this to be low if we want to reject $H_0$ confidently
- **Type I error** - rejecting $H_0$ when it is true (false positive)
- **Type II error** - not rejecting $H_0$ when it is false (false negative)
- There is a corresponding probability to $\alpha$ called $\beta$ that represents the probability of failing to reject $H_0$ when it is false
	- $\alpha$ is set by the user, $\beta$ isn't (is calculated)

![[Hypothesis Table.png]]

### Sidedness of a Test
- Sidedness is the number of scenarios where $H_0$ is false
	- One- and Two-sided test
	- Two-sided tests need the value of $\alpha$ adjusted to $\frac{\alpha}{2}$ to take into account the multiple ways to reject $H_0$

### Decision Function
- In the context of hypothesis testing, a decision function is a function that determines whether we accept or reject the null hypothesis
	- $\mathcal{D}(T, F, \alpha, s)$
- $T$: the *test statistic* of the test
	- This is a modified version of $\hat{\theta}$ that is more robust to draw conclusions from
$$T = \frac{\hat{\theta} - \theta_0}{\sqrt{\frac{\text{Var}[\hat{\theta}|\theta_0]}{n}}}$$
- $F$: the cumulative distribution function of the sample distribution
- $\alpha$: the significance level/power of the test
- $s$: the sidedness of the test

![[Decision Function.png]]

- $1 - F(T)$ is also sometimes interpreted as the probability of getting a result as extreme as what we observed

#### Test Statistic
- The test statistic can be defined as;
$$T = \frac{\hat{\theta} - \theta_0}{\sqrt{\frac{\text{Var}[\hat{\theta}|\theta_0]}{n}}}$$
- Where;
	- $\hat{\theta}$: sample statistic
	- $\theta_0$: value we want to test against in $H_0$
	- $\text{Var}[\hat{\theta}|\theta_0]$: variance of the statistic $\theta$ according to its distribution, given the parameter $\theta_0$
- So;
$$\hat{\theta} \sim \mathcal{B}(n,p) \rightarrow \text{Var}[\hat{\theta}|\theta_0] = n\theta_0(1 - \theta_0)$$
$$\hat{\theta} \sim \mathcal{N}(\mu,\sigma^2) \rightarrow \text{Var}[\hat{\theta}|\theta_0] = \sigma^2$$
- Why does this formula make sense?
	- Since all CDFs, $F$, are monotonically (always) increasing then ($1-F(T)$) is monotonically decreasing in $T$
		- Lower $T$ values lead to lower $p$-values

### Z and T Tests
- The $Z$ and $t$ tests are very basic tests that are most often used to test if means are equal/greater than/less than some hypothesised value
	- Generally, $Z$ test are used when the sample size is greater than 30
	- $t$ tests are used for sample size less than 30
#### Z Test
- Description: Tests if the sample mean, $\hat{\mu}$, is equal to/less than/greater than $\mu_0$
- Statistic: $\mu$
- Distribution: $\mathcal{N}(\mu, \sigma^2)$ (normal)
- Sidedness: Either
- Null Hypothesis: $H_0: \mu = \mu_o$
- Test Statistic: $Z = \frac{\mu - \mu_0}{s/\sqrt{n}}$ ($s = \sigma$ if known)

- The sample mean is defined by;
$$\hat{\mu}_X - \frac{1}{n}\Sigma^n_{i=1}x_i$$
- The test-statistic of the $Z$-test, called the $Z$-score, is defined as;
$$Z = \frac{\hat{\mu} - \mu_0}{\sigma / \sqrt{n}}$$
- Where $\sigma$ is the standard deviation of the assumed sample distribution (normal)
- Most of the time, $\sigma$ is not known in advance, so it is estimated through the sample standard deviation, $s$
$$s = \sqrt{\frac{1}{n-1}\Sigma^n_{i=1}(x_i - \hat{\mu})^2}$$
- This works because $s$ is an unbiased estimator for $\sigma$
	- $\mathbb{E}[s] = \mathbb{E}[\sigma]$


