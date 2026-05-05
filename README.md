# 📡 Telecommuncations-Analysis — ConnectaTel

## 🎯 Project Objective

Evaluate the behavior of **ConnectaTel** customers, a telecommunications company in Latin America, using data recorded through 2024.

The analysis aims to:
- Detect atypical behavior in service usage
- Identify customer segments with differentiated needs
- Optimize the commercial offer and improve the user experience

---

## 📂 Datasets Used

| File | Description |
|---|---|
| `plans.csv` | Plan information (price, included minutes, GB, extra cost) |
| `users_latam.csv` | Customer information (age, city, registration date, plan, churn) |
| `usage.csv` | Detailed record of real service usage (calls and messages) |

---

## 🧩 Analysis Stages

1. **Load and explore** — Load all 3 datasets, review structure, data types, and first rows.
2. **Data quality issues** — Detection of null values, sentinels (`-999`, `?`) and incorrectly formatted dates.
3. **Data cleaning** — Replace sentinels with medians or `pd.NA`, fix future or impossible dates, MAR verification for `duration` and `length`.
4. **User profile construction** — Aggregate `usage` by `user_id` (messages, calls, minutes) and merge with `users`.
5. **Statistical analysis and visualization** — Histograms by plan (`hue='plan'`), boxplots for outlier detection, IQR method for limit calculation.
6. **Customer segmentation** — Classification by usage level (`grupo_uso`) and age group (`grupo_edad`).
7. **Executive insights** — Actionable conclusions for stakeholders on segments, patterns, and plan recommendations.

---

## ▶️ How to Run the Notebook

### Option A — Google Colab (recommended)

1. Open [Google Colab](https://colab.research.google.com/)
2. Go to **File → Upload notebook** and upload the `.ipynb` file
3. Upload the datasets to the `/datasets/` path in the Colab environment:
   - **File → Upload to session storage**
4. Run all cells with `Runtime → Run all`

### Option B — Local Jupyter Notebook

```bash
# 1. Clone the repository
git clone https://github.com/your-username/your-repo.git
cd your-repo

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn

# 3. Open the notebook
jupyter notebook S7_Version-Estudiante-Project-ConnectaTel.ipynb
```

---

## 🔁 Reproduction Guide

1. Make sure all 3 CSV files are located at `/datasets/`
2. Run cells **in sequential order** — each step depends on the previous one
3. The main DataFrames built throughout the notebook are:

| Variable | Content |
|---|---|
| `plans` | Plan information |
| `users` | Cleaned customer data |
| `usage` | Detailed service usage |
| `usage_agg` | Usage aggregated by `user_id` |
| `user_profile` | Full customer profile (merge of users + usage_agg) |

4. At the end of the notebook you will find the **executive analysis** with recommendations for ConnectaTel

---

## 🛠️ Required Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 📌 Notes

- Data contains sentinel values (`-999` in `age`, `?` in `city`) that were corrected during cleaning
- Future dates in `reg_date` were flagged as `NaT`
- Outliers in `cant_mensajes`, `cant_llamadas` and `cant_minutos_llamada` were identified using the IQR method

---

*Project developed as part of Sprint 7 — Data Analysis*
