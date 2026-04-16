# 3.1 Probability and Statistics for Machine Learning

Probability and statistics are the foundation of every machine learning algorithm. This module gives you the tools to describe data, understand uncertainty, and test whether the patterns you find are real — or just noise.

---

## Learning Outcomes

By the end of this module you will be able to:

- Explain why sample size matters and apply the Law of Large Numbers to real A/B testing decisions
- Choose the right measure of central tendency (mean, median, mode) for a given dataset and justify your choice
- Identify common probability distributions (uniform, normal, skewed) and connect them to real-world data
- Apply the Central Limit Theorem to understand why statistical methods work on messy real-world data
- Calculate and interpret z-scores to detect anomalies in a dataset
- Run a hypothesis test end-to-end and communicate the result in plain English

---

## Your Learning Path

This module follows a three-phase flow. Work through the phases in order.

---

### Phase 1 — Before Class: Self-Study (60 min)

**Goal:** Arrive at the session having seen the concepts once, so the hands-on time feels like reinforcement — not a first encounter.

**Start here →** [**studies.md**](./studies.md)

The self-study guide walks you through the key ideas with reflection questions. Read it, attempt the questions, then check the sample answers before moving on.

> **First time?** Before you do anything else, follow the [Setup Guide](./setup.md) to get your environment running. It takes about 10 minutes.

---

### Phase 2 — In Class: Concept Review + Hands-On Notebooks (3 hrs)

**Goal:** Consolidate concepts with the instructor, then run the notebooks yourself and see the ideas in code.

**Concept reference →** [**lesson.md**](./lesson.md)

Each key concept is explained in plain English with a real-world analogy and a quick-check question. Use this during and after class to check your understanding.

**Run the notebooks in order:**

| # | Notebook | What you explore |
|---|---|---|
| 1 | `notebooks/Part_1_probability_statistics_lesson.ipynb` | Law of Large Numbers · Mean · Median · Mode |
| 2 | `notebooks/Part_2_probability_statistics_lesson.ipynb` | Uniform · Normal · Skewed distributions · Central Limit Theorem |
| 3 | `notebooks/Part_3_probability_statistics_lesson.ipynb` | Z-scores · P-values · Hypothesis testing |

Each notebook is self-contained — it opens with a business scenario, guides you through the code, and ends with reflection prompts. Read every markdown cell, not just the code.

**Then practise →** `notebooks/practice.ipynb`

Three-tier practice exercises (guided → partial → open) to bridge the gap between the notebooks and the assignment.

---

### Phase 3 — After Class: Assignment + Further Reading

**Goal:** Apply what you learned independently to a new scenario.

**Assignment →** [**assignment.md**](./assignment.md)

Three exercises set in a healthcare context. Each asks you to write code *and* explain your findings in plain English, as you would to a non-technical colleague. Sample solutions are included at the bottom of the file — check them after you have attempted each exercise yourself.

**Further reading →** [**reference.md**](./reference.md)

Recommended books, videos, and articles if you want to go deeper on any topic from this module.

---

## File Map

```
README.md          ← You are here
setup.md           ← One-time environment setup (do this first)
studies.md         ← Phase 1: Pre-class self-study
lesson.md          ← Phase 2: Concept reference for all key topics
notebooks/
  Part_1_*.ipynb   ← Phase 2: In-class notebook — probability foundations
  Part_2_*.ipynb   ← Phase 2: In-class notebook — distributions
  Part_3_*.ipynb   ← Phase 2: In-class notebook — hypothesis testing
  practice.ipynb   ← Phase 2→3: Practice exercises (3 tiers)
assignment.md      ← Phase 3: After-class assignment with sample solutions
reference.md       ← Phase 3: Further reading
environment.yml    ← Conda environment spec (used in setup)
assets/            ← Supporting images
```
