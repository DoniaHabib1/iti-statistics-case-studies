# Case Study 2: The Placement Report Dispute

**Category:** Statistical Investigation  
**Tools:** Microsoft Excel (Advanced Formulas, PivotTables, Array Formulas)  
**Course:** Introduction to Statistics — Information Technology Institute (ITI)  
**Author:** Donia Mohammed Habib

---

## 📌 Problem Statement

The ITI placement office released a report claiming that the **Data Science** track was the "strongest" and the **UI/UX** track was the "weakest," based purely on raw average scores.

The UI/UX lead objected, arguing that the comparison was unfair because:
- Tracks differ sharply in how consistently their students perform (different spreads).
- Raw averages hide the shape of the distribution (skewness).
- Comparing students across tracks using raw scores ignores relative performance.

**Core Question:** *Is comparing raw averages across tracks with different distributions a statistically valid way to judge performance?*

---

## 🎯 Objective

To determine whether the placement office's claim was statistically valid, and to provide a fair, standardized comparison of student performance across tracks using proper statistical methods.

---

## 🛠️ Tools & Concepts Used

**Tools:**
- **Microsoft Excel** — Advanced formulas (INDEX/MATCH, AVERAGEIF, COUNTIF, SUMPRODUCT), array formulas, PivotTables.

**Statistical Concepts:**
- Coefficient of Variation (CV) — comparing dispersion across different units
- Z-scores & Standardization
- Mean vs. Median (Skewness Detection)
- Normal Distribution (68-95-99.7 rule)
- Binomial Distribution (interview → offer conversion)
- Poisson Distribution (helpdesk ticket arrivals)
- Box Plots (five-number summary, fences, outliers)
- Assumption Checking (before applying any distribution formula)

---

## 📊 Dataset Overview

The analysis uses **three clean datasets** (300 graduates, 180 helpdesk days, 120 timed tasks):

| Dataset | Records | Key Variables |
| :--- | :--- | :--- |
| **Graduates** | 300 | Track, assessment score, starting salary, interviews, offers, days to first offer |
| **Helpdesk** | 180 days | Date, lab, tickets logged |
| **Lab Task** | 120 | Student ref, branch, task completion time |

---

## 🔍 Methodology

### Part A — Is the Comparison Fair? (Dispersion & Shape)

**A1. Assessment Score Dispersion:**
- Calculated Mean, SD, and **Coefficient of Variation (CV)** for each track.
- **CV ranges from 5.47% (Cyber Security) to 15.80% (UI/UX)** — a 2.9x difference in relative variability.
- **Verdict:** Comparing raw averages is misleading when spreads differ so dramatically.

**A2. Salary Skewness:**
- Mean > Median in every track → **right-skewed distribution**.
- The **median** is the more representative measure of a typical graduate's salary.
- **Verdict:** Mean salary is the wrong statistic for this skewed variable.

### Part B — Standardized Comparison (Z-Scores)

- Applied **Z = (Value − Track Mean) / Track SD** to all 300 graduates within their own track.
- **Example:** Candidate A (Cyber Security, score 82) vs. Candidate B (UI/UX, score 84):
  - Candidate A Z-score: **1.666**
  - Candidate B Z-score: **1.122**
  - **Winner:** Candidate A — performed more exceptionally *relative to peers*.
- **Validation:** Mean of all 300 Z-scores ≈ **0.0000**, SD ≈ **0.995** → standardization applied correctly.

### Part C — Normal Distribution (68-95-99.7 Rule)

- Applied **only after** checking that mean ≈ median ≈ mode for Data Science scores.
- Compared theoretical tail probability vs. actual observed count.
- **Gap explained by:** sampling variability (only 95 DS students) and non-perfect normality.

### Part D — Box Plots: Cairo vs. Alexandria

- Five-number summary, IQR, fences (Q1 − 1.5×IQR / Q3 + 1.5×IQR), whiskers, outlier count.
- **Note:** Whiskers drawn to the most extreme observation *inside* the fence, not to the fence itself.

### Part E — Binomial Model (Interviews → Offers)

- **P(X=x) = C(n,x) · p^x · (1−p)^(n−x)**
- Overall conversion rate **p ≈ 29.2%**.
- A graduate with 6 interviews has **~87% chance** of ≥1 offer.
- **Reality check:** Model under-predicts zero-offer graduates because p is not constant across individuals (weak link: assumption 3).

