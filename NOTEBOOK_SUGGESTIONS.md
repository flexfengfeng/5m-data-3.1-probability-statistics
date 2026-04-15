# Notebook Improvement Suggestions — 3.1 Probability and Statistics

These are suggested additions to the three existing lesson notebooks. The goal is to make them more self-study friendly — richer context, clearer comments, and active moments where the learner does something before seeing the answer.

All suggestions are additive. No existing code cells need to be removed or restructured.

---

## Part_1_probability_statistics_lesson.ipynb

### Add at the top (new markdown cell, before any code)

```markdown
## Part 1: Foundations of Probability

**Real-world scenario for this notebook:**
You are a data analyst at a streaming platform (think Spotify or Netflix).
Your team wants to understand listening behaviour — how long do users listen,
how spread out are their sessions, and are there unusual patterns worth flagging?

As you work through this notebook, keep asking: *how would this apply to
understanding our users' data?*
```

### Before the mean/median code cell — add a "Pause and Think" cell

```markdown
### ⏸️ Pause and Think

Before running the next cell, look at the dataset below and make a prediction:
- Will the mean or median be higher? Why?
- If one very large value were added to the dataset, which measure would change more?

Write your predictions in this cell before running the code.
```

### Improve inline comments throughout

Current style (terse):
```python
# calculate mean
np.mean(data)
```

Suggested style (explanatory):
```python
# Calculate the mean — this adds up all values and divides by the count.
# It gives the "centre of mass" of the data, but is sensitive to extreme values (outliers).
np.mean(data)
```

### Add a "Try It Yourself" cell at the end of the central tendency section

```python
# ── TRY IT YOURSELF ──────────────────────────────────────────────
# A real-estate analyst has the following house prices (in $1000s):
# [320, 345, 290, 310, 330, 2100]
#
# 1. Calculate the mean and median
# 2. Which is more representative of a "typical" house price?
# 3. What happens to both values if you remove the 2100 outlier?

house_prices = [320, 345, 290, 310, 330, 2100]

# Your code here:

# ─────────────────────────────────────────────────────────────────
```

### Add a summary cell at the end of Part 1

```markdown
## Part 1 Summary

In this section you covered:
- **Mean vs Median**: Mean is sensitive to outliers; median is more robust.
  Use median when your data has extreme values.
- **Standard deviation**: Measures how spread out data is around the mean.
  Low std = tightly clustered; high std = widely spread.
- **Correlation**: Ranges from -1 to +1. Strong positive = both go up together.
  Strong negative = one goes up as the other goes down. Near zero = no relationship.

**Coming up in Part 2:** We'll look at the *shape* of data — not just its centre
and spread, but whether it follows recognisable patterns (distributions).
```

---

## Part_2_probability_statistics_lesson.ipynb

### Add at the top (new markdown cell)

```markdown
## Part 2: Probability Distributions

**Real-world scenario for this notebook:**
You manage quality control at a food manufacturing company.
Products that are too light get customer complaints; products that are too heavy
cut into margins. You need to understand what "normal" variation looks like
so you can flag genuinely unusual items.

As you work through this notebook, think about: *what would each distribution
look like for product weights, and what would each shape mean for quality control?*
```

### Before the distribution plots — add a "Pause and Think" cell

```markdown
### ⏸️ Pause and Think

You are about to see three distributions plotted: Uniform, Normal, and Skewed.
Before running the cell, sketch (or describe in words) what you expect each to look like.

- **Uniform**: ?
- **Normal**: ?
- **Skewed**: ?

After running, compare your sketch to the actual plots.
```

### Improve comments on the CLT demonstration

Current (if terse):
```python
# sample means
sample_means = [np.mean(np.random.choice(data, size=30)) for _ in range(1000)]
```

Suggested:
```python
# Central Limit Theorem demonstration:
# We take 1000 random samples of 30 data points each, and calculate the mean of each sample.
# Even if the original data (above) is not normally distributed,
# the distribution of these 1000 *sample means* should form a bell curve.
sample_means = [np.mean(np.random.choice(data, size=30)) for _ in range(1000)]
```

### Add a "Try It Yourself" cell after CLT demonstration

