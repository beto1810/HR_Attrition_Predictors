# Predictors for Employee's Attrition





# :books: Table of Contents <!-- omit in toc -->

- [:briefcase: Case Study and Requirement](#case-study-and-requirement)
- [:bookmark_tabs: Example Datasets](#bookmark_tabsexample-datasets)
- [🔎 Explore data and test model](#explore-data-and-test-model)
- [📃 What can you practice with this case study?](#-what-can-you-practice-with-this-case-study)

---

# Case Study and Requirement

Due to the small size of the dataset, consisting of approximately 1500 entries, I utilized an IBM survey dataset to determine the presence or absence of attrition. Given this limited dataset, the model's ability to predict attrition is expected to offer only a slight improvement over random chance.

---

# :bookmark_tabs:Example Datasets

<details><summary> 👆🏼 Click to expand Dataset information </summary>

| Name                    | Description                                           |
|-------------------------|-------------------------------------------------------|
| Age                     | Employee's age in years                              |
| Attrition               | Employee's attrition status (e.g., "Yes" or "No")    |
| BusinessTravel          | Type of business travel (e.g., "Travel_Rarely")      |
| DailyRate               | Employee's daily rate of pay                         |
| Department              | Employee's department (e.g., "Sales")               |
| DistanceFromHome        | Distance from home to workplace in miles            |
| Education               | Employee's education level (e.g., 1 for 'Below College') |
| EducationField          | Field of education (e.g., "Life Sciences")          |
| EmployeeCount           | Number of employees  |
| EmployeeNumber          | Unique employee identification number                |
| EnvironmentSatisfaction | Satisfaction with the work environment (e.g., 3 for 'Neutral') |
| Gender                  | Employee's gender (e.g., "Male" or "Female")        |
| HourlyRate              | Employee's hourly rate of pay                       |
| JobInvolvement          | Job involvement level (e.g., 2 for 'Low')           |
| JobLevel                | Employee's job level (e.g., 1 for 'Entry Level')    |
| JobRole                 | Employee's job role (e.g., "Sales Executive")       |
| JobSatisfaction         | Job satisfaction level (e.g., 4 for 'Very Satisfied') |
| MaritalStatus           | Employee's marital status (e.g., "Married")        |
| MonthlyIncome           | Employee's monthly income in dollars                |
| MonthlyRate             | Employee's monthly rate of pay                      |
| NumCompaniesWorked      | Number of companies worked for                       |
| Over18                  | Employee's age over 18 (e.g., "Y" for "Yes")         |
| OverTime                | Overtime work status (e.g., "Yes" or "No")           |
| PercentSalaryHike       | Percentage increase in salary                       |
| PerformanceRating       | Performance rating (e.g., 3 for 'Good')        |
| RelationshipSatisfaction| Satisfaction with workplace relationships            |
| StandardHours           | Standard working hours (should be 1470 for all records) |
| StockOptionLevel        | Stock option level (e.g., 0 for 'No Stock Options')  |
| TotalWorkingYears       | Total years of working experience                    |
| TrainingTimesLastYear   | Number of training sessions attended last year      |
| WorkLifeBalance         | Work-life balance rating (e.g., 0 for 'Bad')         |
| YearsAtCompany          | Years the employee has spent at the company         |
| YearsInCurrentRole      | Years in the current job role                        |
| YearsSinceLastPromotion | Years since the last promotion                      |
| YearsWithCurrManager    | Years with the current manager       
</details>

<details><summary> 👆🏼 Click to expand Dataset sample rows </summary>

<div align="center">

**Table** 

<div align="center">
First 10 rows

| Age | Attrition | BusinessTravel | DailyRate | Department | DistanceFromHome | Education | EducationField | EmployeeCount | EmployeeNumber | EnvironmentSatisfaction | Gender | HourlyRate | JobInvolvement | JobLevel | JobRole | JobSatisfaction | MaritalStatus | MonthlyIncome | MonthlyRate | NumCompaniesWorked | Over18 | OverTime | PercentSalaryHike | PerformanceRating | RelationshipSatisfaction | StandardHours | StockOptionLevel | TotalWorkingYears | TrainingTimesLastYear | WorkLifeBalance | YearsAtCompany | YearsInCurrentRole | YearsSinceLastPromotion | YearsWithCurrManager |
|-----|-----------|----------------|-----------|------------|------------------|-----------|----------------|--------------|---------------|-----------------------|--------|------------|----------------|----------|---------|-----------------|---------------|--------------|------------|-------------------|-------|----------|------------------|------------------|------------------------|--------------|------------------|------------------|----------------------|-----------------|----------------|-------------------|-----------------------|---------------------|
| 41  | Yes       | Travel_Rarely  | 1102      | Sales      | 1                | 2         | Life Sciences  | 1            | 1             | 2                   | Female | 94         | 3              | 2        | Sales Executive | 4             | Single       | 5993         | 19479      | 8                 | Y     | Yes      | 11               | 3                | 1                      | 80           | 0                | 8                | 0                    | 1               | 6              | 4                | 0                       | 5                   |
| 49  | No        | Travel_Frequently | 279     | Research & Development | 8 | 1 | Life Sciences | 1 | 2 | 3 | Male | 61 | 2 | 2 | Research Scientist | 2 | Married | 5130 | 24907 | 1 | Y | No | 23 | 4 | 4 | 80 | 1 | 10 | 3 | 3 | 10 | 7 | 1 | 7 |
| 37  | Yes       | Travel_Rarely | 1373      | Research & Development | 2 | 2 | Other | 1 | 4 | 4 | Male | 92 | 2 | 1 | Laboratory Technician | 3 | Single | 2090 | 2396 | 6 | Y | Yes | 15 | 3 | 2 | 80 | 0 | 7 | 3 | 3 | 0 | 0 | 0 | 0 |
| 33  | No        | Travel_Frequently | 1392  | Research & Development | 3 | 4 | Life Sciences | 1 | 5 | 4 | Female | 56 | 3 | 1 | Research Scientist | 3 | Married | 2909 | 23159 | 1 | Y | Yes | 11 | 3 | 3 | 80 | 0 | 8 | 3 | 3 | 8 | 7 | 3 | 0 |
| 27  | No        | Travel_Rarely | 591        | Research & Development | 2 | 1 | Medical | 1 | 7 | 1 | Male | 40 | 3 | 1 | Laboratory Technician | 2 | Married | 3468 | 16632 | 9 | Y | No | 12 | 3 | 4 | 80 | 1 | 6 | 3 | 3 | 2 | 2 | 2 | 2 |
| 32  | No        | Travel_Frequently | 1005  | Research & Development | 2 | 2 | Life Sciences | 1 | 8 | 4 | Male | 79 | 3 | 1 | Laboratory Technician | 4 | Single | 3068 | 11864 | 0 | Y | No | 13 | 3 | 3 | 80 | 0 | 8 | 2 | 2 | 7 | 7 | 3 | 6 |
| 59  | No        | Travel_Rarely | 1324       | Research & Development | 3 | 3 | Medical | 1 | 10 | 3 | Female | 81 | 4 | 1 | Laboratory Technician | 1 | Married | 2670 | 9964 | 4 | Y | Yes | 20 | 4 | 1 | 80 | 3 | 12 | 3 | 2 | 1 | 0 | 0 | 0 |
| 30  | No        | Travel_Rarely | 1358      | Research & Development | 24 | 1 | Life Sciences | 1 | 11 | 4 | Male | 67 | 3 | 1 | Laboratory Technician | 3 | Divorced | 2693 | 13335 | 1 | Y | No | 22 | 4 | 2 | 80 | 1 | 1 | 2 | 3 | 1 | 0 | 0 | 0 |
| 38  | No        | Travel_Frequently | 216  | Research & Development | 23 | 3 | Life Sciences | 1 | 12 | 4 | Male | 44 | 2 | 3 | Manufacturing Director | 3 | Single | 9526 | 8787 | 0 | Y | No | 21 | 4 | 2 | 80 | 0 | 10 | 2 | 3 | 9 | 7 | 1 | 8 |


</div>
</div>

</details>

---
## 🔎  Explore data and test model

### The Process is following - [Code & Presentation](https://github.com/beto1810/Predictors-of-mental-health-illness/blob/main/Explore%20data%20and%20test%20model.md#1%EF%B8%8F%E2%83%A3-explore-data-analysis) or [Only Code](https://github.com/beto1810/Predictors-of-mental-health-illness/blob/main/File/Final_Mindx_De1%20(2).ipynb)

- Import Library and dataset
- Explore data
- Correlation Matrix
- Preprocessing - Encoding
- Scaling & Fitting
- Tuning
- Evaluate Model
- Model's Result Comperation

---

# 🧾 What can you practice with this case study?
- Python
  - pandas, numpy,matplotlib,seaborn, sklearn(preprocessing, decision tree, randomforest, adaboost, GradientBoosting.
  - Cleaning, check Null values, transforming.
  - Running model,Scaling model, Fiting model, Testing model. 
  - Loop function, def function.
  - import, save csv file. 

