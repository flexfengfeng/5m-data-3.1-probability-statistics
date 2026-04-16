# Lesson — 3.1 Probability and Statistics for Machine Learning

Use this document as your concept reference — before, during, and after the session. Each section explains a key idea in plain English, anchors it to a real-world scenario, and shows why it matters for machine learning. Run the matching notebook alongside each section to see the concepts in action.

| Section | Notebook | Time |
|---|---|---|
| Part 1: Law of Large Numbers & Central Tendency | `notebooks/Part_1_probability_statistics_lesson.ipynb` | ~30 min |
| Part 2: Probability Distributions & CLT | `notebooks/Part_2_probability_statistics_lesson.ipynb` | ~30 min |
| Part 3: Hypothesis Testing & Inference | `notebooks/Part_3_probability_statistics_lesson.ipynb` | ~30 min |

---

## Why Probability and Statistics Matter for Machine Learning

A machine learning model learns patterns from data. But not every pattern in data is real — some are just noise, random fluctuations, or coincidences. Before you can trust a model, you need tools to answer two questions:

1. **Is this pattern real, or did I get lucky?**
2. **How confident can I be in this result?**

Probability and statistics are exactly those tools. Every ML algorithm you will use in this course — from linear regression to neural networks — is built on the concepts in this lesson. Skipping them is like trying to build a house without understanding what a foundation is.

---

## Part 1: Law of Large Numbers & Central Tendency

### 1.1 The Law of Large Numbers

**The idea:** The more data you collect, the closer your observed result gets to the true underlying probability.

**Real-world analogy:** Imagine you are a doctor testing a new blood pressure drug. In your first trial you test it on 10 patients and see a 40% improvement rate. Should you be excited? Not yet. With only 10 patients, random variation is enormous — you might have happened to enrol 10 unusually healthy people. Run the trial on 10,000 patients and the noise averages out, leaving only the true signal. That is the Law of Large Numbers at work.

**Why it matters for ML:** This is why data scientists always want more data. A model trained on 100 examples might be picking up noise. The same model trained on 100,000 examples is far more likely to have learned a genuine pattern. It is also why A/B tests require minimum sample sizes before results can be trusted.

> **Rule of thumb:** Most A/B testing platforms require at least 1,000 users per variant before considering a result reliable.

---

### 1.2 Mean, Median, and Mode

These are three ways of describing the "centre" of a dataset. They tell you different things and are useful in different situations.

#### Mean — the average

**The idea:** Add all values together and divide by the count.

**Real-world analogy:** If five employees earn $40k, $45k, $50k, $55k, and $500k per year, the mean salary is $138k. No one in the company actually earns anywhere near $138k. The one executive at $500k has dragged the mean far above what is typical.

**When to use it:** The mean is most useful when your data is roughly symmetric — no extreme outliers. It is the most mathematically powerful measure of centre, so it is used in most statistical calculations.

#### Median — the middle value

**The idea:** Sort all values and pick the one in the middle. Half the values are above it, half are below.

**Using the same example:** Sorted salaries are $40k, $45k, **$50k**, $55k, $500k. The median is $50k — a much more honest picture of the typical employee's pay.

**When to use it:** Whenever your data has outliers that would distort the mean. This is why house prices and salaries are almost always reported as medians, not means. A handful of mansions or executive pay packets should not define "typical."

#### Mode — the most common value

**The idea:** The value that appears most frequently in the dataset.

**Real-world analogy:** A shoe shop analysing sales to decide which sizes to stock most heavily does not care about the average shoe size — they care about the most *common* shoe size. That is the mode.

**When to use it:** Categorical data, or when you want to know the most typical outcome rather than the mathematical average.

#### When do they diverge?

For a symmetric distribution (like heights of adults) the mean, median, and mode are nearly identical. They diverge when data is **skewed**:

- **Right-skewed** (long tail to the right): mean > median. Examples: income, house prices, website session lengths.
- **Left-skewed** (long tail to the left): mean < median. Examples: age at retirement, scores on an easy exam.

In right-skewed data, the median is almost always the more honest description of "typical."

---

### Quick Check — Part 1

**Q1:** A company reports that the average salary of its 200 employees is $95,000. When you look more closely, you find the median salary is $58,000. What does this tell you about the salary distribution, and which number is more useful for a job seeker?

> **Sample answer:** The distribution is right-skewed — a small number of very high earners (likely senior executives) are pulling the mean far above what most employees earn. The median of $58,000 is far more useful for a job seeker, as it represents what a typical employee actually takes home.

