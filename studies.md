# Self Study — 3.1 Probability and Statistics

**Estimated time:** 60 minutes  
**Complete this before the lesson session.**

This is a flipped-classroom preparation guide. Your goal is not to memorise everything — it is to arrive at the session having seen the concepts once so the hands-on time feels like reinforcement, not a first encounter.

For each task: watch the video, preview the notebook section, attempt the mini-exercise, then check the sample answer. The act of trying before looking is what makes the learning stick.

---

## Task 1: Foundations of Probability (20 min)

### Real-World Scenario

You work in the marketing team at an e-commerce company. Your manager asks: "Do customers who receive our Tuesday newsletter spend more on average than those who don't?" Before you can answer that, you need to understand your data — are there outliers distorting the average? Are the two groups really different, or could it be random variation? That is the work of probability and statistics.

### What to Do

1. Watch the video below (10 min)

[![The Statistics of Uncertainty](https://img.youtube.com/vi/u2Hgz9jtOHc/default.jpg)](https://youtu.be/u2Hgz9jtOHc)

2. Open `notebooks/Part_1_probability_statistics_lesson.ipynb` — read through the markdown cells and glance at the code without running it yet. Focus on the Law of Large Numbers, mean, median, and mode sections. You don't need to understand every line — just follow the story and notice how `np.random.binomial` simulates experiments and how the sample mean changes as the number of flips grows.

### Mini-Exercise 1A: Spot the Outlier Effect

Without running any code, look at these two datasets:

```
Dataset A: [50, 52, 48, 51, 49, 53, 50]
Dataset B: [50, 52, 48, 51, 49, 53, 980]
```

**Question:** Estimate (don't calculate) how the mean and median will differ between Dataset A and Dataset B. Which measure is more useful for describing "typical" values in Dataset B, and why?

*Write your answer before reading the sample answer.*

> **Sample answer:** Dataset A: mean ≈ 50.4, median = 50 — very similar, no outlier distortion. Dataset B: the 980 drags the mean up to roughly 190, while the median stays around 50. The median is far more useful for Dataset B because it is resistant to that extreme value. The mean would give a completely misleading picture of what a "typical" value looks like.

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
> - Ice cream sales vs drowning incidents → **weak to moderate positive** (both driven by summer heat, not each other — a classic spurious correlation)
> - Age of a car vs resale value → **strong negative** (older car, lower value)
> - Shoe size vs IQ → **near zero** (no meaningful relationship)

### Guiding Questions

- In the coin flip simulation, why does the proportion of heads appear "jittery" with small sample sizes but flatten toward 50% as the number of flips grows?
- Why might we prefer the median over the mean when analysing a dataset with extreme outliers?

---

## Task 2: Probability Distributions (20 min)

### Real-World Scenario

You are a data analyst at a hospital. You have been asked to flag patient wait times that are "unusually long." To do that, you need to know what "normal" looks like — the shape of the distribution — so you can identify when a value is genuinely far outside the norm.

### What to Do

1. Watch the video below (10 min)

[![The Central Limit Theorem](https://img.youtube.com/vi/ITs5zp1Xv2w/default.jpg)](https://youtu.be/ITs5zp1Xv2w)

2. Open `notebooks/Part_2_probability_statistics_lesson.ipynb` — read the markdown cells and look at the distribution plots without running anything yet. Focus on how the shape of Uniform, Normal, and Skewed distributions differ visually. You don't need to understand the plotting code — just build a mental picture of what each shape looks like.

### Mini-Exercise 2A: Distribution Matching

Match each real-world variable to the distribution that best describes it (Normal / Right-skewed / Left-skewed / Uniform):

| Variable | Distribution |
|---|---|
| Heights of adult men in a country | |
| Number of social media followers per account | |
| Score on a very easy exam (most people score high) | |
| A random number generator producing values 1–100 | |

> **Sample answers:**
> - Heights → **Normal** (bell curve, most cluster around average)
> - Social media followers → **Right-skewed** (most have few followers; a tiny number have millions)
> - Easy exam scores → **Left-skewed** (most cluster near the top; few score low)
> - Random number generator → **Uniform** (every value equally likely)

### Mini-Exercise 2B: Central Limit Theorem in Plain English

Imagine you sample 5 people's daily step counts from a fitness app, record the average, then repeat this 1,000 times and plot all 1,000 averages.

**Question:** What shape would you expect that plot to have, even if individual daily step counts are not normally distributed? Why?

*Write your answer before reading the sample answer.*

> **Sample answer:** You would expect a normal (bell curve) shape. This is the Central Limit Theorem — regardless of the shape of the original distribution, the distribution of sample means approaches normal as the number of samples grows. This is why so many statistical techniques that assume normality still work in practice on messy real-world data.

### Guiding Questions

- Why is the normal distribution the default assumption for noise in many machine learning models?
- What happens to the shape of the distribution of sample means as sample size increases from 5 to 30 to 100? Why is this powerful for data science?

---

## Task 3: Statistical Inference and Hypothesis Testing (20 min)

### Real-World Scenario

You are a product analyst at a tech startup. The engineering team just deployed a new homepage design. After two weeks, conversion rates look slightly higher than before. Your CEO asks: "Is this improvement real, or could it just be a good two weeks?" Hypothesis testing is how you answer that question rigorously.

### What to Do

1. Watch the video below (10 min)

[![Statistical Testing](https://img.youtube.com/vi/Uos-xeDAvqA/default.jpg)](https://youtu.be/Uos-xeDAvqA)

2. Open `notebooks/Part_3_probability_statistics_lesson.ipynb` — read the markdown cells without running anything yet. Focus on the logic flow of the hypothesis test: null hypothesis → test statistic → p-value → conclusion. You don't need to memorise formulas — just understand the reasoning behind each step.

### Mini-Exercise 3A: Interpret These Results

A data scientist tests whether a new email subject line generates more opens than the old one. She runs a t-test and gets:

```
t-statistic: 2.34
p-value:     0.021
```

**Questions:**
1. Is this result statistically significant at the 0.05 threshold?
2. What would you recommend the team do?
3. If the p-value were 0.43 instead, what would change?

> **Sample answers:**
> 1. Yes — 0.021 < 0.05, so the result is statistically significant.
> 2. Roll out the new subject line — the data provides sufficient evidence that it genuinely performs better.
> 3. With p = 0.43, we would fail to reject the null hypothesis. The improvement could easily be explained by random variation. Recommendation: do not change yet; collect more data or test a different subject line.

### Mini-Exercise 3B: Z-Score Interpretation

A factory's product weights have a mean of 500g and a standard deviation of 10g. A quality control check finds an item weighing 535g.

**Question:** Calculate the z-score for this item. Should the factory flag it for inspection?

*Formula: z = (value − mean) / standard deviation*

> **Sample answer:**
> z = (535 − 500) / 10 = **3.5**
> A z-score of 3.5 means this item is 3.5 standard deviations above the mean. Only about 0.02% of values in a normal distribution fall this far out. Yes — flag it. It is extremely unlikely to be within normal variation and likely indicates a manufacturing defect or measurement error.

### Guiding Questions

- If a data point has a z-score of +2.5, what does that tell you about its relationship to the average? How might this help detect anomalies?
- When comparing two groups with a t-test, what does a p-value lower than 0.05 tell you about the difference between those groups?

---

## Active Engagement Tips

To deepen your retention, try one of these during your preview read:

- **Visualisation prediction:** When you see a cell that generates a plot, try to sketch the shape you expect before you look at the output. You'll run the code in class — this builds anticipation and makes the result more memorable.
- **Real-world connection:** As you read each concept, think of a dataset from your own work or life. Is it likely normally distributed or skewed? What would a z-score outlier mean in that context?
- **Code commentary** *(do this during class when the notebooks are running):* Pick a code block using `np.random` or `scipy.stats` and write a comment in your own words explaining what each parameter (`loc`, `scale`, `size`) controls. If you can explain it, you understand it.

---

## Bring to the Session

Come ready to discuss:
1. One concept that didn't fully click — the session will address it
2. Your answer to Mini-Exercise 3A — the class will compare approaches
3. One real-world example from your own work or life where you have seen probability or statistics applied (consciously or not)
