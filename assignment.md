# Assignment — 3.1 Probability and Statistics

**Submit your GitHub repository URL to the course portal when complete.**

---

## Context

You are a junior data analyst at a healthcare company. The analytics team has been asked to do three things:

1. Analyse a simulated trial of a new patient appointment booking process
2. Compare health metrics between two patient groups
3. Investigate correlations between clinical measurements to guide future research

Each exercise below corresponds to one of these tasks. The goal is not just to produce correct code — it is to interpret the results in plain English, as you would when presenting findings to a clinical team who do not read Python.

---

## Exercise 1: Appointment Booking Simulation

**Business question:** The new booking system randomly assigns patients one of three appointment slots (morning, afternoon, evening). After 10,000 bookings, does each slot get roughly equal share?

**Your tasks:**
1. Use `np.random.choice` to simulate 10,000 appointment bookings across three slots
2. Count the frequency of each slot and plot a bar chart showing the distribution
3. Calculate the empirical probability for each slot
4. Compare your empirical probabilities to the theoretical probability (1/3 each). Are they close? Why might they not be exactly equal?

**Interpret your results:** Write 2–3 sentences explaining what the simulation shows and why a larger sample (e.g. 100,000) would bring the empirical probabilities even closer to the theoretical ones.

---

## Exercise 2: Comparing Patient Groups

**Business question:** Two groups of patients were tracked: those who used the new app-based booking system (Group A, n=100) and those who used the old phone-based system (Group B, n=100). Group A has an average wait time of 12 minutes; Group B has an average wait time of 15 minutes. Is this difference real or just random variation?

**Your tasks:**
1. Generate two normally distributed samples representing wait times:
   - Group A: mean=12, std=4, n=100
   - Group B: mean=15, std=4, n=100
2. Plot overlapping histograms or box plots for both groups
3. Run an independent samples t-test (`scipy.stats.ttest_ind`)
4. Calculate and visualise 95% confidence intervals for both group means

**Interpret your results:** Write 3–4 sentences. State whether the difference is statistically significant, what the confidence intervals tell you, and what you would recommend to the clinical team.

---

## Exercise 3: Clinical Correlation Analysis

**Business question:** A researcher suspects that patients with higher BMI tend to have higher blood pressure. Before running a full clinical study, they want to know whether the correlation in existing data is strong enough to justify the research investment.

**Your tasks:**
1. Load the dataset provided in the notebook (or use the `sklearn` diabetes dataset as a proxy)
2. Create a scatter plot of BMI vs blood pressure with a regression line
3. Calculate the Pearson correlation coefficient and its p-value (`scipy.stats.pearsonr`)
4. Calculate R² (square the correlation coefficient)

**Interpret your results:** Write 3–4 sentences. State the strength and direction of the correlation, whether it is statistically significant, and what the R² value tells you about how much of the variation in blood pressure can be explained by BMI. Would you recommend the researcher proceed with the full study?

---

## Submission Checklist

Before submitting, confirm:
- [ ] All three exercises produce output (charts and printed results) when the notebook is run top to bottom
- [ ] Each exercise includes a written interpretation in a markdown cell (not just code)
- [ ] Variable names are clear and code has at least one comment per logical block
- [ ] You have pushed your notebook to your GitHub repository

**Submit:** Paste your repository URL into the course portal.

---

## How You Will Be Assessed

| Criterion | What markers look for |
|---|---|
| Correct implementation | Code runs without errors and produces sensible output |
| Statistical reasoning | Correct interpretation of p-values, confidence intervals, and correlation |
| Plain-English communication | Interpretations are clear to a non-technical reader |
| Code quality | Clear variable names, at least one comment per block, readable structure |

---

## Sample Solutions

> **Read this after you have attempted each exercise on your own.**
> Compare your code and interpretation — there is often more than one correct approach.
> Focus on whether your interpretation is clear and your reasoning is sound.

---

### Solution — Exercise 1: Appointment Booking Simulation

