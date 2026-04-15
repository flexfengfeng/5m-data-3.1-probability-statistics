# Self Study — 3.1 Probability and Statistics

**Estimated time:** 60 minutes  
**Complete this before the lesson session.**

This is a flipped-classroom preparation guide. Your goal is not to memorise everything — it is to arrive at the lesson having seen the concepts once so the hands-on session feels like reinforcement, not a first encounter.

At the end of each task, write your answers to the reflection questions before reading the sample answers. The act of attempting the answer yourself — even if you get it wrong — is more valuable than reading the answer cold.

---

## Task 1: Foundations of Probability (20 min)

### Real-World Scenario

You work in the marketing team at an e-commerce company. Your manager asks: "Do customers who receive our Tuesday newsletter spend more on average than those who don't?" Before you can answer that, you need to understand your data. Are there outliers distorting the average? Are the two groups really different, or could it be random variation? That is the work of probability and statistics.

### What to Do

1. Watch the video linked in `reference.md` under "The Statistics of Uncertainty" (10 min)
2. Open `notebooks/Part_1_probability_statistics_lesson.ipynb` — read through it without running the code. Focus on the sections covering Law of Large Numbers, mean, median, standard deviation, and correlation.

### Mini-Exercise 1A: Spot the Outlier Effect

Without running any code, look at these two datasets:

```
Dataset A: [50, 52, 48, 51, 49, 53, 50]
Dataset B: [50, 52, 48, 51, 49, 53, 980]
```

