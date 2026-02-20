## Conditional Probability

Conditional probability allows us to update probabilistic models when additional information is revealed.

It can be treated as the conditional probability of $S'$ given $S$.
- Intuitively this can be interpreted as the fraction of outcomes in $S$ that are also in $S'$;

$$P(S|S') = \frac{\text{outcomes in S' and S}}{\text{outcomes in S}}$$

$$= \frac{P(S' \cap S)}{P(S)}$$

- ==S can have zero probability in continuous p-spaces==

**Example**

JFK airport hires you to estimate how the punctuality of flight arrivals is affected by the weather. You begin by defining a probability space for which the sample space is;

$\Omega$ = {late and rain, late and no rain, on time and rain, on time and no rain}

From previous flights you determine that a reasonable probability measure of the p-space is;

P(late, no rain) = $\frac{2}{20}$, P(on time, no rain) = $\frac{14}{20}$

P(late, rain) = $\frac{3}{20}$, P(on time, rain) = $\frac{1}{20}$

Therefore, P(late|rain) = $\frac{\text{P(late, rain)}}{\text{P(rain)}} = \frac{3/20}{3/20 + 1/20} = \frac{3}{4}$

---

Conditional probabilities can also be used to compute the intersection of events;

$P(A \cap B) = P(A) P(B|A) = P(B) P(A|B)$

- ==$P(A)$ is known as the prior probability of A with $P(A|B)$ known as the posterior probability (as you have learned some information)==
- This can be used in [[Bayes' Theorem]]