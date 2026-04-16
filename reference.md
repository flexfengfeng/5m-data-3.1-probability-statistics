# Reference — 3.1 Probability and Statistics

---

## Further Reading and Watching

Use these after completing the lesson if you want to go deeper on any topic. Start with the free resources — the books are for when you want rigorous depth.

### Free — Videos

**StatQuest with Josh Starmer** (YouTube)
The best plain-English statistics channel on the internet. Each video is one focused concept, explained with hand-drawn diagrams.
- [Statistics Fundamentals playlist](https://www.youtube.com/playlist?list=PLblh5JKOoLUK0FLuzwntyYI10UQFUhsY9)
- Recommended videos: "Normal Distribution", "The Central Limit Theorem", "P-values: What they are and how to interpret them", "Hypothesis Testing and the Null Hypothesis"

**3Blue1Brown — Probability (YouTube)**
Visually stunning explanations that build deep intuition. Slower-paced and more conceptual than StatQuest.
- [Binomial distribution](https://www.youtube.com/watch?v=8idr1WZ1A7Q)
- [Why pi is in the normal distribution](https://www.youtube.com/watch?v=cy8r7WSuT1I) — fascinating if you want to understand *why* the bell curve has the shape it does

### Free — Interactive

**Khan Academy — Statistics and Probability**
Well-structured, self-paced, with practice problems. Good for filling in gaps or reviewing concepts you want more repetition on.
- https://www.khanacademy.org/math/statistics-probability

**Kaggle — Intro to Machine Learning (free micro-course)**
Short, practical, and free. Gets you applying statistics to real datasets quickly.
- https://www.kaggle.com/learn/intro-to-machine-learning

**Seeing Theory (Brown University)**
Beautiful interactive visualisations of probability and statistics concepts — distributions, hypothesis testing, regression — all explorable in the browser.
- https://seeing-theory.brown.edu

### Free — Reading

**Towards Data Science — Statistics for Data Science**
Practical articles written by practitioners. Search for specific topics (e.g. "p-value", "CLT", "z-score") to find focused explanations.
- https://towardsdatascience.com

### Books (when you want depth)

**Practical Statistics for Data Scientists** — Bruce, Bruce & Gedeck
The most practical statistics book for people who work in data. Covers exactly what's in this module and more, with Python and R examples.
- https://www.amazon.com.au/Practical-Statistics-Data-Scientists-2e/dp/149207294X

**The Book of Why** — Judea Pearl & Dana Mackenzie
An accessible, story-driven introduction to causality vs correlation — one of the most important distinctions in data science. Recommended once you are comfortable with the core statistics from this module.
- http://bayes.cs.ucla.edu/WHY/

**Causality** — Judea Pearl
The rigorous technical companion to *The Book of Why*. For those who want the full mathematical treatment.
- http://bayes.cs.ucla.edu/BOOK-2K/

---

## Glossary

Key terms from this module, in plain English.

**Alternative hypothesis (H₁)**
The claim you are trying to find evidence for — that something real is happening (e.g. "Version B has a higher conversion rate than Version A"). You need data to support it.

**Central Limit Theorem (CLT)**
Even if individual data values are not normally distributed, the *average* of many samples from that data will follow a normal distribution, as long as the sample size is large enough (typically n ≥ 30). This is why so many statistical methods work in practice.

**Confidence interval**
A range of values that is likely to contain the true value of a parameter. A 95% confidence interval means: if you ran the same experiment many times, 95% of those intervals would contain the true value. It is *not* a statement about a single interval's probability.

**Correlation**
A measure of how strongly two variables move together, always between −1 and +1. A correlation of +1 means they move perfectly in sync; −1 means they move in opposite directions; 0 means no linear relationship. Correlation does not imply causation.

**Covariance**
Similar to correlation but not standardised — it tells you the *direction* of the relationship between two variables but not the strength on a common scale. Correlation is covariance divided by the product of the two standard deviations.

**Distribution**
A description of all possible values a variable can take and how likely each one is. Think of it as a map of the data's shape — where the heavy concentrations are and how the tails behave.

**Hypothesis test**
A formal procedure for deciding whether the pattern observed in data is real or could plausibly be due to random chance. The four steps are: state H₀ and H₁ → collect data → calculate a test statistic → decide based on the p-value.

**Law of Large Numbers**
As the number of observations grows, the sample average converges toward the true underlying average. More data = more reliable estimates.

**Mean**
The arithmetic average — sum of all values divided by the count. Sensitive to outliers; can be misleading when data is skewed.

**Median**
The middle value when data is sorted. Half the values are above it, half below. Resistant to outliers; preferred for skewed data like income or house prices.

**Mode**
The most frequently occurring value in a dataset. Most useful for categorical data or when you need to know the most typical outcome.

**Normal distribution**
The symmetric bell-shaped distribution where most values cluster around the mean and taper off symmetrically. Described by two numbers: mean (centre) and standard deviation (spread). Many natural measurements follow this shape.

**Null hypothesis (H₀)**
The "boring" default assumption — that there is no real effect, no real difference, nothing interesting happening. A hypothesis test tries to gather enough evidence to reject this.

**Outlier**
A data point that is unusually far from the rest of the data. Can be a genuine rare event, a measurement error, or a data entry mistake. Always investigate before removing.

**P-value**
The probability of observing data at least as extreme as yours, *if the null hypothesis were true*. A small p-value (typically < 0.05) means the data would be very surprising under H₀ — evidence to reject it. Common misunderstanding: a p-value is *not* the probability that your hypothesis is true.

**Probability**
A number between 0 and 1 that measures how likely an event is. 0 = impossible; 1 = certain. A probability of 0.3 means the event happens 30% of the time in the long run.

**Right-skewed distribution**
A distribution with a long tail extending to the right — most values are low, but a few very high values stretch the distribution. The mean is pulled above the median. Examples: income, order values, social media follower counts.

**Standard deviation**
A measure of how spread out values are around the mean. A small standard deviation means values cluster tightly; a large one means they are spread widely. Denoted σ (population) or s (sample).

**Statistical significance**
A result is statistically significant when the p-value falls below the chosen threshold (usually α = 0.05), meaning it is unlikely to have occurred by chance. Note: statistical significance does not mean the effect is large or practically important.

**T-test**
A hypothesis test that compares the means of one or two groups to determine whether the difference is statistically significant. Use an independent samples t-test when comparing two separate groups (e.g. treatment vs control).

**Uniform distribution**
A distribution where every possible outcome is equally likely. Rolling a fair die follows a uniform distribution. Flat histogram with no peak.

**Z-score**
A measure of how many standard deviations a value is from the mean. Formula: z = (value − mean) / standard deviation. A z-score of 0 is exactly at the mean; ±2 is unusual (5% of data); ±3 is very unusual (0.3% of data). Used for anomaly detection and feature scaling.