**Question:** Estimate (don't calculate) how the mean and median will differ between Dataset A and Dataset B. Which measure is more useful for describing "typical" values in Dataset B, and why?

**Write your answer here before reading the sample answer.**

> **Sample answer:** Dataset A: mean ≈ 50.4, median = 50. Very similar — no outlier distortion.
> Dataset B: the 980 drags the mean up dramatically (to roughly 190), while the median stays around 50. The median is far more useful for Dataset B because it is resistant to that outlier. The mean would give a completely misleading picture of what a "typical" value looks like.

### Mini-Exercise 1B: Correlation Intuition

Match each pair of variables to the likely correlation type (strong positive / weak positive / near zero / strong negative):

| Variable Pair | Your Guess |
|---|---|
| Hours studied vs exam score | |
| Ice cream sales vs drowning incidents | |
| Age of a car vs its resale value | |
| Shoe size vs IQ | |

> **Sample answers:**
> - Hours studied vs exam score → **strong positive** (more study, higher score)
> - Ice cream sales vs drowning incidents → **weak to moderate positive** (both driven by summer, not each other — this is a classic spurious correlation)
> - Age of a car vs resale value → **strong negative** (older car, lower value)
> - Shoe size vs IQ → **near zero** (no meaningful relationship)

### Reflection Questions

**Q:** The Law of Large Numbers says that as sample size grows, the sample average approaches the true average. Why does this matter when training a machine learning model?

> **Sample answer:** It means a model trained on more data will have a more accurate picture of the true underlying patterns. With a small dataset, random noise in the sample can mislead the model into learning patterns that do not really exist. Larger samples make the signal more reliable relative to the noise.

---

## Task 2: Probability Distributions (20 min)

### Real-World Scenario

You are a data analyst at a hospital. You have been asked to flag patient wait times that are "unusually long." To do that, you need to know what "normal" looks like — the shape of the distribution of wait times — so you can identify when a value is far outside the norm.

### What to Do

1. Watch the video linked in `reference.md` under "The Central Limit Theorem" (10 min)
2. Open `notebooks/Part_2_probability_statistics_lesson.ipynb` — read through the sections on Uniform, Normal, and Skewed distributions. Pay attention to the seaborn visualisation code — you do not need to memorise it, but notice how the shape of each distribution looks different.

### Mini-Exercise 2A: Distribution Matching

Match each real-world variable to the distribution that best describes it (Normal / Right-skewed / Left-skewed / Uniform):

| Variable | Distribution |
|---|---|
| Heights of adult men in a country | |
| Number of social media followers per account | |
| Score on a very easy exam (most people score high) | |
| A random number generator (equally likely to produce any value 1–100) | |

> **Sample answers:**
> - Heights → **Normal** (bell curve, most cluster around average)
> - Social media followers → **Right-skewed** (most have few followers, a tiny number have millions)
> - Easy exam scores → **Left-skewed** (most cluster near the top, few score low)
> - Random number generator → **Uniform** (every value equally likely)

### Mini-Exercise 2B: Central Limit Theorem in Plain English

Imagine you sample 5 people's daily steps from a fitness app. Then you repeat this 1,000 times and plot the average of each sample.

**Question:** What shape would you expect that plot of 1,000 averages to have, even if individual daily steps are not normally distributed? Why?

**Write your answer before reading the sample answer.**

> **Sample answer:** You would expect a normal (bell curve) shape. This is the Central Limit Theorem — regardless of the shape of the original distribution, the distribution of sample means will approach normal as the number of samples grows. This is why so many statistical techniques that assume normality still work in practice.

### Reflection Questions

**Q:** Why does a machine learning practitioner need to care about whether their data is normally distributed or skewed?

> **Sample answer:** Many ML algorithms perform best when features are roughly normally distributed. Skewed features can cause algorithms to weight extreme values too heavily, or produce misleading error metrics. Knowing the distribution helps you decide when to apply transformations (like log-scaling) before training.

---

## Task 3: Statistical Inference and Hypothesis Testing (20 min)

### Real-World Scenario

You are a product analyst at a tech startup. The engineering team just deployed a new homepage design. After two weeks, conversion rates look slightly higher than before. Your CEO asks: "Is this improvement real, or could it just be a good two weeks?" Hypothesis testing is how you answer that question rigorously.

### What to Do

1. Watch the video linked in `reference.md` under "Statistical Testing" (10 min)
2. Open `notebooks/Part_3_probability_statistics_lesson.ipynb` — read through the hypothesis testing section. Focus on understanding the logic flow: null hypothesis → test statistic → p-value → conclusion. You do not need to memorise formulas.

### Mini-Exercise 3A: Interpret These Results

A data scientist tests whether a new email subject line generates more opens than the old one. She runs a t-test and gets:

```
t-statistic: 2.34
p-value: 0.021
```

**Questions:**
1. Is this result statistically significant at the 0.05 threshold?
2. What would you recommend the team do?
3. If the p-value were 0.43 instead, what would change?

> **Sample answers:**
> 1. Yes — 0.021 < 0.05, so the result is statistically significant.
> 2. Roll out the new subject line — the data provides sufficient evidence that it genuinely performs better.
> 3. With p = 0.43, we would fail to reject the null hypothesis. The improvement could easily be explained by random variation. The recommendation would be: do not change yet, collect more data or try a different subject line.

### Mini-Exercise 3B: Z-Score Interpretation

A factory's product weights have a mean of 500g and a standard deviation of 10g. A quality control check finds an item weighing 535g.

**Question:** Calculate the z-score for this item. Should the factory flag it for inspection?

*Formula: z = (value - mean) / standard deviation*

> **Sample answer:**
> z = (535 - 500) / 10 = **3.5**
> A z-score of 3.5 means this item is 3.5 standard deviations above the mean. In a normal distribution, only about 0.02% of values fall this far out. Yes — this item should absolutely be flagged. It is extremely unlikely to be within normal variation and suggests a manufacturing defect or measurement error.

### Reflection Questions

**Q:** A data scientist tells you their model has a 95% confidence interval of [2.1%, 4.7%] improvement in conversion rate. What does this mean in plain English?

> **Sample answer:** It means that if we ran this experiment many times, 95% of the time the true improvement would fall somewhere between 2.1% and 4.7%. We are fairly confident the new version is genuinely better, and the realistic size of that improvement is in that range — it's not likely to be negligible or enormous.

---

## Learning App Idea 🔨

You are building toward the end-of-module hackathon where your team creates a learning app that makes one concept from this course fun and accessible.

After today's self-study, jot down any ideas that came to mind:

- Could a coin-flip simulator that grows the sample size in real time show the Law of Large Numbers visually?
- Could a drag-and-drop game where users place data points and watch the mean vs median shift teach the outlier effect?
- Could a "p-value explainer" that takes a plain-English scenario and returns a plain-English verdict make hypothesis testing less intimidating?

No commitment needed yet — just capture the idea.

---

## Bring to the Lesson Session

Come ready to discuss:
1. One concept from your self-study that did not fully click — the session will address it
2. Your answer to Mini-Exercise 3A — the class will compare approaches
3. One real-world example from your own work or life where you have seen probability or statistics applied (consciously or not)