**Q2:** Two investment portfolios have the same mean annual return of 10%. Portfolio A has a standard deviation of 2%; Portfolio B has a standard deviation of 18%. What does standard deviation tell you here, and which portfolio is "safer"?

> **Sample answer:** Standard deviation measures how spread out the returns are around the mean. Portfolio A is much safer — its returns are tightly clustered around 10%, varying by roughly 2% in either direction. Portfolio B's returns swing wildly (could be +28% one year, -8% the next), even though the long-run average is the same. Same mean, very different experience.

**Q3:** Why does the Law of Large Numbers matter for A/B testing? What could go wrong if you stop a test too early?

> **Sample answer:** Early in a test, random variation dominates — the group that happens to be doing better might just have got lucky. The Law of Large Numbers says you need enough samples for the noise to average out and the true difference (if any) to emerge. Stopping too early risks making decisions based on random fluctuation rather than a genuine effect — a very common and costly mistake in product and marketing teams.

---

## Part 2: Probability Distributions & the Central Limit Theorem

### 2.1 What is a Probability Distribution?

**The idea:** A probability distribution describes all the possible values a variable can take, and how likely each one is. Think of it as a map of uncertainty — it tells you where the "heavy" outcomes are and how thinly the possibilities spread out at the edges.

**Real-world analogy:** Before you arrive at a train station, your uncertainty about the next train's arrival is a distribution. If trains run every 10 minutes, you might wait anywhere from 0 to 10 minutes — roughly equally likely (uniform distribution). If trains run on a schedule but are occasionally delayed, the distribution clusters around on-time with a tail of late arrivals (roughly normal).

---

### 2.2 Uniform Distribution

**The idea:** Every possible outcome is equally likely.

**Real-world example:** Rolling a fair six-sided die. Each face — 1 through 6 — has exactly a 1-in-6 chance of appearing. A random number generator producing integers between 1 and 100 follows a uniform distribution.

**When you see it in ML:** Initialising model weights randomly before training. Generating synthetic test data. Random train/test splits.

**The key feature:** It has no "centre" that is more likely than the edges. Flat histogram.

---

### 2.3 Normal (Gaussian) Distribution

**The idea:** Values cluster symmetrically around a central mean, with fewer and fewer values the further you move from the centre. The famous bell curve.

**Real-world examples:** Heights of adults. Blood pressure readings. Measurement errors in a manufacturing process. Daily temperature fluctuations.

**Why it appears everywhere:** The normal distribution emerges naturally whenever a measurement is the sum of many small independent random effects. Height, for instance, is influenced by hundreds of genes, each contributing a tiny amount — their combined effect produces a bell curve.

**The 68–95–99.7 Rule** (useful to memorise):
- 68% of values fall within 1 standard deviation of the mean
- 95% of values fall within 2 standard deviations
- 99.7% of values fall within 3 standard deviations

**Practical use:** If you know a dataset is normally distributed, you immediately know that a value 3 standard deviations from the mean is extremely unusual — only 0.3% of values are that extreme. This is the foundation of anomaly detection.

**When you see it in ML:** Residuals from a linear regression model should be normally distributed. Many statistical tests assume normality. The output of a well-trained classifier often approximates a normal distribution.

---

### 2.4 Skewed Distributions

**The idea:** When the bell curve leans to one side — the distribution has a longer tail on the left or right.

**Right-skewed (positive skew) — the most common in business data:**
- Long tail extends to the right
- Mean > Median
- Examples: income, transaction amounts, number of app sessions, bug counts in software releases

**Left-skewed (negative skew):**
- Long tail extends to the left
- Mean < Median
- Examples: age at which professional athletes retire, scores on a very easy exam

**Why it matters for ML:** Many algorithms assume roughly normal data. Feeding them heavily skewed data without transformation can degrade performance. Recognising skew is the first step toward deciding whether to apply a log transform, use the median, or choose a model that handles skew natively.

---

### 2.5 Central Limit Theorem (CLT)

**The idea:** Even if the underlying data is not normally distributed, the *average* of many samples drawn from that data will follow a normal distribution — as long as the sample size is large enough (typically n ≥ 30).

**Real-world analogy:** Imagine a call centre where call durations are heavily right-skewed — most calls are short, but a few complaints run very long. If you take the *average call duration* each day across 50 calls, those daily averages will form a nice bell curve, even though the individual calls do not. The extremes cancel each other out in the average.

