# Building-Performance-ML-2025
# Machine Learning for Building Performance Prediction

This repository contains the code and a sample dataset for a study submitted to *Building and Environment*. The study evaluates six machine learning regression models—Random Forest (RF), K-Nearest Neighbors (KNN), Support Vector Regression (SVR), Artificial Neural Network (ANN), Extreme Gradient Boosting (XGBoost), and Linear Regression (LR)—to predict five building performance metrics: Primary Energy Consumption (PEC, kWh), CO₂-equivalent Emissions (kg), Indoor Air Quality (IAQ, ppm), Predicted Percentage of Dissatisfied (PPD, %), and Visual Discomfort Hours (VDH, hr). Using a synthetic dataset of 1,826 design configurations with 25 input variables, RF and XGBoost achieved test R² values of 0.816–0.959, outperforming other models.

## Repository Structure

- `code/`
  - `train_models.py`: Trains and evaluates the six ML models with hyperparameter tuning (Grid Search, Bayesian Optimization).
  - `plot_residuals.py`: Generates violin and scatter plots for residual distributions.
  - `scenario_analysis.py`: Performs scenario analysis with uncertainty quantification (1,000 bootstrap iterations).
  - `shap_analysis.py`: Conducts sensitivity analysis using SHAP values to identify key drivers (e.g., ventilation, HVAC).
- `data/`
  - `sample_data.csv`: A sample dataset (1826 rows) with 25 input variables and five output metrics for testing code.
- `figures/`: Directory for saving output plots (e.g., violin plots, SHAP dependence plots).
- `requirements.txt`: Python dependencies required to run the code.
- `LICENSE`: MIT License for code usage.

## Usage

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/Building-Environment-ML-2025.git
