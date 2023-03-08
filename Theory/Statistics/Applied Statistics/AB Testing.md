# A/B Testing

## A/B Testing
- At its very core, A/B testing consists of a randomised experiment with two variants that we name A and B. A and B are usually similar, except for one variation that might affect user behavior

## How to evaluate which feature to test
- One way to evaluate the value of different ideas is to conduct **quantitative analysis** using historical data to obtain the **opportunity sizing** of each idea.
- To get a comprehensive evaluation of each idea, we could conduct **qualitative analysis** with focus groups and surveys.

## Designing A/B tests
Once we select an idea to test, we need to decide how long we want to run a test and how to select the randomisation unit. In this section, we’ll go through these questions one by one.

## How long to run a test
To decide the duration of a test, we need to obtain the sample size of a test, which requires three parameters. These parameters are:
- Type II error rate _β_ or Power, because Power = _1 - β_. You know one of them, you know the other
- Significance level _α_
- Minimum detectable effect

The rule of thumb is that sample size _n_ approximately equals 16 (based on _α = 0.05_ and _β = 0.8_) multiplied by _sample variance_ divided by _δ_ square, whereas _δ_ is the difference between treatment and control.

## How to obtain parameters
Want to know how to obtain each parameter and how each parameter influences the sample size.

For example, we need more samples if the sample variance is larger, and we need fewer samples if the delta is larger.

Sample variance can be obtained from the existing data, but how do we estimate _δ_, i.e the difference between treatment and control?

Actually, we don’t know this before we run an experiment, and this is where we use the last parameter: **the minimum detectable effect**. It is the smallest difference that would matter in practice. For example, we may consider a 0.1% increase in revenue as the minimum detectable effect. In reality, this value is discussed and decided by multiple stakeholders.

Once we know the sample size, we can obtain the number of days to run the experiment by dividing the sample size by the number of users in each group. If the number is less than a week, we should run the experiment for at least seven days to capture the weekly pattern. It is typically recommended to run it for two weeks. When it comes to collecting data for a test, **more is almost always better than not enough**






## AB Testing

### What is A/B testing
* A/B testing is a type of controlled experiment where you show two versions of a product to a sample of customers
	* The experimental group are given the varied version
	* The control group are given the existing version
* The goal of the test is to look at the metric that is a measure of performance during the test period and find out whether there is a difference in the performance of the product in either group and what type of difference it is

### Pros of A/B testing
* Allows for quick changes in a product
* Allows for direct feedback from customer
* Removes bias as users are not aware they are part of either test group

### Cons of A/B testing
* Presenting different content/prices/features to different customers especially in the same geolocation might potentially be dangerous resulting in Change Aversion
	* YouTube recently tested multiple ad’s a in a row and faced backlash even if it was trying to prove that wouldn’t be a positive feature
* Can require significant resources (Data Science, Engineering, etc.)
* Potential for error if test not conducted properly

### Metrics
* Consider two alternate website designs: A and B
* Visitors of a website are **randomly** served one of the two and data about their activity is collected via web analytics
	* Given this data, you can apply statistical tests to determine whether one of the two designs have a better efficacy
* **Discrete metrics** (also called binomial metrics) take one of two values
	* Click-through rate – if a user is shown an ad, do they click on it
	* Conversion rate – if a user is shown an ad, do they convert into customers
	* Bounce rate – if a user visits a website, is the following visited page on the same website
* **Continuous metrics** (also called non-binomial metrics) may take any value
	* Average revenue per user – how much revenue does a user generate in a month
	* Average session duration – for how long does a user stay on a website in one session
	* Average order value – What is the total value of the order of a user
* These two types of metrics require different tests
