# Case Study 1: The Commute Question 

## 📌 Problem Statement
The ITI academic director received complaints that students with long commutes arrive tired and underperform. A policy was proposed to offer remote attendance for long-commute students. Before approving the budget, the director asked:

1. **Is the commute problem real?** (How long do students actually travel?)
2. **Does commuting hurt academic performance?**
3. **If we run the policy, who qualifies?** (Give a defendable threshold and count how many students it covers.)

---

##  Data Cleaning Process (Part B)
The dataset was deliberately messy. We dealt with **7 distinct types of dirty data**:
1. **Duplicate Records** – Removed 11 exact duplicates (271 → 260 rows).
2. **Inconsistent Categories** – Standardized branch names (e.g., "cairo" → "Cairo", "Mansora" → "Mansoura").
3. **Missing Values** – Converted "NA", "?", "unknown", blanks to `NaN` (not zero).
4. **Impossible Values** – Replaced invalid ages (-1, 150), study hours (-5, 200), and scores (999, 150) with `NaN`.
5. **Numbers Stored as Text** – Extracted numbers from strings like "45 min" and "25.1 hours".
6. **Genuine Outliers** – Preserved 15 extreme commutes (e.g., 200+ mins) as valid long-distance travelers.
7. **Ambiguous Answers** – Interpreted "None" as "No sport" (not missing).

---

## 🔍 Key Findings (Part C & D)

| Metric | Value |
| :--- | :--- |
| **Mean Commute** | 45.3 minutes |
| **Median Commute** | 33.05 minutes |
| **Std Dev Commute** | 39.58 minutes |
| **Correlation (Commute vs Score)** | `r = -0.055` (Very weak) |
| **Correlation (Study Hours vs Score)** | `r = 0.614` (Strongest driver) |
| **Top Driver of Performance** | Weekly Study Hours (not commute time!) |

**Key Insight:** The distribution is **right-skewed** (Mean > Median). This means a small number of students with extremely long commutes inflate the average. The "typical" student actually travels about **33 minutes** (Median).

**Cairo Branch Effect:** Excluding Cairo drops the national mean commute by **~9.5 minutes**, proving a single national policy is inappropriate.

---

##  Files in this Folder

| File | Description |
| :--- | :--- |
| [Commute_Question_Statistics_Final_Report.pdf](./Commute_Question_Statistics_Final_Report.pdf) | Complete final report (Executive Summary + Parts A–F). |
| [Commute_Question_Statistics_CaseStudy_Cleaned.xlsx](./Commute_Question_Statistics_CaseStudy_Cleaned.xlsx) | Excel file with Raw, Cleaned, Analysis, and Cleaning Log sheets. |
| [Part_A_Classification.docx](./Part_A_Classification.docx) | Variable classification answers (Nominal, Ordinal, Continuous, Discrete). |
| [Part_B_Classification.docx](./Part_B_Classification.docx) | Detailed decisions for each dirty data category. |
| [Final_Conclusions_part C.xlsx](./Final_Conclusions_part%20C.xlsx) | Excel File with 2 sheets Descriptive_Statistics, Branch_Calculations Explain Steps for Descriptive Statistics. |

---

## 📊 Final Recommendation (Part F)
- **Do NOT run** the blanket remote-attendance policy for all students.
- **Instead:** Implement a **branch-specific support program** targeting Cairo students and extreme commuters (>114.9 mins, ~2 hours).
- **Number affected:** ~15 students (5.8% of sample).
- **Why:** The data shows commute time has almost no effect on scores. The real driver is **study hours**. We cannot claim causation due to sampling bias and confounding factors.

---

##  Tools Used
- **Microsoft Excel** (PivotTables, CORREL, AVERAGEIF, IQR, standard deviation)
- **Statistical Concepts:** Mean, Median, Mode, Standard Deviation, IQR, Correlation, Skewness, CV.

---

##  Key Takeaway
> *"Clean data lies too, whenever it is summarized carelessly."*  
> The arithmetic was correct, but choosing the **median** over the **mean** completely changed the story. Always check the shape of your distribution before reporting an average.

---

## 🔗 Related Projects
-  **[Main BI Project: SalesPulse Dashboard](https://github.com/DoniaHabib1/salesPulse-analytics-dashboard)**
-  **[Case Study 2: The Placement Report Dispute](../Case-Study-2-Placement-Report/)**
