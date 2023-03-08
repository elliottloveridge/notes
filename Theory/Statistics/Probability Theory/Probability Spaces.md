## Probability Spaces

The goal is to build a mathematical framework to represent and analyse uncertain phenomena (such as rolling a die). For this we model the phenomenon of interest as an **experiment** with several (possibly infinite) #mutually-exclusive **outcomes**.

Except in simple cases when the number of outcomes is small, it is normal to reason using sets of outcomes (events).
- To quantify how likely it is for the outcome of an experiment to belong to a specific event, you assign a [[Probability and Counting]].

The experiment is characterised by constructing a **probability space**, consisting of:
- A #sample-space $\Omega$, which contains all possible outcomes of an experiment
	- Two coin tosses would have the sample space {hh, tt, ht, th}
	- P($\Omega$) **must** equal 1
	- The event space $A$ is within this sample space
- A set of events $\mathcal{F}$
	- They must be a **$\sigma$-algebra**
		- Used in set theory to denote a collection of sets that satisfy certain conditions.
		- A complex way of saying if we give some probability to an event we **must** also give a probability to its complement and its union
- A #probability-measure $P$ that assigns probabilities to the events in $\mathcal{F}$

Sample spaces may be #discrete or #continuous. A coin toss is an example of a discrete sample space, temperature or time are continuous sample spaces, usually intervals or $\mathbb{R}$ or $\mathbb{R}^n$.

