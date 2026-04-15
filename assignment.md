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