### Part F — Poisson Model (Helpdesk Tickets)

- **P(X=x) = e^(−λ) · λ^x / x!**
- Mean ≈ Variance → consistent with Poisson fingerprint.
- Compared observed vs. expected frequency table (0–10 tickets/day).
- **Caveat:** Independence assumption may break (busy days rolling over).

---

## 📈 Key Findings

| # | Finding | Evidence |
| :--- | :--- | :--- |
| 1 | **Raw comparisons are unfair** across tracks with different spreads | CV ranges 5.5% (Cyber) to 15.8% (UI/UX) — a 2.9x difference |
| 2 | **Mean salary is misleading** for all tracks | Mean > Median in every track; 9 outliers (5 in Data Science) inflate averages |
| 3 | **UI/UX top students outperform** on scores, but **not on salary** | UI/UX has the cohort's highest single score (98.0) and top-decile average; but its top earners trail other tracks |
| 4 | **Standardization is required** for fair cross-track comparison | Z-scores validated: mean ≈ 0, SD ≈ 0.995 across all 300 |
| 5 | **Distribution formulas must be assumption-checked** | Normal applied only after shape check; Binomial caveat on constant p; Poisson caveat on independence |

---

## ✅ Recommendations

1. **Replace raw averages with standardized measures** (CV + Z-scores) in all future placement reports.
2. **Use the median, not the mean,** for any salary headline statistic (due to right-skewness).
3. **Report dispersion (CV) alongside central tendency** — a high average with high variability tells a different story than a tight, reliable average.
4. **Apply distribution formulas only after stating WHY the assumption is reasonable** for that specific column.
5. **Acknowledge the limits of the data** — a model that under-predicts zero-offer graduates is still useful if its limits are honestly reported.

---

## 📁 Files in This Repository

| File | Description |
| :--- | :--- |
| `ITI_CaseStudy2_Solved.xlsx` | Full statistical workbook — all results are LIVE FORMULAS driven by raw data tabs. Change a raw value and every table recalculates. |
| `ITI-CaseStudy2-DoniaMohammedHabib.xlsx` | Answer sheet with formulas and assumptions documented per part. |
| `CaseStudy2-Report-DoniaHabib.docx` | Full written report with executive summary and conclusions. |
| `README.md` | This file. |

### Workbook Tabs (in `ITI_CaseStudy2_Solved.xlsx`)

| Tab | Contents |
| :--- | :--- |
| `README` | Color key: Blue = editable input, Black = formula, Orange = pooled total |
| `Graduates` | Cleaned raw data (300 rows) + per-student Z-score and binomial model columns |
| `Lab_Task` | Cleaned raw data (120 rows) + outlier flag per branch |
| `Helpdesk` | Cleaned raw data (180 rows) |
| `Track_Stats` | Part A & C — mean / median / mode / SD / CV / quartile & moment skewness |
| `B_ZScores` | Part B — candidate Z-scores, days-to-offer Z-score, standardization check |
| `C_Normal` | Part C — 68-95-99.7 rule applied to Data Science scores |
| `D_BoxPlots` | Part D — five-number summary, fences, whiskers, outliers |
| `E_Binomial` | Part E — binomial model of interview→offer conversion, reality check |
| `F_Poisson` | Part F — Poisson model of helpdesk tickets, observed vs expected |
| `G_Summary` | Part G — corrected placement-report paragraph and verdict on all three objections |

---

## 🔗 Related Links

- [Main Portfolio](https://github.com/DoniaHabib1)
- [Case Study 1: The Commute Question](https://github.com/DoniaHabib1/iti-statistics-case-studies/tree/main/Case-Study-1-Commute-Question)

---

> *"Clean data lies too, whenever it is summarized carelessly."*
>
> The arithmetic was always correct. The challenge was knowing *which* number to compute, *when* a formula applies, and being **honest about the limits** of the data.


## 💡 Lessons Learned

- Raw averages can be dangerously misleading when comparing groups with different distributions.
- Always check the shape of your data (skewness) before choosing a measure of central tendency.
- Z-scores are a powerful tool for fair comparison across different scales.
- Statistical assumptions must be verified before applying any formula.
- Honest reporting means acknowledging what the data **cannot** tell you.
