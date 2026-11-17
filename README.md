# Automobile Price Prediction Using Machine Learning

## Project Overview

This project develops a machine learning model to predict automobile prices using technical specifications and configuration characteristics of vehicles. The project demonstrates a complete predictive analytics workflow in the automotive domain, including data preparation, feature engineering, model development, evaluation, interpretation, and error analysis.

The objective is to determine whether vehicle characteristics can be used to accurately estimate automobile prices and identify the variables that contribute most strongly to price prediction.

## Problem Statement

Automobile prices depend on multiple factors such as engine size, curb weight, horsepower, fuel economy, vehicle dimensions, and manufacturer. Manually estimating prices from these specifications can be difficult and inconsistent.

This project addresses the problem by developing regression-based machine learning models capable of predicting automobile prices from available vehicle specifications.

## Dataset

The project uses the publicly available UCI Automobile Dataset.

- Original records: 205
- Original variables: 26
- Target variable: `price`
- Records used for modeling: 201
- Modeling features after encoding: 59

Records with missing target prices were removed before modeling.

## Data Preparation

The following preprocessing steps were performed:

1. Records with missing automobile prices were removed.
2. Missing numerical values were handled using median imputation.
3. Missing categorical values were handled using mode imputation.
4. Duplicate records were checked.
5. Categorical variables were converted into numerical variables using one-hot encoding.
6. The dataset was divided into training and testing sets using an 80:20 split with a fixed random state of 42.

After preprocessing, the final modeling dataset contained 201 usable automobile records with no remaining missing values or duplicate rows.

## Feature Engineering

Four domain-informed features were created:

- `power_to_weight` — horsepower relative to vehicle curb weight
- `engine_size_per_cylinder` — engine size relative to the number of cylinders
- `average_mpg` — average of city and highway fuel economy
- `vehicle_volume` — estimated vehicle volume using length × width × height

The engineered features were tested quantitatively rather than being automatically retained.

The comparison showed that the original feature set produced slightly better RMSE and R² values. Therefore, the original feature set was retained for the final model.

## Machine Learning Models

Three regression algorithms were developed and compared:

1. Linear Regression
2. Random Forest Regression
3. Gradient Boosting Regression

### Model Performance

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Gradient Boosting | ₹1,605.94 | ₹2,456.94 | 0.9507 |
| Linear Regression | ₹1,806.31 | ₹2,857.71 | 0.9333 |
| Random Forest | ₹2,280.49 | ₹3,748.02 | 0.8852 |

Gradient Boosting Regression achieved the best overall performance.

## Final Model Results

The final Gradient Boosting model achieved:

- **MAE:** ₹1,605.94
- **RMSE:** ₹2,456.94
- **R²:** 0.9507
- **Predictions within ₹1,000:** 51.2%
- **Predictions within ₹2,000:** 78.0%
- **Predictions within ₹5,000:** 97.6%

The model explained approximately 95.07% of the variation in automobile prices on the test dataset.

## Feature Importance

The most influential variables in the final Gradient Boosting model were:

| Feature | Importance |
|---|---:|
| Curb weight | 0.3904 |
| Engine size | 0.2770 |
| Highway MPG | 0.0671 |
| Horsepower | 0.0566 |
| City MPG | 0.0507 |

Curb weight and engine size were the two strongest contributors to the model's price predictions.

## Error Analysis

Residual analysis was performed to understand prediction errors rather than relying only on overall evaluation metrics.

The final model had:

- Mean residual: ₹609.64
- Minimum residual: -₹3,865.27
- Maximum residual: ₹10,406.44

The largest prediction error was approximately ₹10,406, occurring for a high-priced automobile. This indicates that although the model performs strongly overall, certain high-value vehicles remain more difficult to predict accurately.

## Automotive Applications

The model can potentially support:

- Preliminary vehicle price estimation
- Product benchmarking
- Competitive pricing analysis
- Vehicle configuration assessment
- Data-driven automotive market analysis
- Early-stage pricing decisions

The model should be treated as a decision-support tool rather than a replacement for detailed market-based pricing analysis.

## Project Workflow

Automotive Dataset  
↓  
Data Cleaning  
↓  
Missing Value Treatment  
↓  
Feature Engineering  
↓  
Categorical Encoding  
↓  
Train/Test Split  
↓  
Model Development  
↓  
Model Comparison  
↓  
Evaluation & Error Analysis  
↓  
Final Gradient Boosting Model  
↓  
Automotive Interpretation

## Project Files

- `Week3_Automotive_Price_Prediction.ipynb` — complete Python implementation and analysis
- `automobile_price_prediction_dataset.csv` — dataset used in the project
- `final_model_comparison.csv` — comparison of regression model performance
- `final_gradient_boosting_predictions.csv` — actual and predicted prices from the final model

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Google Colab
- GitHub

## Conclusion

This project demonstrates a complete machine learning workflow for automobile price prediction. Among the three evaluated regression algorithms, Gradient Boosting provided the strongest overall performance, achieving an R² of 0.9507 and an RMSE of ₹2,456.94.

The analysis also demonstrated that adding engineered features does not automatically improve predictive performance. Testing the engineered features quantitatively showed that the original feature set provided better overall RMSE and R² performance.

The results highlight the importance of vehicle characteristics such as curb weight, engine size, fuel economy, and horsepower in automobile price prediction while also identifying areas where prediction errors remain relatively high.
