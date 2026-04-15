# Lesson — 3.1 Probability and Statistics for Machine Learning

## Setup

Before you begin, follow the [Setup Guide](setup.md) to create and activate your environment. Run the smoke test to confirm everything works, then come back here.

Open the three lesson notebooks in order:
1. `notebooks/Part_1_probability_statistics_lesson.ipynb`
2. `notebooks/Part_2_probability_statistics_lesson.ipynb`
3. `notebooks/Part_3_probability_statistics_lesson.ipynb`

---

## Why This Matters

Every time Netflix decides which thumbnail to show you, it is running a probability experiment. It shows version A to some users and version B to others, counts the clicks, and picks the winner. The reason it needs *thousands* of users per test — not just ten — is the Law of Large Numbers. With ten people, random luck dominates. With ten thousand, the real signal emerges.

That is what this lesson is about. Before a machine learning model can learn anything useful from data, someone has to understand whether the patterns in that data are real or just noise. Probability and statistics are the tools that answer that question. Every ML algorithm you will use in this course is built on the foundations you learn today.

---

## Part 1: Foundations of Probability (40 min)

### What You Are Learning

Probability is a way of measuring uncertainty with a number between 0 (impossible) and 1 (certain). Statistics is the practice of drawing conclusions from data despite that uncertainty.

Before a model can find patterns, we need to describe and summarise data. That means understanding:

- **Central tendency** — where is the "middle" of the data? The mean gives you the average; the median gives you the midpoint. They differ when data is skewed (like salaries — a few very high earners pull the mean up, but the median stays representative).
- **Dispersion** — how spread out is the data? Standard deviation tells you how far values typically stray from the mean. Two datasets can have the same mean but very different shapes.
- **Correlation vs covariance** — do two variables move together? Covariance tells you the direction; correlation also tells you the strength (always between -1 and 1, making it easier to compare).

### Real-World Anchor

Think about house prices. The mean price in a neighbourhood is pulled up by a few mansions. The median is more representative of what a typical buyer pays. When a journalist says "average house prices rose 10%", ask yourself: mean or median? That question matters.

### Quick Check — Part 1

**Q1:** A dataset of 100 employees' salaries has a mean of $80,000 and a median of $62,000. What does this tell you about the distribution?

> **Sample answer:** The distribution is right-skewed — a small number of very high salaries are pulling the mean upward. The median is a more representative measure of what a typical employee earns.

**Q2:** Two investment portfolios both have an average return of 8% per year. Portfolio A has a standard deviation of 2%; Portfolio B has a standard deviation of 15%. Which is riskier and why?

> **Sample answer:** Portfolio B is riskier. The higher standard deviation means its returns vary much more wildly — it might return 23% one year and -7% the next. Portfolio A is steadier. Same average, very different experience.

**Q3:** What is the difference between correlation and causation? Give an example.

> **Sample answer:** Correlation means two variables tend to move together. Causation means one variable directly causes the other. Example: ice cream sales and drowning rates are correlated (both go up in summer) but eating ice cream does not cause drowning — summer heat causes both.

---

## Part 2: Probability Distributions (50 min)

### What You Are Learning

A probability distribution describes all the possible values a variable can take and how likely each one is. You can think of it as a map of uncertainty.

The three distributions you'll encounter most in ML:

- **Uniform distribution** — every outcome equally likely (rolling a fair die). Rare in real data, but a useful baseline.
- **Normal (Gaussian) distribution** — the famous bell curve. Height, measurement errors, test scores — many natural phenomena cluster around a mean with fewer and fewer values at the extremes. Most ML algorithms assume your data is (roughly) normally distributed.
- **Skewed distributions** — when the bell curve leans. Income, website traffic, and city sizes are all right-skewed: most values are low, but a long tail extends to the right.

**The Central Limit Theorem (CLT)** is the most important result in statistics for ML: even if your underlying data is not normally distributed, the *average* of many samples will be. This is why so many ML techniques work in practice despite messy real-world data.

