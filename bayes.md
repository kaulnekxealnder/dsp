Bayes' Theorem is an important tool in understanding what we really know, given evidence of other information we have, in a quantitative way. It helps incorporate conditional probabilities into our conclusions.

Elvis Presley had a twin brother who died at birth. What is the probability that Elvis was an identical twin? Assume we observe the following probabilities in the population: fraternal twin is 1/125 and identical twin is 1/300.

**Bayes Theorem:**
$$
\mathbf{P(H|D)} = \frac{P(H) P(D|H)}{P(D)}
$$
**P(H)** = The probability of the hypotheses before we see the data, called the prior probability; **prior**

**P(H|D)** = What we are trying to figure out.  The probabilty of th hypothesis after we see the data; **posterior**

**P(D|H)** = the probabilty of the data under the hypothesis; **likelihood**

**P(D)**  = the probability of the data under any hypothesis; **Normalizing Constant**

Elvis and his dead twin brother:

P(H|D) = probability elvis was an identical twin, given that D happened being he had a brother

P(D) = the probability of having a twin that is also male - so conjoining fraternal and identical probabilities 
$$
P(Boy|Fraternal) = 1/2*1/2 * 1/125
$$

$$
P(Boy|Identical) = 1/2 * 1/300
$$

$$
P(D)= P(Boy|Fraternal) + P(Boy|Identical)
$$

P(H) = probability of an identical twin
$$
P(H) = 1/300
$$
P(D|H) = probability of of a twin that is make, given that it was identical
$$
P(D|H) = 1/2
$$

$$
P(H|D) = \frac{1/2 * 1/300}{1/4 * 1/125 + 1/2 * 1/300} = 5/11
$$



