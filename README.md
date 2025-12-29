# Laptop Price Prediction - Regression Project

## Project Overview
The goal of this project is to develop a machine learning model that can accurately predict laptop prices based on historical data. Regression techniques are employed to analyze the relationship between multiple features and the target variable, which is the laptop price. The aim is to achieve a model performance with an R² score above 0.85 where possible, ensuring reliable predictions.

This project demonstrates the complete pipeline of a regression-based predictive model, including data collection, cleaning, feature engineering, model training, evaluation, and comparison.

---

## Dataset
The dataset contains information about 1303 laptops with the following features:

- **Company:** Brand of the laptop  
- **TypeName:** Laptop type (e.g., Ultrabook, Gaming, Notebook)  
- **RAM:** Amount of RAM in GB  
- **CPU:** Processor type and brand  
- **GPU:** Graphics card brand and type  
- **OS:** Operating system (Windows, Mac, Linux, or No OS)  
- **ScreenResolution:** Resolution of the laptop display  
- **Touchscreen:** Boolean indicating if the laptop has a touchscreen  
- **IPS:** Boolean indicating if the laptop display is IPS  
- **Weight:** Laptop weight in kg  
- **Price:** Target variable (laptop price in USD)  

---

## Data Preprocessing and Feature Engineering
Before modeling, the dataset was preprocessed to ensure high-quality input for the models:

1. **Handling Categorical Variables:** CPU and GPU brands were grouped by manufacturer to reduce the number of unique categories. The OS feature was categorized into major groups.  
2. **Extracting Display Features:** Information such as touchscreen capability and IPS technology was extracted from the `ScreenResolution` field.  
3. **Numeric Conversion:** RAM, storage (HDD/SSD), and weight were converted into numeric formats suitable for regression models.  
4. **Outlier Detection:** Boxplots and visualizations were used to detect and handle extreme price values to improve model robustness.  
5. **Scaling:** Certain features like weight and screen PPI were scaled to improve model performance.  

---

## Exploratory Data Analysis
Key insights from the dataset:

- **Price vs. RAM & Storage:** Laptops with higher RAM and SSD storage tend to have significantly higher prices.  
- **Price vs. Display:** Touchscreen and IPS displays contribute to higher prices. Higher pixel density (PPI) is positively correlated with price.  
- **Brand Influence:** Premium brands generally have higher price ranges.  
- **CPU/GPU Influence:** High-performance CPUs and dedicated GPUs increase the price substantially.  

---

## Model Training and Evaluation
Several regression models were trained and evaluated on the dataset. The performance metrics used were:

- **R² (Coefficient of Determination):** Measures how well the model explains variance in the target variable.  
- **RMSE (Root Mean Squared Error):** Measures the standard deviation of prediction errors.  
- **MAE (Mean Absolute Error):** Measures the average magnitude of prediction errors.  

| Model                  | R²        | RMSE           | MAE           |
|------------------------|-----------|----------------|---------------|
| **XGBRegressor**       | 0.8419    | 15096.92       | 9218.61       |
| Gradient Boosting      | 0.8369    | 15333.85       | 10228.22      |
| Decision Tree          | 0.7723    | 18120.40       | 11984.12      |
| Lasso                  | 0.7682    | 18282.86       | 12666.22      |
| Linear Regression      | 0.7680    | 18287.92       | 12676.87      |
| Ridge                  | 0.7578    | 18688.66       | 12756.78      |
| SGD                    | 0.7436    | 19228.89       | 12987.21      |
| Extra Tree             | 0.6834    | 21365.83       | 12728.68      |
| KNeighborsRegressor    | 0.6720    | 21747.50       | 17869.24      |
| AdaBoost               | 0.6476    | 22542.54       | 13298.22      |
| ElasticNet             | 0.3433    | 30770.92       | 21230.25      |
| SVR                    | -0.0278   | 38495.85       | 26379.82      |
| MLP Regressor          | -2.2826   | 68797.72       | 57455.39      |

**Key Observations:**

- The highest performing models are **XGBRegressor** (R² = 0.8419) and **Gradient Boosting** (R² = 0.8369).  
- Linear models such as Linear Regression, Lasso, and Ridge performed moderately well but could not capture non-linear relationships effectively.  
- SVR and MLP Regressor performed poorly, likely due to inadequate hyperparameter tuning or data scaling issues.  

---

## Conclusion
- The most influential features on laptop price are **RAM, SSD capacity, CPU & GPU brand, display resolution (PPI), touchscreen, and IPS technology**.  
- Tree-based ensemble models such as **XGBRegressor** and **Gradient Boosting** provide the most accurate predictions.  
- Future work could include hyperparameter optimization, feature selection, and testing on larger datasets to further improve model accuracy.  

---
