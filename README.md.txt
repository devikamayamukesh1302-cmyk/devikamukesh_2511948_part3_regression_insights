# Task 1: Understand the Dataset

## Objective

The objective of this task was to understand the business regression dataset, identify the target variable for prediction, classify the variables by type, and determine which variables require cleaning, transformation, or exclusion before building a regression model.

---

# Dataset Overview

The dataset contains monthly retail store performance data collected from multiple stores. It includes operational, marketing, customer, and financial metrics that can be used to analyze and predict business performance.

### Dataset Fields

| Variable | Description |
|----------|-------------|
| store_id | Unique identifier for each store |
| month | Reporting month |
| region | Geographic region of the store |
| store_type | Type of retail store |
| marketing_spend | Monthly marketing expenditure |
| footfall | Number of customer visits |
| avg_discount_pct | Average discount percentage |
| staff_count | Number of employees |
| inventory_availability_pct | Inventory availability percentage |
| competitor_distance_km | Distance to nearest competitor |
| holiday_flag | Indicates whether the month contains a holiday (0 = No, 1 = Yes) |
| customer_rating | Average customer satisfaction rating |
| monthly_sales | Total monthly sales |
| monthly_profit | Total monthly profit |

---

# Dependent Variable (Target Variable)

For this regression analysis, the selected dependent variable is:

**monthly_profit**

This is the value the regression model will predict using the independent variables.

---

# Potential Independent Variables

The following variables are potential predictors of monthly profit:

- marketing_spend
- footfall
- avg_discount_pct
- staff_count
- inventory_availability_pct
- competitor_distance_km
- holiday_flag
- customer_rating
- monthly_sales
- region
- store_type
- month (after feature extraction)

These variables may influence business profitability directly or indirectly.

---

# Numerical Variables

The following variables are numerical:

- marketing_spend
- footfall
- avg_discount_pct
- staff_count
- inventory_availability_pct
- competitor_distance_km
- customer_rating
- monthly_sales
- monthly_profit

---

# Categorical Variables

The following variables are categorical:

- store_id
- region
- store_type
- holiday_flag (Binary)
- month (Date)

---

# Variables That May Need Cleaning or Transformation

| Variable | Required Transformation |
|----------|--------------------------|
| month | Extract Month, Quarter, or Year for analysis |
| region | Convert to dummy variables (One-Hot Encoding) |
| store_type | Convert to dummy variables |
| holiday_flag | Treat as binary categorical variable |
| avg_discount_pct | Ensure percentage format is consistent |
| Numerical variables | Check for missing values and outliers |
| Continuous variables | Standardize or normalize if required |

---

# Variables That May Not Be Useful for Regression

The following variables may not directly contribute to predicting profit:

| Variable | Reason |
|----------|--------|
| store_id | Unique identifier with no predictive value |
| month (raw date) | Should be transformed into useful date features rather than used directly |

---

# Data Preparation Considerations

Before building the regression model, the following preprocessing steps should be completed:

- Check for missing values.
- Identify and handle duplicate records.
- Detect and treat outliers.
- Encode categorical variables.
- Transform date variables into meaningful features.
- Verify numerical data types.
- Standardize numerical variables if required by the regression algorithm.

---

# Summary

The dataset is suitable for business regression analysis. The primary objective is to predict **monthly_profit** using operational, marketing, customer, and sales-related variables. Proper preprocessing, feature engineering, and encoding of categorical variables will improve the accuracy and reliability of the regression model.


Simple Regression 1 (Marketing Spend)
Regression Equation
Sales = 91,167.69 + 0.3625 × Marketing Spend
R-squared
0.0663 (6.63%)
Coefficient
0.3625
P-value
3.03 × 10⁻⁶
Business Interpretation
For every additional 1 unit spent on marketing, sales increase by approximately 0.36 units, on average. However, marketing spend explains only 6.63% of the variation in sales, indicating a weak relationship.
Useful Variable?
Yes, but weak. The variable is statistically significant (p < 0.05), but its low R² suggests it has limited predictive power on its own

Simple Regression 2 (Footfall)
Regression Equation
Sales = 67,928.67 + 6.6475 × Footfall
R-squared
0.3500 (35.00%)
Coefficient
6.6475
P-value
1.35 × 10⁻³¹
Business Interpretation
For every additional 1 customer (footfall), sales increase by approximately 6.65 units, on average. Footfall explains 35.00% of the variation in sales, indicating a much stronger relationship.
Useful Variable?
Yes. The variable is highly statistically significant (p < 0.05) and has substantially better explanatory power, making it a useful predictor of sales.


Multiple Regression Model 1 Interpretation
Regression Equation
Sales=410682.43−9458.50(Dummy Store Type)+1.1367(Marketing Spend)+29.6126(Footfall)+2293.57(Staff Count)
1. Intercept

Intercept = 410,682.43

Interpretation:

The intercept represents the estimated sales when all independent variables (Dummy Store Type, Marketing Spend, Footfall, and Staff Count) are zero.
Although this situation is unlikely in practice, the intercept provides the baseline value from which the effects of the other variables are measured.
2. Coefficients

          Variable             Coefficient
         Dummy Store Type       -9,458.50
         Marketing spend         1.1367
         Football                29.6126
         Satff Count             2,293.57


3. R-squared

R² = 0.7915 (79.15%)

Interpretation:

The model explains approximately 79.15% of the variation in sales.
This indicates a strong overall fit, suggesting that the selected variables collectively explain most of the differences in sales.

4. P-values

        Variable                 P-value
         Dummy Store Type        0.00055
         Marketing spend         4.89 × 10⁻¹⁵
         Football                6.31 × 10⁻²⁴
         Satff Count             0.0945

Conclusion:

