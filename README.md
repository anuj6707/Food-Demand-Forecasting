# Food Demand Forecasting using Machine Learning

## Project Overview

This project focuses on forecasting food demand using machine learning regression techniques.

The objective is to predict the number of meal orders (`num_orders`) based on historical demand patterns, pricing strategies, promotional campaigns, and fulfillment center characteristics.

Multiple machine learning models were implemented and compared to identify the most effective approach for demand forecasting.

---

## Business Problem

Accurate demand forecasting is critical for food delivery companies, cloud kitchens, restaurants, and supply chain operators.

Poor forecasts can lead to:

* Food waste
* Inventory shortages
* Excess operational costs
* Poor customer experience
* Inefficient workforce planning

The goal of this project is to build predictive models that help estimate future meal demand and support data-driven operational planning.

---

## Dataset Description

The dataset contains historical meal order information along with pricing, promotion, and fulfillment center details.

### Features

#### Time Information

* Week Number

#### Pricing Information

* Base Price
* Checkout Price

#### Promotional Information

* Homepage Featured
* Emailer Promotion

#### Product Information

* Meal ID

#### Fulfillment Center Information

* Center ID

### Target Variable

```text
num_orders
```

Number of meal orders placed during a given week.

---

## Data Preprocessing

### Data Cleaning

* Missing value inspection
* Data validation
* Feature consistency checks

### Feature Engineering

#### Discount Percentage

```python
discount = (
    base_price - checkout_price
) / base_price
```

Measures the percentage discount applied to a meal.

#### Promotional Discount

```python
promo_discount = (
    discount
    * homepage_featured
    * emailer_for_promotion
)
```

Captures the interaction between discounts and promotional campaigns.

This feature was designed to estimate the amplified impact of marketing-driven discounts.

---

### Categorical Encoding

High-cardinality categorical variables were encoded using One-Hot Encoding.

```python
pd.get_dummies(
    df,
    columns=[
        "meal_id",
        "center_id"
    ]
)
```

Final dataset:

```text
456,548 observations
134 features
```

---

## Exploratory Data Analysis

Several visualizations were created to understand demand behavior and identify important relationships.

### Analysis Performed

* Correlation Heatmaps
* Weekly Demand Trends
* Demand vs Discount Analysis
* Demand vs Promotional Discount Analysis
* Feature Importance Analysis
* Promotion Impact Analysis

---

# Models Implemented

## 1. Linear Regression

Used as the baseline forecasting model.

### Results

```text
R² ≈ 0.50
```

Observations:

* Captured broad demand trends
* Limited ability to model nonlinear behavior

---

## 2. Ridge Regression

Applied L2 regularization to reduce model complexity.

### Results

```text
R² ≈ 0.49
```

Best Alpha:

```text
5
```

Observations:

* Similar performance to Linear Regression
* Improved coefficient stability

---

## 3. Lasso Regression

Applied L1 regularization for feature selection.

### Results

```text
R² ≈ 0.50
```

Observations:

* Automatically reduced less useful features
* Performance remained similar to other linear models

---

## 4. K-Nearest Neighbors Regression

KNN predicts demand based on similar historical observations.

Feature scaling was applied using StandardScaler.

### Results

```text
R² ≈ 0.76
MSE ≈ 36,875
```

Observations:

* Significant improvement over linear models
* Captured nonlinear demand patterns
* Demonstrated the importance of local relationships

---

## 5. Random Forest Regression

Random Forest was implemented to capture complex interactions between pricing, promotions, meals, and fulfillment centers.

### Results

```text
Train R² ≈ 0.98
Test R² ≈ 0.83
MSE ≈ 25,482
```

Observations:

* Best-performing model
* Strong predictive accuracy
* Successfully captured nonlinear demand drivers
* Some overfitting observed but maintained strong generalization performance

---

# Model Comparison

| Model                    | R² Score |
| ------------------------ | -------- |
| Linear Regression        | ~0.50    |
| Ridge Regression         | ~0.49    |
| Lasso Regression         | ~0.50    |
| KNN Regression           | ~0.76    |
| Random Forest Regression | ~0.83    |

---

# Feature Importance Analysis

Random Forest feature importance revealed several major demand drivers.

Top Features Included:

| Feature        | Importance |
| -------------- | ---------- |
| Checkout Price | 0.17       |
| Promo Discount | 0.08       |
| Meal ID 2290   | 0.08       |
| Discount       | 0.06       |
| Week           | 0.06       |
| Base Price     | 0.06       |

Key finding:

Pricing and promotional variables were among the strongest predictors of customer demand.

---

# Key Business Insights

### Pricing Directly Influences Demand

Checkout price was identified as the single most important feature.

This suggests that pricing strategy plays a critical role in determining customer ordering behavior.

---

### Promotions Increase Demand

The engineered promotional discount feature emerged as one of the most important variables.

Combining discounts with promotional exposure significantly improved demand generation.

---

### Certain Meals Consistently Drive Orders

Specific meal categories demonstrated consistently high demand regardless of promotion levels.

This information can support inventory planning and menu optimization.

---

### Demand Patterns Are Highly Nonlinear

The large performance gap between linear models and Random Forest indicates that food demand is influenced by complex nonlinear relationships.

---

# Business Applications

The forecasting system can be used to:

* Predict future meal demand
* Optimize inventory management
* Reduce food waste
* Improve workforce scheduling
* Support promotional planning
* Improve supply chain efficiency

---

# Technologies Used

* Python
* Pandas
* NumPy
* Scikit-Learn
* Matplotlib
* Seaborn

---

# Machine Learning Concepts Demonstrated

* Regression Modeling
* Linear Regression
* Ridge Regression
* Lasso Regression
* KNN Regression
* Random Forest Regression
* Feature Engineering
* Hyperparameter Tuning
* GridSearchCV
* Feature Importance Analysis
* Model Comparison

---

# Future Improvements

* XGBoost Regressor
* Gradient Boosting
* LightGBM
* Time Series Forecasting Models
* Advanced Feature Engineering
* Flask Deployment

---

# Conclusion

This project compared multiple machine learning approaches for food demand forecasting.

While traditional linear models achieved moderate predictive performance, ensemble methods dramatically improved forecasting accuracy.

Random Forest Regression achieved the strongest performance with a test R² score of approximately 0.83, demonstrating the importance of nonlinear modeling techniques for real-world demand forecasting problems.

The results highlight how pricing strategies, promotions, and product characteristics can be leveraged to improve forecasting accuracy and operational decision-making.

