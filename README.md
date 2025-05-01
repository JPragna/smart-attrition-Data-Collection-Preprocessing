# **Smart Attrition Prediction & Employee Wellness Recommendation Engine**

## **Overview**
This project aims to predict employee attrition and recommend wellness programs based on various employee features. The dataset includes employee details such as job satisfaction, performance rating, salary, and more. This repository documents the data cleaning and preprocessing steps undertaken to prepare the dataset for modeling.

## **Table of Contents**
- [Project Description](#project-description)
- [Data Dictionary](#data-dictionary)
- [Data Cleaning & Preprocessing](#data-cleaning--preprocessing)
- [Tools and Technologies](#tools-and-technologies)
- [Data Source](#data-source)
- [Steps](#steps)
- [Output](#output)
- [Issues Logged](#issues-logged)
- [Environment Setup](#environment-setup)
- [Future Work](#future-work)
- [References](#references)

---

## **Project Description**
The goal of this project is to develop a predictive model that can forecast employee attrition and recommend wellness programs accordingly. Attrition predictions help organizations proactively manage employee satisfaction, retain talent, and reduce turnover. 

The project involves:
- **Data Collection**: Gathering relevant employee data from an internal system or public datasets.
- **Data Cleaning**: Handling missing values, data types, and irrelevant information.
- **Feature Engineering**: Creating additional features to improve the model's predictive power.
- **Model Development**: Using machine learning algorithms for attrition prediction.
- **Wellness Program Recommendation**: Based on attrition predictions, recommending relevant wellness programs.

---

## **Data Dictionary**
The following is the description of each column in the dataset:

| **Column Name**              | **Description**                                                                                   |
|------------------------------|---------------------------------------------------------------------------------------------------|
| Age                          | Employee's age                                                                                   |
| Attrition                    | Whether the employee left the company (1 for Yes, 0 for No)                                       |
| DailyRate                    | Daily rate of the employee                                                                        |
| DistanceFromHome             | Distance from the employee's home to the workplace in miles                                       |
| EmployeeCount                | The total number of employees in the organization (constant in the dataset)                        |
| EmployeeNumber               | A unique identifier for each employee                                                             |
| EnvironmentSatisfaction      | Employee's satisfaction with the work environment (scale 1-4)                                      |
| HourlyRate                   | Hourly wage of the employee                                                                       |
| JobInvolvement               | Degree of involvement in the job (scale 1-4)                                                      |
| JobLevel                     | Job level (1 to 5)                                                                                  |
| JobSatisfaction              | Job satisfaction level (scale 1-4)                                                                 |
| MonthlyIncome                | Employee’s monthly income in USD                                                                   |
| MonthlyRate                  | Total monthly revenue (from internal systems)                                                     |
| NumCompaniesWorked           | Number of companies the employee has worked for                                                   |
| Over18                       | Whether the employee is over 18 years old (1 for Yes, 0 for No)                                   |
| PercentSalaryHike            | Percentage increase in the employee's salary from the previous year                              |
| PerformanceRating            | Rating of employee's performance (scale 1-4)                                                      |
| RelationshipSatisfaction     | Satisfaction with work relationships (scale 1-4)                                                  |
| StandardHours                | Standard hours worked in a week (constant across all employees)                                    |
| TotalWorkingYears            | Total number of years the employee has worked professionally                                       |
| TrainingTimesLastYear        | Number of times the employee participated in training last year                                    |
| YearsAtCompany               | Number of years the employee has been at the company                                             |
| YearsInCurrentRole           | Number of years the employee has been in their current role                                      |
| YearsSinceLastPromotion      | Number of years since the employee's last promotion                                               |
| YearsWithCurrManager         | Number of years the employee has worked with the current manager                                  |
| SatisfactionIndex            | Index derived from several satisfaction-related columns                                           |
| WorkBalanceScore             | A score indicating the balance between work and personal life                                     |
| Overworked                   | Whether the employee is overworked (True/False)                                                   |
| AbsentDaysLastYear           | Number of days the employee was absent last year                                                 |
| LateComingCount              | Number of times the employee came late to work in the last year                                   |
| WorkedOvertimeDays           | Number of days the employee worked overtime                                                        |
| ExitComment                  | Comment provided by the employee about their reason for leaving, if available                     |
| SurveyText                   | Text from employee surveys regarding workplace satisfaction                                        |
| EngagementScore              | Employee's score on workplace engagement                                                           |
| PerformanceScore             | Employee's score based on their overall performance                                               |
| Bonus                        | Whether the employee received a bonus (1 for Yes, 0 for No)                                        |
| WellnessProgramParticipation | Whether the employee participated in wellness programs (1 for Yes, 0 for No)                      |
| WorkHoursPerWeek             | Number of hours the employee worked per week                                                      |
| TenureInYears                | The number of years the employee has worked at the company                                        |
| **Categorical Columns (Encoded)** |                                                                                              |
| BusinessTravel_Travel_Frequently | Whether the employee travels frequently for business                                          |
| BusinessTravel_Travel_Rarely | Whether the employee travels rarely for business                                                  |
| Department_Research & Development | Whether the employee is in the research and development department                            |
| Department_Sales             | Whether the employee is in the sales department                                                   |
| Education_2 to Education_5   | Education level (encoded)                                                                          |
| EducationField_Life Sciences to EducationField_Technical Degree | The field of education of the employee (encoded)                                            |
| Gender_Male                  | Gender of the employee (Male/Female)                                                              |
| JobRole_* (various roles)     | Job roles such as Manager, Laboratory Technician, etc. (encoded)                                  |
| MaritalStatus_Married, Single | Marital status of the employee (encoded)                                                         |
| OverTime_Yes                  | Whether the employee works overtime (1 for Yes, 0 for No)                                          |
| StockOptionLevel_1,2,3       | Level of stock options available to the employee (encoded)                                       |
| WorkLifeBalance_* (scale 2-4) | Work-life balance score (encoded)                                                                |
| TenureBucket_*               | Employee’s tenure categorized into ranges (e.g., 2-5 years, 5-10 years)                         |
| IncomeLevel_*                | Income level (Low, Medium, High)                                                                   |
| WellnessCategory_*           | Category of wellness program participation (Fair, Good, Poor)                                     |
| ManagerPerformance_*         | Performance evaluation of the manager (encoded)                                                   |

---

## **Data Cleaning & Preprocessing**

The following steps were taken to clean and preprocess the data:

1. **Handling Missing Values**: 
   - Columns with missing or `NaN` values were addressed using imputation techniques. For numerical columns, the median was used to fill missing values, while for categorical columns, the mode (most frequent value) was used.
   
2. **Feature Encoding**: 
   - Categorical variables such as `Gender`, `Department`, and `JobRole` were encoded using one-hot encoding to transform them into numerical values suitable for machine learning algorithms.
   
3. **Normalization**: 
   - Numerical features, including `Age`, `DistanceFromHome`, and `MonthlyIncome`, were normalized using Min-Max scaling to ensure they are within the same range.
   
4. **Feature Engineering**:
   - New features such as `SatisfactionIndex` and `WorkBalanceScore` were created by combining relevant columns, to provide more insights for predictive models.

5. **Outlier Removal**: 
   - Any extreme values that could skew the model were identified and either removed or capped, depending on the nature of the data.

6. **Text Cleaning**:
   - `ExitComment` and `SurveyText` were cleaned by removing stop words, normalizing the text, and applying tokenization for further analysis.

---

## **Tools and Technologies**
- **Python**: Programming language used for data cleaning and preprocessing.
- **Pandas**: Library for data manipulation and cleaning.
- **NumPy**: Used for numerical operations and handling arrays.
- **Scikit-learn**: Library for machine learning and preprocessing tasks (e.g., feature scaling, encoding).
- **Matplotlib & Seaborn**: For data visualization and exploratory data analysis.
- **Jupyter/Google Colab**: Environment for coding and running the project.

---

## **Data Source**
The dataset used in this project is derived from a publicly available employee attrition dataset (such as from Kaggle). This dataset contains various features about employee satisfaction, performance, and other metrics crucial for predicting employee turnover.

---

## **Steps**
1. **Initial Exploration**:
   - Load the dataset and inspect for missing values, data types, and other issues.
2. **Data Cleaning**:
   - Address missing values, handle outliers, and normalize/encode features.
3. **Feature Engineering**:
   - Create new features based on existing ones to better represent the data for predictive modeling.
4. **Final Dataset Creation**:
   - Prepare the cleaned dataset with all necessary transformations applied.

---

## **Output**
The output of this project will be a cleaned dataset with:
- Imputed missing values.
- Categorical variables encoded.
- Normalized numerical features.
- New features created through engineering.
- Ready-to-use dataset for building predictive models for employee attrition.

---

## **Issues Logged**
- **Missing Values**: Some columns contained missing values that were imputed.
- **Outliers**: Certain numerical columns had extreme values that were either capped or removed to ensure they did not affect model performance.
- **Categorical Encoding**: Some categorical columns had a high number of unique values, which were reduced using one-hot encoding.

---

## **Environment Setup**
1. **Python Version**: 3.x
2. **Required Libraries**:
   - Pandas
   - NumPy
   - Scikit-learn
   - Matplotlib
   - Seaborn
3. **Installation**:
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn

Future Work
Model Building: Implement machine learning algorithms such as Logistic Regression, Random Forest, and XGBoost to predict employee attrition.

Wellness Recommendation System: Based on the attrition prediction, suggest personalized wellness programs to employees.

References
Employee Attrition Dataset from Kaggle (or any other publicly available source).

Scikit-learn documentation for machine learning and preprocessing techniques.


