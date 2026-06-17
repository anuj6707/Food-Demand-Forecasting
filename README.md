# Food Demand Forecasting using Machine Learning 📈🍽️

## Overview

This project focuses on forecasting food demand using machine learning techniques.

The goal is to predict the number of meal orders (`num_orders`) based on historical demand data, meal characteristics, pricing information, promotional campaigns, and fulfillment center attributes.

Multiple regression algorithms were implemented and compared to identify the most effective approach for forecasting food demand.

---

## Business Problem

Accurate demand forecasting is essential for:

* Inventory management
* Supply chain optimization
* Reducing food waste
* Workforce planning
* Promotional strategy planning

Poor demand forecasting can lead to overstocking, shortages, increased costs, and reduced customer satisfaction.

This project aims to build predictive models that can estimate future meal demand using historical operational data.

---

## Dataset Features

The dataset contains information related to:

### Meal Information

* Meal ID
* Category
* Cuisine

### Pricing Information

* Base Price
* Checkout Price

### Promotional Information

* Homepage Featured
* Emailer Promotion

### Fulfillment Center Information

* Center ID
* Region and Operational Attributes

### Time Information

* Week Number

### Target Variable

* Number of Orders (`num_orders`)

---

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-Learn
* Matplotlib
* Seaborn

---

## Data Preprocessing

The following preprocessing steps were performed:

* Missing value inspection
* Feature engineering
* One-hot encoding of categorical variables
* Train-test split
* Feature scaling (for KNN, Ridge, and Lasso)

### One-Hot Encoding

Categorical features were converted into numerical representations:

```python
pd.get_dummies(df, columns=["meal_id", "center_id"])
```

This resulted in 134 total features.

---

## Feature Engineering

### Discount Percentage

A normalized discount feature was created:

```python
discount = (base_price - checkout_price) / base_price
```

This captures the percentage discount offered on a meal.

---

### Promotional Discount Feature

```python
promo_discount = (
    discount
    * homepage_featured
    * emailer_for_promotion
)
```

This feature captures the combined effect of promotions and discounts.

The hypothesis was that discounts become significantly more effective when supported by marketing campaigns.

---

## Exploratory Data Analysis

Several visualizations were created to understand demand patterns.

### Analysis Performed

* Correlation Heatmap
* Weekly Demand Trends
* Demand vs Discount Analysis
* Demand vs Promotional Discount Analysis
* Homepage Promotion Impact
* Email Promotion Impact
* Feature Importance Visualization

---

## Models Implemented

### 1. Linear Regression

Used as the baseline model.

Linear Regression assumes a linear relationship between features and demand.

---

### 2. Ridge Regression

Introduces L2 regularization to reduce model complexity and improve generalization.

Hyperparameter tuning was performed using GridSearchCV.

---

### 3. Lasso Regression

Introduces L1 regularization and performs automatic feature selection.

GridSearchCV was used to determine the optimal regularization strength.

---

### 4. K-Nearest Neighbors (KNN) Regression

KNN predicts demand based on the behavior of similar historical observations.

Because KNN is distance-based, feature scaling was applied using StandardScaler.

Cross-validation was performed to identify an appropriate value of K.

---

## Model Evaluation

Models were evaluated using:

* R² Score
* Mean Squared Error (MSE)

---

## Results

| Model             | R² Score |
| ----------------- | -------- |
| Linear Regression | ~0.50    |
| Ridge Regression  | ~0.49    |
| Lasso Regression  | ~0.50    |
| KNN Regression    | ~0.76    |

### Best Model

**KNN Regression achieved the highest predictive performance.**

```text
R² ≈ 0.76
MSE ≈ 36,875
```

Compared to linear models:

```text
Linear Models: R² ≈ 0.50
KNN Regression: R² ≈ 0.76
```

This significant improvement suggests that food demand exhibits nonlinear patterns that are not fully captured by traditional linear regression approaches.

---

## Key Insights

### Discounts Matter

Higher discounts were generally associated with increased demand.

---

### Promotions Amplify Demand

The interaction between discounts and promotional campaigns had a measurable impact on order volume.

---

### Certain Meals Drive Demand

Feature importance analysis indicated that specific meal IDs consistently contributed to higher order volumes.

---

### Demand Patterns Are Nonlinear

The strong performance of KNN suggests that demand forecasting benefits from learning local patterns and similarities rather than relying solely on global linear relationships.

---

## Project Structure

```text
food-demand-forecasting/
│
├── notebooks/
│   ├── Linear_Regression.ipynb
│   ├── Ridge_Regression.ipynb
│   ├── Lasso_Regression.ipynb
│   └── KNN_Regression.ipynb
│
├── images/
│
├── README.md
│
└── requirements.txt
```

---

## Future Improvements

Potential future enhancements include:

* Decision Tree Regressor
* Random Forest Regressor
* XGBoost Regressor
* Time Series Forecasting Models
* Feature Selection Techniques
* Model Deployment using Flask

---

## Skills Demonstrated

This project demonstrates practical experience with:

* Data Cleaning
* Feature Engineering
* Exploratory Data Analysis
* Regression Modeling
* Hyperparameter Tuning
* Cross Validation
* Model Comparison
* Machine Learning Pipelines
* Business-Oriented Forecasting

---

## Conclusion

This project explored multiple machine learning approaches for forecasting food demand.

While traditional linear models achieved moderate predictive performance, KNN Regression significantly improved forecasting accuracy by capturing nonlinear demand patterns.

The results highlight the importance of model selection and feature engineering when building real-world forecasting systems.

---

## Author

Built as part of a machine learning learning journey focused on:

* Predictive Analytics
* Demand Forecasting
* Feature Engineering
* Model Evaluation
* Applied Machine Learning