### Real-World Anchor

Think about the height of 10,000 people. Most cluster around the average, with a smooth drop-off on either side — a normal distribution. Now think about annual income. A few billionaires drag the right tail out enormously — a skewed distribution. The same ML algorithm applied to both needs to be handled differently. That is why distribution awareness is a core skill.

### Quick Check — Part 2

**Q1:** A machine learning model for detecting fraudulent credit card transactions notices that 99.9% of transactions are legitimate and 0.1% are fraud. What type of distribution does this suggest, and why does it matter for training?

> **Sample answer:** This is a highly skewed (imbalanced) distribution. It matters because a model that simply predicts "not fraud" every time would be 99.9% accurate but completely useless. The skew requires special handling during training (oversampling, class weights, etc.).

**Q2:** The Central Limit Theorem says that sample means follow a normal distribution regardless of the original data's shape. Why is this useful for machine learning?

> **Sample answer:** It means we can use statistical tests and confidence intervals that assume normality even when our data isn't normally distributed, as long as we're working with averages or sums of many observations. It's why so many ML methods are robust in practice.

---

## Part 3: Statistical Inference and Hypothesis Testing (50 min)

### What You Are Learning

Hypothesis testing is how you decide whether a pattern you see in data is real or just happened by chance. The workflow is:

1. State a **null hypothesis** (H₀): "there is no effect" — the boring default
2. State an **alternative hypothesis** (H₁): "there is an effect" — what you are trying to prove
3. Calculate a **p-value**: the probability of seeing results this extreme *if the null hypothesis were true*
4. If p < 0.05 (the conventional threshold), the result is statistically significant — you reject the null hypothesis

**Z-scores** tell you how many standard deviations a value sits from the mean. A z-score of 2 means a value is unusually high; a z-score of -3 is very unusually low. This is how anomaly detection works in practice.

**T-tests** compare the means of two groups to ask: are these groups genuinely different, or could the difference be random chance?

### Real-World Anchor

Imagine you are a product manager and you run an A/B test on your website's checkout button — red vs green. After a week, the green button has a 3% higher conversion rate. Is that real, or just a lucky week? Hypothesis testing answers that question. A p-value below 0.05 means you are confident enough to ship the green button. Above 0.05 means you need more data.

### Quick Check — Part 3

**Q1:** A pharmaceutical company tests a new drug. Their p-value is 0.03. What does this mean, and what would they conclude?

> **Sample answer:** The p-value of 0.03 means there is only a 3% probability of observing results this extreme if the drug had no effect. Since 0.03 < 0.05, the result is statistically significant — they would reject the null hypothesis and conclude the drug has a real effect.

**Q2:** A data scientist has a z-score of -3.1 for a data point in a sensor reading dataset. What should they investigate?

> **Sample answer:** A z-score of -3.1 means this reading is 3.1 standard deviations below the mean — an extreme outlier. In sensor data, this could indicate equipment malfunction, a measurement error, or a genuine rare event. It is a strong signal that something unusual happened and warrants investigation.

**Q3:** What is the risk of setting your significance threshold (α) too low — say, 0.001 instead of 0.05?

> **Sample answer:** You make it much harder to detect real effects. You will miss true patterns (more false negatives / Type II errors). This is a problem in fields like medicine where failing to detect a real treatment effect has serious consequences.

---

## Hackathon Lens 🔨

You are building toward a learning app that makes one of these concepts fun and engaging for a complete beginner. After today's lesson, ask yourself:

- Could you build an interactive coin-flip or dice-roll simulator that shows the Law of Large Numbers in action?
- Could a p-value calculator with plain-English interpretation ("yes, this difference is real" / "not enough data yet") make hypothesis testing less intimidating?
- What would a "normal distribution explorer" look like where the user drags sliders to change the mean and standard deviation and watches the curve update?

Jot any ideas down — you'll come back to them.