Dummy Store Type, Marketing Spend, and Footfall are statistically significant predictors of sales.
Staff Count does not appear to have a statistically significant effect after accounting for the other variables.

. Direction of Relationships
Variable	Relationship
Dummy Store Type	Negative
Marketing Spend	Positive
Footfall	Positive
Staff Count	Positive (but statistically weak)

6. Business Meaning of Important Variables
Marketing Spend
Has a positive and statistically significant impact on sales.
Increasing marketing expenditure is associated with higher sales, even after controlling for other factors.
Footfall
Has the strongest positive influence among the predictors.
More customer visits lead to substantially higher sales, making footfall a key driver of business performance.
Dummy Store Type
The negative coefficient indicates that the store type represented by the dummy variable performs worse than the reference store type.
This suggests that store format or type may influence sales and should be considered in business strategy.
7. Statistically Weak Variable
Staff Count
Coefficient: 2,293.57
P-value: 0.0945 (> 0.05)

Interpretation:

Although the coefficient is positive, the relationship is not statistically significant at the 5% level.
The effect of staff count may be influenced by other variables or may not independently explain sales.
Additional investigation or alternative model specifications may be needed before drawing firm conclusions about staffing levels.
Overall Conclusion
The multiple regression model provides a strong fit (R² = 79.15%), explaining a large proportion of the variation in sales.
Marketing Spend and Footfall are the most important positive predictors of sales.
Dummy Store Type has a significant negative effect, indicating differences in sales performance between store types.
Staff Count appears to be a weak predictor because its p-value exceeds the conventional 5% significance level, so its impact should be interpreted with caution.


# Retail Store Sales Regression Analysis

## Business Problem Summary

The objective of this project is to identify the key business factors that influence monthly store sales using regression analysis. The analysis aims to determine which variables have the strongest association with sales, compare simple and multiple regression models, and provide business recommendations that support data-driven decision-making.

---

# Dataset Description

The dataset contains information for **320 retail stores** and includes operational and marketing variables used to predict monthly sales.

### Dataset Variables

* Monthly Sales (Dependent Variable)
* Marketing Spend
* Footfall
* Staff Count
* Store Type
* Dummy Store Type (created for regression analysis)

---

# Dependent and Independent Variables

## Dependent Variable

* **Monthly Sales**

## Independent Variables

* Marketing Spend
* Footfall
* Staff Count
* Dummy Store Type

---

# Regression Approach

Three regression models were developed and evaluated:

### Simple Regression Model 1

* Dependent Variable: Monthly Sales
* Independent Variable: Marketing Spend

### Simple Regression Model 2

* Dependent Variable: Monthly Sales
* Independent Variable: Footfall

### Multiple Regression Model

* Dependent Variable: Monthly Sales
* Independent Variables:

  * Dummy Store Type
  * Marketing Spend
  * Footfall
  * Staff Count

The models were compared using:

* R-squared
* Adjusted R-squared
* P-values
* Coefficient interpretation
* Business relevance

---

# Dummy Variable Approach

Store Type is a categorical variable and was converted into a dummy variable for regression analysis.

* **0 = Reference Store Type**
* **1 = Comparison Store Type**

The dummy coefficient measures the difference in expected sales between the comparison store type and the reference category while holding other variables constant.

---

# Model Comparison Summary

| Model                               |         R² | Key Finding                                                                         |
| ----------------------------------- | ---------: | ----------------------------------------------------------------------------------- |
| Simple Regression (Marketing Spend) | **0.0663** | Marketing spend has a positive but weak relationship with sales.                    |
| Simple Regression (Footfall)        | **0.3500** | Footfall is a stronger predictor of sales than marketing spend.                     |
| Multiple Regression                 | **0.7915** | Provides the highest explanatory power and the best overall predictive performance. |

The multiple regression model explains approximately **79.15%** of the variation in monthly sales and outperforms both simple regression models.

---

# Final Model Selected

**Multiple Regression Model**

### Reasons for Selection

* Highest R² (79.15%)
* Includes multiple business drivers
* Marketing Spend and Footfall are statistically significant predictors
* Captures differences between store types
* Suitable for forecasting and strategic decision-making

---

# Business Recommendation

Based on the regression analysis:

* Increase customer footfall through promotions, loyalty programs, and improved customer experience.
* Continue investing in marketing while regularly evaluating campaign effectiveness.
* Review the performance of different store types and adopt best practices from higher-performing stores.
* Use the multiple regression model to support sales forecasting, budgeting, and resource allocation.
* Collect additional variables such as promotions, seasonality, and customer demographics to further improve predictive accuracy.

---

# Assumptions and Limitations

## Assumptions

* Linear relationships exist between predictors and sales.
* Data is accurate and representative.
* Independent variables are measured consistently.
* Observations are independent.

## Limitations

* Approximately **20.85%** of sales variation remains unexplained.
* External factors such as promotions, seasonality, weather, competition, and economic conditions were not included.
* Staff Count was not statistically significant in the final model.
* Regression identifies statistical associations but does not establish causal relationships.

---

# Screenshots Included

The repository includes the following screenshots as supporting evidence:

* `simple_regression1_output.png`
* `simple_regression2_output.png`
* `multiple_regression_output.png`
* `model_comparison.png`
* `residuals_preview.png`

These screenshots provide evidence of the regression analyses, model comparison, and residual analysis completed during the project.

---

# Project Deliverables

* `analysis/model_comparison.md`
* `analysis/residual_analysis.md`
* `outputs/regression_summary.xlsx`
* `outputs/model_equations.md`
* `outputs/final_recommendation.md`
* `README.md`
* Supporting screenshots

This project demonstrates how regression analysis can be applied to identify important business drivers of sales, compare predictive models, and provide practical recommendations for improving retail performance.