```python
import numpy as np
import matplotlib.pyplot as plt

np.random.seed(42)

# --- Step 1: Simulate 10,000 bookings ---
slots = ['Morning', 'Afternoon', 'Evening']
bookings = np.random.choice(slots, size=10_000)

# --- Step 2: Count frequencies ---
unique, counts = np.unique(bookings, return_counts=True)
frequencies = dict(zip(unique, counts))
print("Slot frequencies:", frequencies)

# Bar chart
fig, ax = plt.subplots(figsize=(7, 4))
ax.bar(unique, counts, color=['steelblue', 'coral', 'mediumseagreen'], edgecolor='white')
ax.axhline(10_000 / 3, color='orange', linestyle='--', linewidth=2,
           label='Expected (1/3 each = 3,333)')
ax.set_xlabel('Appointment Slot')
ax.set_ylabel('Number of Bookings')
ax.set_title('Simulated Appointment Slot Distribution (n=10,000)')
ax.legend()
plt.tight_layout()
plt.show()

# --- Step 3: Empirical probabilities ---
for slot, count in zip(unique, counts):
    empirical_prob = count / 10_000
    print(f"{slot}: {count} bookings → empirical probability = {empirical_prob:.4f}")

# --- Step 4: Compare to theoretical ---
print(f"\nTheoretical probability for each slot: {1/3:.4f}")
print(f"Maximum deviation: {max(abs(c/10_000 - 1/3) for c in counts):.4f}")
```

**Sample interpretation:**

> The simulation shows that after 10,000 bookings, each slot receives close to — but not exactly — one third of all appointments. The empirical probabilities hover around 0.333, with small random deviations (typically less than 0.01). This is the Law of Large Numbers in action: the more bookings we simulate, the closer each slot's share converges to the true theoretical probability of 1/3. With 100,000 bookings, those deviations would shrink further, because the random noise averages out over a larger sample.

---

### Solution — Exercise 2: Comparing Patient Groups

```python
import numpy as np
import scipy.stats as stats
import matplotlib.pyplot as plt

np.random.seed(42)

# --- Step 1: Generate wait-time samples ---
group_a = np.random.normal(loc=12, scale=4, size=100)   # App booking
group_b = np.random.normal(loc=15, scale=4, size=100)   # Phone booking

# --- Step 2: Overlapping histograms ---
fig, ax = plt.subplots(figsize=(8, 4))
ax.hist(group_a, bins=20, alpha=0.6, color='steelblue',
        edgecolor='white', label='Group A (App)')
ax.hist(group_b, bins=20, alpha=0.6, color='coral',
        edgecolor='white', label='Group B (Phone)')
ax.set_xlabel('Wait Time (minutes)')
ax.set_ylabel('Number of Patients')
ax.set_title('Wait Time Distribution: App vs Phone Booking')
ax.legend()
plt.tight_layout()
plt.show()

# --- Step 3: Independent samples t-test ---
t_stat, p_value = stats.ttest_ind(group_a, group_b)
print(f"t-statistic: {t_stat:.3f}")
print(f"p-value:     {p_value:.6f}")
print(f"Significant at α=0.05: {p_value < 0.05}")

# --- Step 4: 95% confidence intervals for each group mean ---
def confidence_interval_95(sample):
    n = len(sample)
    mean = np.mean(sample)
    se = stats.sem(sample)          # Standard error of the mean
    margin = se * stats.t.ppf(0.975, df=n-1)   # t critical value
    return mean, mean - margin, mean + margin

mean_a, ci_lo_a, ci_hi_a = confidence_interval_95(group_a)
mean_b, ci_lo_b, ci_hi_b = confidence_interval_95(group_b)

print(f"\nGroup A — mean: {mean_a:.2f} min, 95% CI: [{ci_lo_a:.2f}, {ci_hi_a:.2f}]")
print(f"Group B — mean: {mean_b:.2f} min, 95% CI: [{ci_lo_b:.2f}, {ci_hi_b:.2f}]")

# Visualise confidence intervals
fig, ax = plt.subplots(figsize=(6, 3))
for i, (label, mean, lo, hi, color) in enumerate([
    ('Group A (App)',   mean_a, ci_lo_a, ci_hi_a, 'steelblue'),
    ('Group B (Phone)', mean_b, ci_lo_b, ci_hi_b, 'coral')
]):
    ax.plot([lo, hi], [i, i], color=color, linewidth=4, solid_capstyle='round')
    ax.plot(mean, i, 'o', color='white', markersize=10, markeredgecolor=color, markeredgewidth=2)
    ax.text(hi + 0.2, i, f'{mean:.1f} min', va='center', fontsize=11)

ax.set_yticks([0, 1])
ax.set_yticklabels(['Group A (App)', 'Group B (Phone)'])
ax.set_xlabel('Wait Time (minutes)')
ax.set_title('95% Confidence Intervals for Group Means')
plt.tight_layout()
plt.show()
```

