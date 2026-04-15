# Setup Guide — 3.1 Probability and Statistics

This guide walks you through setting up your environment step by step. It should take about 10 minutes. If anything goes wrong, the troubleshooting section at the bottom has you covered.

---

## What You Are Setting Up and Why

This lesson uses **Jupyter Notebook** — a tool that lets you write and run Python code in your browser, one small block at a time. Think of it like a interactive worksheet where you can see the results of your code immediately below each block.

To keep everyone using the same Python libraries and versions, we use **conda** to create a contained environment. Think of it like a dedicated workspace that has exactly the tools this lesson needs, separate from anything else on your computer.

---

## Step 1: Check That Conda Is Installed

Open your **Terminal** (Mac/Linux) or **Anaconda Prompt** (Windows) and type:

```
conda --version
```

You should see something like `conda 23.x.x`. If you see that, move to Step 2.

**If you see "command not found":** You need to install Miniconda first. Go to [https://docs.conda.io/en/latest/miniconda.html](https://docs.conda.io/en/latest/miniconda.html), download the installer for your operating system, and run it. Then come back and repeat Step 1.

---

## Step 2: Download the Course Files

If you haven't already, clone the repository to your computer:

```
git clone https://github.com/flexfengfeng/5m-data-3.1-probability-statistics
```

Then navigate into the folder:

```
cd 5m-data-3.1-probability-statistics
```

---

## Step 3: Create the Course Environment

This command reads the `environment.yml` file and installs everything the lesson needs:

```
conda env create -f environment.yml
```

This will take 2–5 minutes. You will see a progress bar and a list of packages being installed. That is normal.

When it finishes, you should see:

```
done
# To activate this environment, use:
#   conda activate ml
```

---

## Step 4: Activate the Environment

```
conda activate ml
```

Your terminal prompt should now show `(ml)` at the start, like this:

```
(ml) your-computer:5m-data-3.1-probability-statistics yourname$
```

That `(ml)` confirms you are in the right environment.

---

## Step 5: Launch Jupyter Notebook

```
jupyter notebook
```

Your browser should open automatically and show the Jupyter file browser. If it does not open, copy the URL shown in your terminal (it looks like `http://localhost:8888/...`) and paste it into your browser.

---

## Step 6: Smoke Test — Confirm Everything Works

In the Jupyter file browser, click **New → Python 3** to open a blank notebook. In the first cell, paste this code and press **Shift + Enter** to run it:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

print("✅ All good! Your environment is ready.")
print(f"   NumPy version: {np.__version__}")
print(f"   Pandas version: {pd.__version__}")
```

If you see the green tick and version numbers, you are all set. Close this test notebook (you do not need to save it) and open the lesson notebooks.

---

## Troubleshooting

**"conda activate ml" says the environment does not exist**
The environment was not created successfully. Try running `conda env create -f environment.yml` again. If the error mentions a package conflict, run `conda env create -f environment.yml --solver=libmamba` instead.

**Jupyter does not open in my browser**
Copy the full URL from your terminal output (starts with `http://localhost:8888/tree?token=...`) and paste it manually into Chrome or Firefox.

**"ModuleNotFoundError" when running the smoke test**
You are probably in the wrong environment. Close Jupyter, run `conda activate ml`, then `jupyter notebook` again.

**The terminal says "(base)" instead of "(ml)"**
You skipped Step 4. Run `conda activate ml` before launching Jupyter.

**I am on Windows and the commands are not working**
Make sure you are using **Anaconda Prompt**, not the regular Windows Command Prompt or PowerShell.

---

## Still Stuck?

Post a message in the course channel with:
1. The exact error message you see (a screenshot is fine)
2. Which step you are on
3. Your operating system (Mac / Windows / Linux)
