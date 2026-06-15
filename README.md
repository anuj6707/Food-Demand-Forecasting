# Food Demand Forecasting and Promotion Impact Analysis using Regression Models 📈

## Overview

Food demand forecasting is a critical business problem in the food delivery and catering industry. Accurate demand predictions help organizations optimize inventory, reduce food waste, improve customer satisfaction, and increase operational efficiency.

In this project, machine learning regression models were used to predict meal demand based on historical ordering patterns, pricing information, promotional campaigns, meal characteristics, and fulfillment center attributes.

The project focuses on feature engineering, model comparison, and extracting actionable business insights from the data.

---

## Business Problem

Food providers must estimate future demand accurately to avoid:

* Excess inventory and food waste
* Stock shortages
* Increased operational costs
* Poor customer experience

The goal of this project is to predict the number of meal orders (`num_orders`) using available historical and operational data.

---

## Dataset Features

The dataset contains information related to:

* Meal identifiers
* Fulfillment center identifiers
* Pricing information
* Promotional activity
* Weekly demand history
* Meal categories and cuisines

Target Variable:

* `num_orders`

---

## Feature Engineering

Several custom features were created to improve predictive performance.

### Discount Percentage

```python
discount = (base_price - checkout_price) / base_price
```

Captures the relative discount offered on a meal.

### Promotion-Discount Interaction

```python
promo_discount = discount * homepage_featured * emailer_for_promotion
```

Measures the combined effect of promotions and discounts.

---

## Models Evaluated

### Linear Regression

Used as the baseline model.

### Ridge Regression

L2 regularization was applied to reduce coefficient instability and multicollinearity.

### Lasso Regression

L1 regularization was applied for feature selection and coefficient shrinkage.

### Hyperparameter Tuning

GridSearchCV was used to optimize the regularization strength (`alpha`) for Ridge and Lasso Regression.

---

## Results

| Model             | Test R²   |
| ----------------- | --------- |
| Linear Regression | 0.50      |
| Ridge Regression  | 0.49      |
| Lasso Regression  | 0.45-0.49 |

The best-performing model achieved an R² score of approximately **0.50**, explaining around **50% of the variation in food demand**.

---

## Key Findings

### Promotions Matter

The interaction between discounts and promotional campaigns emerged as one of the strongest predictors of demand.

### Pricing Drives Demand

Discount-related features had the largest coefficient magnitudes, indicating a strong relationship between pricing strategy and customer purchasing behavior.

### Meal Identity is Important

Specific meals consistently generated significantly higher demand than others.

### Center Effects Exist

Certain fulfillment centers displayed systematically higher order volumes, suggesting geographic or demographic influences.

### Feature Engineering Had the Biggest Impact

The baseline model initially achieved an R² score of approximately 0.19.

After introducing engineered features and encoding categorical variables, performance improved to approximately 0.50.

This highlights the importance of feature engineering in practical machine learning projects.

---

## Exploratory Data Analysis

The project includes:

* Correlation analysis
* Feature importance analysis
* Weekly demand trend analysis
* Promotion impact analysis
* Discount vs demand analysis
* Heatmap visualizations

---

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-Learn
* Matplotlib
* Seaborn

---

## Future Improvements

Potential next steps include:

* Random Forest Regression
* XGBoost
* LightGBM
* Time-series forecasting techniques
* Model deployment using Streamlit
* Interactive dashboard creation

---

## Project Structure

```text
food-demand-forecasting-regression/
│
├── notebooks/
│   └── food_demand_forecasting.ipynb
│
├── data/
│   └── sample_train.csv
│
├── README.md
│
└── requirements.txt
```

---

## Author

Built as part of a machine learning learning journey focused on regression modeling, forecasting, statistics, and feature engineering.