**Why it is the most important theorem in statistics for ML:**
- It means statistical tests that assume normality (t-tests, confidence intervals) are valid even on messy real-world data, as long as you are working with means or sums of enough observations.
- It explains why ensemble models (Random Forest, Gradient Boosting) often outperform single models — averaging many imperfect predictions cancels out individual errors.
- It is the reason cross-validation works: averaging performance across multiple folds gives a reliable estimate of true model performance.

---

### Quick Check — Part 2

**Q1:** A data scientist finds that 99.9% of credit card transactions are legitimate and 0.1% are fraudulent. What type of distribution does this represent, and why is it a problem for training a classifier?

> **Sample answer:** This is a heavily right-skewed (imbalanced) distribution. The problem is that a model that predicts "not fraud" for every single transaction would achieve 99.9% accuracy — but it would be completely useless. The model would never learn to detect the rare event it actually needs to catch. Special techniques are needed: oversampling the minority class, undersampling the majority, adjusting class weights, or using metrics like precision/recall instead of accuracy.

**Q2:** A manufacturing plant measures the diameter of 10,000 ball bearings and finds the data is perfectly normally distributed with mean 10mm and standard deviation 0.1mm. What percentage of bearings fall between 9.8mm and 10.2mm?

> **Sample answer:** 9.8mm is 2 standard deviations below the mean; 10.2mm is 2 standard deviations above. By the 68–95–99.7 rule, 95% of values fall within 2 standard deviations. So approximately 9,500 out of 10,000 bearings fall in that range.

**Q3:** Why does the Central Limit Theorem matter for cross-validation in machine learning?

> **Sample answer:** When you run k-fold cross-validation, you train and evaluate your model k times, getting k separate performance scores. By the CLT, the average of those k scores is normally distributed — even if individual fold results are noisy. This makes it valid to compute a mean accuracy and confidence interval, and to use standard statistical tests to compare two models. Without the CLT, you could not trust that the average fairly represents true model performance.

---

## Part 3: Statistical Inference & Hypothesis Testing

### 3.1 Z-Scores — Measuring How Unusual a Value Is

**The idea:** A z-score tells you how many standard deviations a value sits from the mean of its distribution. It converts any measurement onto a common scale, making comparisons possible.

**Formula:** z = (value − mean) / standard deviation

**Real-world analogy:** A student scores 85 on a maths exam. Is that good? It depends entirely on how everyone else did. If the class average is 70 with a standard deviation of 10, then 85 is 1.5 standard deviations above the mean — a strong result. If the class average is 80 with a standard deviation of 3, then 85 is 1.67 standard deviations above — an equally good result in a much harder context. The z-score lets you compare across different scales.

**Quick interpretation guide:**

| Z-score | What it means |
|---|---|
| 0 | Exactly at the mean |
| ±1 | Within the typical range (68% of data) |
| ±2 | Somewhat unusual (only 5% of data is further out) |
| ±3 | Very unusual (only 0.3% of data is this extreme) |
| > ±3 | Potential anomaly — worth investigating |

**Why it matters for ML:** Z-scores are the basis of anomaly detection, outlier removal, and feature scaling. Many ML algorithms (k-nearest neighbours, support vector machines, neural networks) are sensitive to the scale of input features. Standardising features to have a mean of 0 and standard deviation of 1 — which is exactly what z-score normalisation does — ensures no single feature dominates just because it happens to be measured in larger units.

---

### 3.2 P-Values and Statistical Significance

**The idea:** A p-value answers the question: *"If there were actually no real effect, how likely is it that I would see data this extreme just by chance?"*

A small p-value means: this result would be very unlikely if nothing were happening. That is evidence something is actually happening.

**Real-world analogy:** Imagine you suspect a coin is biased toward heads. You flip it 20 times and get 16 heads. The p-value asks: if the coin were fair, what is the probability of getting 16 or more heads in 20 flips? If that probability is very small (say 0.005), you have good evidence the coin is not fair. If the probability is 0.3 (meaning a fair coin would produce this result 30% of the time), you have no reason to suspect bias.

**The significance threshold (α = 0.05):** By convention, a p-value below 0.05 is called "statistically significant." This means you are willing to accept a 5% chance of being wrong when you conclude an effect is real.

**Common misinterpretations to avoid:**
- A p-value is NOT the probability that your hypothesis is true
- A p-value is NOT the probability that the result happened by chance
- A statistically significant result can still be practically unimportant (a tiny effect can be significant with a large enough sample)

---

### 3.3 Hypothesis Testing — The Full Workflow

Hypothesis testing is how you make data-driven decisions with confidence. The four steps are always the same:

