# 3.1 Probability and Statistics for Machine Learning

Probability and statistics are the foundation of every machine learning algorithm. This module gives you the tools to describe data, understand uncertainty, and test whether the patterns you find are real — or just noise.

![Probability](assets/infographic-3.1-probability.png)
![Statistics](assets/infographic-3.1-statistics.png)

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

## Before You Start — Environment Setup

> **If this is your first time using this repo, do this before anything else.**
>
> Follow the [**Setup Guide →**](./setup.md) to install the required Python environment. It takes about 10 minutes. Without it, none of the notebooks will run.

---

## Your Learning Path

This module follows a three-phase flow. Work through the phases in order.

---

### Phase 1 — Before Class: Self-Study (60 min)

**Goal:** Arrive at the session having seen the concepts once, so the hands-on time feels like reinforcement — not a first encounter.

**Start here →** [**pre-class.md**](./pre-class.md)

The self-study guide walks you through the key ideas with videos, mini-exercises, and reflection questions. Attempt each question before checking the sample answer.

---

### Phase 2 — In Class: Concept Review + Hands-On Notebooks (3 hrs)

**Goal:** Consolidate concepts with the instructor, then run the notebooks yourself and see the ideas in code.

**Concept reference →** [**lesson.md**](./lesson.md)

Each key concept is explained in plain English with a real-world analogy and a quick-check question. Use this during and after class to check your understanding.

**Choose your entry point:**

> **Prefer learning by doing with an instructor?** Start with the three part notebooks below.
>
> **Prefer story-driven learning?** Start with `notebooks/case_study.ipynb` — it covers all the same concepts as a single connected narrative, following Maya, a junior data analyst at a Singapore e-commerce company, through one week of real problems. You can use it instead of or alongside Parts 1–3.

**Part notebooks — run in order:**

| # | Notebook | What you explore |
|---|---|---|
| 1 | `notebooks/Part_1_probability_statistics_lesson.ipynb` | Law of Large Numbers · Mean · Median · Mode |
| 2 | `notebooks/Part_2_probability_statistics_lesson.ipynb` | Uniform · Normal · Skewed distributions · Central Limit Theorem |
| 3 | `notebooks/Part_3_probability_statistics_lesson.ipynb` | Z-scores · P-values · Hypothesis testing |

Each notebook opens with a business scenario, guides you through the code with Pause & Predict prompts, and ends with reflection questions. Read every markdown cell, not just the code.

---

### Phase 3 — After Class: Assignment + Further Reading

**Goal:** Apply what you learned independently to a new scenario.

**Assignment →** `notebooks/assignment.ipynb`

Three tiers of practice (guided → partial → open) followed by three independent assignment exercises set in a healthcare context. Each exercise asks you to write code *and* explain your findings in plain English. Sample solutions are at the bottom of the notebook — check them only after you have attempted each exercise yourself.

**Further reading →** [**reference.md**](./reference.md)

Recommended books, videos, and articles if you want to go deeper on any topic from this module.

---

## File Map

```
README.md             ← You are here
setup.md              ← One-time environment setup (do this first)
pre-class.md          ← Phase 1: Pre-class self-study
lesson.md             ← Phase 2: Concept reference for all key topics
notebooks/
  Part_1_*.ipynb      ← Phase 2: In-class notebook — probability foundations
  Part_2_*.ipynb      ← Phase 2: In-class notebook — distributions
  Part_3_*.ipynb      ← Phase 2: In-class notebook — hypothesis testing
  case_study.ipynb    ← Phase 2: Story-driven alternative (ShopEasy) — good starting point for story-based learners
  assignment.ipynb    ← Phase 3: Practice tiers + assignment + sample solutions
reference.md          ← Phase 3: Further reading and glossary
environment.yml       ← Conda environment spec (used in setup)
assets/               ← Supporting images
```
