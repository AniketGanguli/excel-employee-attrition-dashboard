# 👩‍💼 Employee Attrition Analysis Dashboard  
*A Data-Driven Approach to Understanding Workforce Turnover*

---

## 🎯 Objective

To uncover key drivers of employee attrition using Microsoft Excel and build an interactive dashboard that helps HR and leadership teams make strategic, data-driven decisions.

---

## 📁 Dataset Information

- **Source**: [Kaggle – Employee Attrition Dataset](https://www.kaggle.com/datasets)  
- **Contents**: Employee-level data including demographics, income, education, satisfaction scores, and attrition status.

---

## 🧩 Workflow Summary

### 1️⃣ Data Import & Cleaning

- Imported dataset into **Excel Power Query**
- Removed unnecessary columns
- Standardized data types
- Handled:
  - Null values
  - Duplicate entries
  - Inconsistent formatting

---

### 2️⃣ Feature Engineering (Power Query)

New fields created for deeper analysis:

| Feature | Description |
|--------|-------------|
| 🎂 **Age Group** | 18–30, 31–40, 41–50, 51–60 |
| 📍 **Work Distance** | Near-by, Far, Very Far |
| 💰 **Monthly Income** | `<5k`, `5k–10k`, `10k–15k`, `15k–20k` |
| 🎓 **Education Level** | Bachelor, Master, Doctor, etc. |
| 📊 **Ratings** | Converted performance, satisfaction, and work-life balance scores into High/Medium/Low descriptors |

---

### 3️⃣ Pivot Tables & Data Visualization

Built using:
- **Pivot Tables** for attrition by age, income, education, department, etc.
- **Slicers** for filtering by gender and department
- **Custom formatting** for professional presentation

---

### 4️⃣ Dashboard Design

📊 Designed a fully interactive Excel dashboard with:
- Key metrics (total attrition, active employees, attrition rate, average age)
- Visuals (bar charts, pie charts, gender breakdowns)
- Filters for department and gender
- Clean layout with icons, color coding, and shape containers

📸 **Dashboard Preview:**

![Employee Attrition Dashboard](images/Dashboard.png)

---

## ⚠️ Problem Encountered & Solution

**Issue:** When slicers were applied, pivot tables excluded fields with 0 count, which caused layout breaks and formula errors due to cell reference shifts.

**Fix:**
- Tried enabling "Show items with no data" (option was greyed out).
- **Final solution:** Created a DAX measure in Power Pivot to return `0` instead of blank:

```DAX
EmployeeCount := IF(COUNTA(EmployeeID) = BLANK(), 0, COUNTA(EmployeeID))
