# ITI Statistics Case Studies 

This repository contains **two complete statistics case studies** completed during the **Introduction to Statistics** course at the Information Technology Institute (ITI).

These projects go beyond simple calculations. They focus on **data cleaning**, **choosing the right statistical test**, **checking assumptions**, and **communicating findings** to non-technical stakeholders.

---

##  Case Studies

### 1. [The Commute Question](./Case-Study-1-Commute-Question/)
**Problem:** ITI leadership considered a remote attendance policy for students with long commutes. Did commuting actually hurt academic performance?

**Key Findings:**
- Median commute time: **33 minutes** (vs. Mean: 45.3 mins – right-skewed).
- Correlation between commute and final score: `r = -0.055` (no meaningful relationship).
- The real driver of performance was **weekly study hours** (`r = 0.614`).
- **Recommendation:** Reject blanket policy; implement branch-specific support for Cairo students and extreme commuters (>114.9 mins).

📄 **[View Case Study 1](./Case-Study-1-Commute-Question/)**

---

### 2. [The Placement Report Dispute](./Case-Study-2-Placement-Report/)
**Problem:** The ITI placement office claimed Data Science was the "strongest" track and UI/UX was the "weakest" based on raw averages. The UI/UX lead objected, arguing the comparison was unfair.

**Key Findings:**
- Used **Z-scores** to compare students fairly across tracks (a UI/UX student with 84 scored better *relative to peers* than a Cyber Security student with 82).
- Salaries were **positively skewed** (Mean > Median), making the median a better measure.
- Applied **Binomial** and **Poisson** distributions, checking assumptions before using formulas.
- **Recommendation:** Rewrote the report using standardized scores and honest conclusions.

📄 **[View Case Study 2](./Case-Study-2-Placement-Report/)**

---

## 🛠️ Tools Used
- **Microsoft Excel** (PivotTables, CORREL, AVERAGEIF, IQR, Standard Deviation)
- **Python (Pandas)** – optional for data manipulation
- **Statistical Concepts:** Z-scores, Normal Distribution, Binomial, Poisson, Box Plots, Skewness, CV, Correlation vs. Causation.

---

##  Key Takeaway
> *"Clean data lies too, whenever it is summarized carelessly."*  
> The arithmetic was always correct. The challenge was knowing *which* number to compute, *when* a formula applies, and being **honest about the limits** of the data.

> 🚀 **Check out my main BI Project:** [SalesPulse Dashboard](https://github.com/DoniaHabib1/salesPulse-analytics-dashboard)
