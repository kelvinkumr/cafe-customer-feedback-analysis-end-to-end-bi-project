# ☕ Cafe Customer Feedback Analysis: End-to-End BI Project

![Excel](https://img.shields.io/badge/Excel-Data_Cleaning-green)
![Tableau](https://img.shields.io/badge/Tableau-Visualization-blue)
![Data Analysis](https://img.shields.io/badge/Analysis-Qualitative_%26_Quantitative-orange)

## 📌 Project Overview
This project involves a comprehensive analysis of customer feedback data from multiple café locations. The primary objective was to resolve significant data integrity issues in a raw dataset and transform unstructured customer comments into actionable business intelligence.

**Status:** Completed Analysis (Task assigned from [Customer Radar](https://customerradar.com/)).  
**Interactive Dashboard:** [View on Tableau Public](https://public.tableau.com/app/profile/kelvin.kumar/viz/cafe_graphs/Dashboard1?publish=yes)

---

## 📈 Executive Summary of Insights

### 1. The "Human Element" Driver
* **Service Dominance:** Customer experience is shaped primarily by personal interactions. Key terms like **"service," "friendly,"** and **"staff"** appear most frequently in comments (over 3,500 mentions for 'Service').
* **Sentiment Correlation:** High frequency of positive service terms directly aligns with a high rating distribution across the network.

### 2. Performance Benchmarking
* **Consistency:** Average ratings across most locations are consistently high, scoring between **4.3 and 4.8**.
* **Core Product Loyalty:** **"Coffee"** and **"food"** quality (2,736 and 1,394 appearances) are the secondary drivers of satisfaction, confirming that core offerings meet brand expectations.

### 3. Operational Pain Points
* **Friction Points:** Lower-rated locations (below the 4.3 average) show a direct link to operational issues such as **wait times**, **order inaccuracies**, and **inconsistent service**.
* **Environment:** Physical factors like **cleanliness** and **atmosphere** significantly contribute to the overall customer perception of the visit.

---

## 🏗️ Data Engineering & Methodology

### Step 1: Data Cleaning & Integrity
Identified and resolved structural errors in the raw dataset to ensure accurate analysis:
* **Data Imputation:** Corrected a corruption issue where transaction dates were erroneously stored in the transaction value column (affecting 0.16% of the data).
* **Standardization:** Converted all columns to correct data types and removed miscellaneous feedback IDs found outside the primary dataset.

### Step 2: Qualitative-to-Quantitative Transformation
To quantify unstructured customer comments, I developed logic to calculate the frequency of specific phrases across **2,400+ rows** of feedback. This created a structured map of customer sentiment.

### Step 3: Visual Dashboarding
Developed a Tableau dashboard focused on two key pillars:
* **Comparative Performance:** A visualization of **Average Rating by Location** to identify top and bottom performers.
* **Thematic Analysis:** A **Word Frequency Visual** to highlight the recurring topics customers mention most.

---

## 🧠 Challenges & Solutions

### 🛠️ Problem: Corrupted Timestamps
**Issue:** 0.16% of transaction dates were stored as numeric patterns in the transaction value column.  
**Solution:** Reconstructed the timestamps using a nested Excel formula to restore the correct format:

```excel=UPPER(TEXT(DATE(2000+LEFT(x,2), MID(x,3,2), MID(x,5,2))+TIME(MID(x,7,2), MID(x,9,2), MID(x,11,2)), "dd/mm/yyyy h:mm:ss AM/PM"))```

---

## 🛠️ Problem: Unstructured Text Analysis
**Issue:** Counting specific word appearances within a large range of unstructured text.
**Solution:** Applied a case-insensitive SUMPRODUCT and SUBSTITUTE logic to calculate precise appearances:

```excel==SUMPRODUCT((LEN(comment_range) - LEN(SUBSTITUTE(LOWER(comment_range), LOWER(keyword), ""))) / LEN(keyword))```

---

## 💡 Recommendations
  • Scale Excellence: Invest in staff training at lower-performing locations to mirror the "friendly" service found at top-rated sites.
  
  • Reduce Friction: Review operational workflows at sites with high "wait time" mentions to improve order accuracy and speed.
  
  • Keyword Monitoring: Implement ongoing keyword tracking to identify shifts in customer expectations or emerging product issues.

---

## 🚀 Tools Used
  • Excel: Data cleaning, formula-based timestamp reconstruction, and word frequency analysis.
  
  • Tableau: Data visualization and dashboard design.
  
