# Seoul Bike-Sharing Demand Prediction

### End-to-End Data Analytics & Machine Learning Project

## Project Overview

This project analyzes hourly bike-sharing demand in Seoul using Python, exploratory data analysis, and machine learning.

The goal is to understand how temporal patterns, weather conditions, and operational factors relate to bike rental demand and to develop regression models that can estimate hourly rental counts.

The project demonstrates an end-to-end analytical workflow, from data preprocessing and visualization to model optimization, interpretation, and business recommendations.

## Dataset

**Source:** [UCI Machine Learning Repository — Seoul Bike Sharing Demand](https://archive.ics.uci.edu/dataset/560/seoul+bike+sharing+demand)

- **Observations:** 8,760 hourly records
- **Period:** December 2017 – November 2018
- **Target Variable:** Rented Bike Count
- **Features:** Weather conditions, date and time, seasons, holidays, and operational status

The dataset is retrieved programmatically using the `ucimlrepo` Python package.

## Technologies & Skills

**Programming and Analysis:** Python, Pandas, NumPy

**Visualization:** Matplotlib, Seaborn

**Machine Learning:** Scikit-learn, Linear Regression, Random Forest Regression

**Model Validation:** Chronological Train-Test Split, Time-Series Cross-Validation, RandomizedSearchCV

**Model Interpretation:** Permutation Feature Importance, Residual Analysis

**Business Analytics:** Demand Pattern Analysis, Performance Evaluation, Operational Recommendations

## Project Workflow

1. **Data Acquisition & Cleaning:** Retrieve the dataset, validate data quality, and prepare features.
2. **Exploratory Data Analysis:** Investigate rental demand patterns across time, weather conditions, and seasons.
3. **Feature Engineering:** Create cyclical temporal features and encode categorical variables.
4. **Baseline Modeling:** Train and evaluate Linear Regression and Random Forest models.
5. **Cross-Validation:** Apply date-based expanding-window validation to preserve chronological ordering.
6. **Hyperparameter Optimization:** Tune Random Forest using RandomizedSearchCV.
7. **Final Model Evaluation:** Compare models using an independent chronological test set.
8. **Feature Importance:** Identify influential predictors using permutation importance.
9. **Business Insights:** Translate analytical findings into practical recommendations.

## Key Findings

### Demand Patterns

- Overall rental demand peaked around **18:00**, while the lowest demand occurred around **04:00**.
- Weekday average hourly demand was approximately **7.24% higher** than weekend demand.
- Summer recorded the highest average hourly demand at **1,034.07 rentals**, compared with **225.54** in winter.
- Hours with rainfall had substantially lower average rental demand than hours without rainfall.

These findings describe historical associations and do not establish causal relationships.

### Model Performance

Three regression models were evaluated on the same held-out chronological test dataset.

| Model | Test MAE | Test RMSE | Test R² |
|---|---:|---:|---:|
| Linear Regression | 306.48 | 426.22 | 0.5171 |
| Baseline Random Forest | **264.16** | 361.82 | 0.6520 |
| Tuned Random Forest | 269.13 | **357.57** | **0.6601** |

Random Forest substantially outperformed Linear Regression.

Hyperparameter tuning improved test RMSE by **1.17%**, although the baseline Random Forest retained the lowest MAE.

The results highlight the importance of considering multiple evaluation metrics rather than selecting models solely based on R².

### Feature Importance

Permutation importance indicated that hour-of-day information was the strongest predictor group for the tuned Random Forest during the selected chronological validation period.

Other influential features included solar radiation, humidity, day of week, temperature, and rainfall.

## Business Implications

The findings suggest opportunities for:

- Time-aware bike availability and capacity planning.
- Weather-responsive demand forecasting.
- Seasonal resource and maintenance planning.
- Incorporating known operational constraints into forecasting systems.
- Monitoring demand-specific prediction errors.

The current model predicts system-wide hourly rentals. Station-level inventory and geographic data would be required for station-specific fleet rebalancing.

## Limitations

The analysis uses approximately one year of historical records, limiting the evaluation of long-term demand patterns.

The models also rely on weather observations and operational information. Real-world forecasting would require weather forecasts and advance knowledge of operational status.

Chronological validation revealed variability in performance across different periods, and residual analysis identified systematic underprediction in the tuned Random Forest.

Future work could incorporate multiple years of historical data, station-level information, and operational cost-based evaluation.

## How to Run

1. Clone or download this repository.
2. Install the required Python packages.
3. Open the Jupyter Notebook.
4. Run the cells sequentially.

The notebook retrieves the dataset directly from the UCI Machine Learning Repository using `ucimlrepo`.

## Conclusion

This project demonstrates how exploratory analysis, machine learning, chronological validation, and model interpretation can be combined to understand and estimate bike-sharing demand.

Beyond predictive accuracy, the analysis emphasizes reproducibility, model limitations, and the translation of technical results into business-relevant insights.