**Sample interpretation:**

> The t-test returns a p-value well below 0.05, so the 3-minute difference in average wait times is statistically significant — it is very unlikely to have occurred by chance alone. The 95% confidence intervals for the two groups do not overlap, which reinforces this conclusion: we can be 95% confident that the true mean wait time for app users falls below that of phone users. The data supports recommending the app-based booking system to the clinical team as a meaningful improvement. That said, statistical significance alone does not tell us whether 3 minutes is a clinically important saving — that judgement belongs to the team.

---

### Solution — Exercise 3: Clinical Correlation Analysis

```python
import numpy as np
import matplotlib.pyplot as plt
import scipy.stats as stats
from sklearn.datasets import load_diabetes

np.random.seed(42)

# --- Step 1: Load the sklearn diabetes dataset ---
# Column index 2 = BMI (normalised), column index 3 = blood pressure (normalised)
diabetes = load_diabetes()
bmi = diabetes.data[:, 2]
bp  = diabetes.data[:, 3]

print(f"Dataset: {len(bmi)} patients")
print(f"BMI range (normalised): {bmi.min():.3f} to {bmi.max():.3f}")

# --- Step 2: Scatter plot with regression line ---
# Fit a linear regression line manually
slope, intercept, r_value, p_value, std_err = stats.linregress(bmi, bp)
x_line = np.linspace(bmi.min(), bmi.max(), 100)
y_line = slope * x_line + intercept

fig, ax = plt.subplots(figsize=(7, 5))
ax.scatter(bmi, bp, alpha=0.5, color='steelblue', edgecolors='white', s=40, label='Patients')
ax.plot(x_line, y_line, color='coral', linewidth=2.5, label='Regression line')
ax.set_xlabel('BMI (normalised)')
ax.set_ylabel('Blood Pressure (normalised)')
ax.set_title('BMI vs Blood Pressure — Diabetes Dataset')
ax.legend()
plt.tight_layout()
plt.show()

# --- Step 3: Pearson correlation and p-value ---
r, p = stats.pearsonr(bmi, bp)
print(f"\nPearson r:  {r:.4f}")
print(f"p-value:    {p:.6f}")
print(f"Significant at α=0.05: {p < 0.05}")

# --- Step 4: R-squared ---
r_squared = r ** 2
print(f"\nR² = {r_squared:.4f}")
print(f"BMI explains {r_squared * 100:.1f}% of the variation in blood pressure")
```

**Sample interpretation:**

> The Pearson correlation coefficient is approximately r = 0.39, indicating a moderate positive relationship: patients with higher BMI tend to have higher blood pressure, and the direction is consistent with the researcher's hypothesis. The p-value is well below 0.05, confirming this correlation is statistically significant and not a result of random chance. However, R² ≈ 0.15 means that BMI alone explains only about 15% of the variation in blood pressure — the majority of variation is driven by other factors not captured here. Given the significant but modest correlation, the researcher is justified in proceeding with a full study, but should design it to control for confounders such as age, medication use, and lifestyle factors.
