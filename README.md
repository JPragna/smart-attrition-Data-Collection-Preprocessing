# Smart Attrition Prediction - Module 1: Data Collection & Preprocessing

## 📌 Objective
This module focuses on the initial data cleaning steps necessary to prepare the employee dataset for further analysis, modeling and prediction.

---

## 📂 Data Source
The dataset used is the [IBM HR Analytics Employee Attrition & Performance dataset](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) with additional engineered features.

---

## 🔧 Preprocessing & Cleaning Steps
### 1. **Initial Checks**
- Removed duplicate records (if any).
- Checked for null/missing values across all columns.
- Converted all string column names to lowercase and underscore format.

### 2. **Dropped Irrelevant Columns**
- `EmployeeCount` – constant value
- `Over18` – constant value
- `StandardHours` – constant value

### 3. **Converted Categorical Data**
- Label encoding for binary variables (`Yes/No` → 1/0)
- One-hot encoding for:
  - `JobRole`
  - `MaritalStatus`
  - `Department`
  - `EducationField`
  - `BusinessTravel`

### 4. **Feature Engineering**
Added new columns for deeper analytics and modeling:

| New Column | Description |
|------------|-------------|
| `SatisfactionIndex` | Weighted score of satisfaction-related fields |
| `TenureBucket` | Categorized years at company: `0–2`, `3–5`, `6–10`, `10+` |
| `WorkBalanceScore` | Derived from `WorkLifeBalance`, `OverTime`, and `JobInvolvement` |
| `IncomeLevel` | Income range category: `Low`, `Mid`, `High` |
| `Overworked` | Flag if `OverTime` is Yes + `WorkedOvertimeDays` > 15 |

### 5. **Handled Missing Values**
- Imputed using mean/mode or flagged for further review.
- Added an issue log for missing patterns (see below).

---

## 📁 Output
- **Cleaned Dataset Filename**: `cleaned_dataset.csv`
- **Rows**: Same as original (no dropped rows unless corrupted)
- **Columns**: ~50 (original + engineered)

---

## 📘 Sample of Data Dictionary

| Column Name | Description |
|-------------|-------------|
| `Age` | Age of employee |
| `Attrition` | Whether the employee left (Yes/No) |
| `JobRole` | Employee’s role in the organization |
| `WorkLifeBalance` | Self-rated work-life balance (1–4) |
| `SatisfactionIndex` | Custom index derived from multiple factors |
| `Overworked` | Whether employee worked overtime heavily |
| ... | ... |

*A full data dictionary will be added in the final report.*

---

## 🐞 Issues Logged

- Null values in `EnvironmentSatisfaction` for 6 entries.
- Inconsistent case formatting in `BusinessTravel`.
- Some entries show `MonthlyIncome` as "0", flagged for review.

---

## 📌 Tools & Environment
- **Platform**: Google Colab
- **Language**: Python (pandas, numpy, seaborn)
- **File Format**: CSV

---