```python
# ── TRY IT YOURSELF ──────────────────────────────────────────────
# The CLT says sample means follow a normal distribution regardless of the
# original data shape. Let's test this with a highly skewed distribution.
#
# 1. Generate 10,000 values from an exponential distribution (highly right-skewed):
#    skewed_data = np.random.exponential(scale=2, size=10000)
#
# 2. Plot the original distribution — confirm it is skewed
#
# 3. Take 1000 samples of size 50 each, calculate each sample mean,
#    and plot the distribution of those sample means
#
# 4. Does it look more normal than the original? What does that tell you?

# Your code here:

# ─────────────────────────────────────────────────────────────────
```

### Add a summary cell at the end of Part 2

```markdown
## Part 2 Summary

Key takeaways:
- **Normal distribution**: Bell-shaped, symmetric, most ML algorithms assume this.
  Real-world examples: heights, measurement errors, exam scores.
- **Skewed distributions**: Asymmetric. Right-skewed means a long tail to the right
  (e.g. incomes, social media followers). Left-skewed is the reverse.
- **Central Limit Theorem**: Sample means tend toward a normal distribution
  regardless of the underlying data shape. This is why statistical methods work
  on messy real-world data.

**Coming up in Part 3:** We'll use these foundations to test whether differences
we observe in data are real or just chance.
```

---

## Part_3_probability_statistics_lesson.ipynb

### Add at the top (new markdown cell)

```markdown
## Part 3: Statistical Inference and Hypothesis Testing

**Real-world scenario for this notebook:**
You are a product analyst at a subscription app. The team ran an A/B test:
half the users saw a new onboarding flow (Group B), the other half saw the old one (Group A).
After 30 days, Group B shows a higher retention rate.

The CEO asks: "Is this real, or did we just get lucky this month?"

Hypothesis testing is how you answer that question rigorously.
```

### Before the hypothesis test code — add a "Pause and Think" cell

```markdown
### ⏸️ Pause and Think

Before running the t-test, form a hypothesis:
- **Null hypothesis (H₀)**: The two groups are the same — any difference is random chance
- **Alternative hypothesis (H₁)**: The two groups are genuinely different

Based on the data you've seen so far, what do you *expect* the p-value to be?
- Less than 0.05? (suggesting a real difference)
- Greater than 0.05? (suggesting we can't rule out chance)

Write your expectation here, then run the cell to find out.
```

### Improve z-score comments

Suggested:
```python
# Z-score: how many standard deviations is this value from the mean?
# Formula: z = (value - mean) / standard_deviation
#
# Rule of thumb:
#   |z| > 2 → unusual (only ~5% of values in a normal distribution)
#   |z| > 3 → very unusual (only ~0.3% of values)
#   This makes z-scores useful for anomaly detection.
z_score = (value - mean) / std
```

### Add a "Try It Yourself" cell after hypothesis testing

```python
# ── TRY IT YOURSELF ──────────────────────────────────────────────
# A coffee shop tests two layouts for their menu board.
# They track the average spend per customer for 60 days on each layout.
#
# Layout A (current): mean=$8.20, std=$2.10, n=60 days
# Layout B (new):     mean=$9.10, std=$2.30, n=60 days
#
# 1. Generate synthetic data for both layouts using np.random.normal()
# 2. Run a t-test to determine if Layout B significantly increases spend
# 3. What is your recommendation to the shop owner?

import numpy as np
from scipy import stats

# Your code here:

# ─────────────────────────────────────────────────────────────────
```

### Add a final summary cell

```markdown
## Module 3.1 Summary

You have now covered the statistical foundations that underpin all of machine learning.

**The big ideas:**
- **Descriptive statistics** (mean, median, std, correlation) help you understand what your data looks like before you model it
- **Probability distributions** describe the shape of your data — knowing the shape helps you choose the right model and preprocessing steps
- **Hypothesis testing** lets you distinguish real patterns from random noise — essential whenever you're comparing a before vs after, or testing whether a model improvement is genuine

**What's next:** In Module 3.2 you'll use these foundations to understand how machine learning algorithms actually learn from data — and why they sometimes fail.

---
*Before moving on: complete the practice notebook, then attempt the assignment.*
```
