# Practice — 3.1 Probability and Statistics

**Complete this after the lesson session and before the assignment.**  
**Estimated time:** 60–90 minutes

This practice session bridges the gap between the guided code-along and the assignment. It has three tiers — start at Tier 1 and work your way through. Use the hints if you get stuck, but try each exercise independently first.

Open `notebooks/practice.ipynb` and work through the exercises there.

---

## What This Practice Covers

| Tier | Style | What you do |
|---|---|---|
| Tier 1 — Guided | Fully worked example | Read, run, and understand a complete solution |
| Tier 2 — Partial | Fill in the blanks | Key lines are removed; you write them with hints available |
| Tier 3 — Open | New scenario | You apply the concepts to a fresh dataset with only a problem statement and success criteria |

---

## Tier 1: Guided — Customer Spend Analysis

**Scenario:** You work at a subscription software company. You have data on monthly spend per customer. Your job is to describe this data and check whether two customer segments (free-trial converts vs direct purchases) spend significantly differently.

This exercise is fully worked in the notebook. Your job is to:
1. Read each code cell and its comment carefully
2. Before running each cell, predict what the output will look like
3. After running, check whether your prediction was right — if it wasn't, re-read the code and figure out why

---

## Tier 2: Partial — Employee Salary Distribution

**Scenario:** You are an HR analyst at a mid-size company. You have been given salary data for two departments: Engineering and Marketing. Your manager wants to know:
- What does the salary distribution look like in each department?
- Is the difference in average salary between the two departments statistically significant?

In the notebook, key lines have been replaced with `# YOUR CODE HERE`. Use the hints below if you get stuck.

**Hints:**
- To plot a distribution, try `sns.histplot()` or `sns.kdeplot()`
- To run a t-test comparing two groups, use `scipy.stats.ttest_ind(group_a, group_b)`
- The p-value is in the result object: `result.pvalue`
- If p < 0.05, the difference is statistically significant

**Success criteria:** You know you've got it right when:
- You can see two clearly different distribution shapes
- Your t-test output includes a t-statistic and p-value
- You can state in one plain-English sentence whether the salary difference is statistically significant

---

## Tier 3: Open — Website Traffic Anomaly Detection

**Scenario:** You are a data analyst at a media company. The team tracks daily website visitors. Your job is to flag any days where traffic was "unusually low" — more than 2 standard deviations below the mean — so the engineering team can investigate potential outages.

The dataset is generated in the notebook. You will need to:
1. Calculate the mean and standard deviation of daily traffic
2. Calculate a z-score for each day
3. Flag days where z-score < -2
4. Visualise the flagged days on a line chart

No hints are provided for Tier 3. Use what you practised in Tiers 1 and 2.

**Success criteria:**
- You have identified at least one anomalous day
- Your chart clearly shows the flagged day(s) in a different colour
- You can explain in one sentence why z-score < -2 is a reasonable threshold for flagging anomalies

---

## Reflection

After completing all three tiers, answer these questions in the notebook's final markdown cell:

1. Which concept felt most solid after the practice?
2. Which concept still feels uncertain? (Bring this to the next session or post in the course channel)
3. Looking at Tier 3 — if this were a real company scenario, what additional context would you want before presenting your anomaly findings to the engineering team?