**Step 1 — State the null hypothesis (H₀)**
The null hypothesis is the "boring" default: no effect, no difference, nothing interesting happening.
*Example: "The new checkout button colour has no effect on conversion rate."*

**Step 2 — State the alternative hypothesis (H₁)**
This is what you are trying to show — that something real is happening.
*Example: "The green button has a higher conversion rate than the red button."*

**Step 3 — Run the test and calculate the p-value**
Choose the appropriate test (t-test for comparing two means, chi-square for categorical data, etc.), run it on your data, and get a p-value.

**Step 4 — Make a decision**
- If p < 0.05: reject H₀ — the evidence is strong enough to conclude the effect is real
- If p ≥ 0.05: fail to reject H₀ — the evidence is not strong enough; you need more data or a larger effect

**Real-world example — A/B test on an email campaign:**

> A marketing team changes the subject line of their weekly email. The old subject line gets a 22% open rate. The new subject line gets a 28% open rate across 1,000 test recipients. Is this a real improvement or random variation?
>
> H₀: The new subject line has no effect on open rate.
> H₁: The new subject line increases the open rate.
>
> Running a t-test gives p = 0.003. Since 0.003 < 0.05, we reject H₀ and conclude the new subject line is genuinely better. The team rolls it out to the full list.

---

### 3.4 T-Tests — Comparing Two Groups

**The idea:** A t-test asks whether the means of two groups are different enough that the difference is unlikely to be random chance.

**When to use it:** You have two groups (treatment vs control, before vs after, Group A vs Group B) and you want to know if their averages differ in a meaningful way.

**Real-world example:** A hospital tests a new physiotherapy protocol. After 8 weeks, the average pain score in the treatment group is 3.2 (out of 10) and in the control group is 5.1. A t-test on the two groups returns p = 0.02. Since p < 0.05, the hospital concludes the new protocol genuinely reduces pain — the difference is not just random variation between the groups.

**One-sample vs independent samples:**
- **One-sample t-test:** Compare a group's mean to a known value (e.g., "is our average delivery time significantly different from the industry benchmark of 3 days?")
- **Independent samples t-test:** Compare the means of two separate groups (e.g., "do app users and web users have different average order values?")

---

### Quick Check — Part 3

**Q1:** A clinical trial for a new painkiller returns a p-value of 0.04. A second trial of a different drug returns p = 0.001. Both are "statistically significant." What does the difference in p-values tell you?

> **Sample answer:** Both results are statistically significant (below the 0.05 threshold), meaning both drugs show effects unlikely to be due to chance. However, p = 0.001 represents much stronger evidence than p = 0.04. With p = 0.001, there is only a 0.1% chance of seeing data this extreme if the drug had no effect, versus a 4% chance for the first drug. The second trial's evidence is about 40 times stronger.

**Q2:** A data scientist is monitoring a fleet of IoT temperature sensors. One sensor returns a z-score of −4.2. What action should be taken and why?

> **Sample answer:** A z-score of −4.2 means this sensor reading is 4.2 standard deviations below the mean — an extreme outlier. Only 0.001% of readings would naturally fall this far from the mean. This is almost certainly an anomaly. The data scientist should flag it for investigation: the sensor may be malfunctioning, a physical fault may have occurred, or the environment being monitored may have experienced an unusual event. Before feeding data to any ML model, this type of outlier needs to be investigated and handled.

**Q3:** What is the risk of running many hypothesis tests on the same dataset (known as the "multiple comparisons problem")?

> **Sample answer:** Every time you run a hypothesis test with α = 0.05, there is a 5% chance of a false positive — concluding an effect is real when it is not. If you run 20 tests, you would expect about one false positive just by chance. This is a common trap in data analysis: testing every possible combination of variables until something looks significant. The fix is to either correct the significance threshold (Bonferroni correction divides α by the number of tests) or, better, to define your hypotheses before looking at the data.

---

## Putting It All Together

These three areas — central tendency, distributions, and hypothesis testing — are not separate topics. They form a single workflow that data scientists use every day:

1. **Describe your data** (Part 1): What is the mean, median? Is it skewed? Are there outliers?
2. **Understand its shape** (Part 2): What distribution does it follow? Are the assumptions of your model met?
3. **Test your conclusions** (Part 3): Is the pattern you see real, or could it be chance?

A machine learning model that skips these steps is flying blind. A data scientist who understands them can interpret model outputs, diagnose failures, and communicate findings to non-technical stakeholders — which is ultimately what separates useful analysis from code that merely runs.
