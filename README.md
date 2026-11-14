# Machine Learning for Building Performance Prediction
# Current Climate 
Evaluating Machine Learning Models for Sustainable Building Design: Energy, Emissions, and Comfort Metrics

Abstract

This study assesses six machine learning regression models—Random Forest (RF), K-Nearest Neighbors (KNN), Support Vector Regression (SVR), Artificial Neural Network (ANN), Extreme Gradient Boosting (XGBoost), and Linear Regression (LR)—for predicting building performance in a 79.35 m² residential unit in Sari, Iran (ASHRAE Zone 3A). The EnergyPlus model, calibrated with three years of utility data (2021–2023) per ASHRAE Guideline 14, used a synthetic dataset of 1826 configurations with 25 input variables. Five metrics were evaluated: Primary Energy Consumption (kWh), CO₂-equivalent Emissions (kg), Indoor Air Quality (IAQ, ppm), Predicted Percentage of Dissatisfied (PPD, %), and Visual Discomfort Hours (VDH, hr). The dataset was split into 60 % training and 40 % testing sets, with performance measured by RMSE, R², and MAPE. RF and XGBoost excelled, achieving test R² values of 0.9188–0.9578, reducing RMSE by up to 31 % compared to LR (R²: 0.35–0.50). Hyperparameter tuning via Grid Search and Bayesian Optimization improved accuracy, with XGBoost reaching an R² of 0.9578 for IAQ. Sensitivity and SHAP analyses highlighted ventilation and HVAC as key drivers. Scenario analysis with 1000 bootstrap iterations showed trade-offs: increased ventilation increased energy use by 110.7 % and emissions by 76.2 % but improved IAQ by 20.3 %. Optimization reduced energy consumption by 34.3 % and emissions by 38.1 %, enhancing comfort. RF and XGBoost are robust for sustainable building design optimization.

# Integrated Framework for Climate-Resilient Building Performance Prediction Using ML and Simulations
# Future Climate Scenarios (2050 & 2080)
Adaptive Machine Learning Framework for Multi-Objective Building Performance Optimization Under Future Climate Scenarios

Abstract

Machine-learning surrogates trained on present-day weather lose accuracy under future climates, yet it remains unclear how much future-climate simulation data is required to restore performance and whether deep transfer learning outperforms updating tree-based models with the same data. This study addresses both questions for a calibrated residential building in Sari, Iran, using 1,826 (present), 909 (2050) and 991 (2080) EnergyPlus simulations (HadCM3 A2) to predict five building-performance indicators: primary energy consumption (PEC), CO₂-equivalent emissions (CO₂e), indoor air quality (IAQ), predicted percentage of dissatisfied (PPD) and visual discomfort hours (VDH). Random Forest, XGBoost and deep neural networks (DNNs) trained on the present climate were applied zero-shot or adapted with 5–100 % of the future training samples (fine-tuning, warm-start boosting, pooled training and training from scratch; ten random splits). Zero-shot degradation increased with the shift of the target distribution (Spearman ρ = 0.84) and was largest for PPD in 2080. Fine-tuned DNNs outperformed non-adapted XGBoost (mean R² 0.88 and 0.85 versus 0.83 and 0.67 in 2050 and 2080), but XGBoost adapted with the same future samples matched or exceeded them at every data budget (mean R² ≈ 0.92 with the full future split). Future-climate data, not the deep architecture, was therefore the decisive factor, and about 10 % of the training split already raised the 2080 R² of XGBoost from 0.67 to 0.82. All models under-predicted high PPD. The findings guide data-efficient adaptation of building-energy and thermal-comfort surrogates under climate change, for one building archetype and one climate pathway.


# Future-Climate Reliability and Data-Efficient Adaptation
# Data-Efficient Adaptation of Building Performance Surrogates under Climate-Induced Domain Shift: Quantifying the Future-Simulation Budget

## Research Overview

Machine-learning (ML) surrogate models are increasingly used to accelerate building performance simulation by approximating computationally expensive physics-based models such as EnergyPlus. However, their reliability under future climate conditions remains insufficiently quantified. Models trained on present-climate data may experience substantial predictive degradation when deployed under future climate regimes due to climate-induced distribution shifts.

This research investigates the reliability of multi-output building-performance surrogates under future climate conditions and quantifies the additional physics-based simulations required to adapt existing models while maintaining predictive performance.

The central research question is:

**How much future-climate simulation data are required to adapt an existing building-performance surrogate while maintaining reliable predictive performance?**

The study focuses on a residential building in Sari, Iran, and evaluates three surrogate-model families: Random Forest, XGBoost and Deep Neural Networks (DNNs).

## Research Objectives

The study has four main objectives:

1. Quantify the predictive degradation of present-climate surrogate models when applied to future climate conditions without retraining.
2. Investigate climate-induced distribution shifts across building-design inputs and performance targets.
3. Evaluate the data efficiency of different adaptation strategies, including future-only training, pooled training and DNN transfer learning.
4. Translate future-data requirements into explicit EnergyPlus simulation budgets to support computational planning for climate-resilient building-performance assessment.

## Simulation Datasets and Climate Scenarios

The computational framework is based on three climate-specific synthetic datasets generated using EnergyPlus.

| Climate condition | Total simulations |
|---|---:|
| Present climate | 1,826 |
| 2050 climate | 909 |
| 2080 climate | 991 |

Future weather files were generated using **CMIP6-based climate projections under the SSP2-4.5 scenario**, representing future climate conditions for 2050 and 2080.

The same 107 building-design and system-input features are considered across the climate conditions. Five performance indicators are predicted simultaneously:

- Primary Energy Consumption (PEC)
- CO₂-equivalent emissions
- Indoor Air Quality (zone CO₂ concentration)
- Thermal Comfort (Predicted Percentage of Dissatisfied, PPD)
- Visual Discomfort Hours (VDH)

The future-climate datasets are divided into adaptation and independent testing subsets. Based on the reported simulation-budget fractions, the adaptation pools contain 727 simulations for 2050 and 793 simulations for 2080, while the remaining samples are reserved for independent testing.

## Experimental Framework

Five modelling regimes are investigated to assess predictive reliability and adaptation efficiency.

**1. Zero-shot deployment**

Models trained exclusively on present-climate simulations are directly evaluated on independent future-climate test sets without retraining or adaptation. This experiment quantifies the predictive penalty associated with climate-induced domain shift.

**2. Future-only training**

Models are trained from scratch using limited subsets of future-climate simulations. This regime provides a baseline for evaluating whether transfer learning offers an advantage over training with future data alone.

**3. Pooled present- and future-climate training**

Present- and future-climate samples are combined to retrain the tree-based models. This strategy investigates whether retaining source-domain data improves adaptation efficiency and predictive generalisation.

**4. DNN transfer learning**

A DNN initially trained on present-climate simulations is fine-tuned using progressively larger subsets of future-climate data. Different layer-freezing strategies are evaluated to investigate how much of the learned source-domain representation can be retained during adaptation.

**5. Full-future reference**

Models trained using the complete future-climate adaptation pool provide a reference for quantifying the performance recovered by data-efficient adaptation strategies. This reference is based on the adaptation pool rather than the independent future-climate test set.

## Future-Simulation Budget

A central contribution of this research is the explicit conversion of future-data fractions into additional EnergyPlus simulations.

The following adaptation fractions are evaluated:

| Adaptation fraction | 2050 simulations | 2080 simulations |
|---|---:|---:|
| 5% | 36 | 40 |
| 10% | 73 | 79 |
| 20% | 145 | 159 |
| 30% | 218 | 238 |
| 50% | 364 | 397 |
| 75% | 545 | 595 |
| 100% | 727 | 793 |

These budgets refer to the future-climate adaptation pools, not the complete future datasets.

This approach makes it possible to evaluate surrogate adaptation not only in terms of predictive performance but also in terms of the additional computational effort required to generate physics-based simulations.

## Climate-Induced Domain Shift and Model Reliability

Climate-induced domain shift is examined through complementary statistical and predictive-performance analyses, including:

- Squared Maximum Mean Discrepancy (MMD²) for feature-distribution differences.
- Changes in target distributions across climate conditions.
- Zero-shot R² degradation.
- Root Mean Squared Error (RMSE) and Mean Absolute Error (MAE).
- Mean Bias Error (MBE).
- Coefficient of Variation of RMSE (CV(RMSE)).
- Spearman rank correlation.
- Bootstrap-based 95% confidence intervals for selected configurations.

The analysis treats surrogate reliability as a multi-output and target-dependent problem. In particular, thermal comfort prediction (PPD) exhibits substantially greater sensitivity to future climate conditions than indoor-air-quality prediction under the tested scenarios.

## Main Findings

The results demonstrate several important findings within the investigated building and climate-scenario setting:

- Present-climate surrogate models experience measurable predictive degradation when deployed under future climates without adaptation.
- Mean relative R² losses across the five prediction targets are approximately 10–27% under the 2050 climate and 29–33% under the 2080 climate, depending on the model family.
- Thermal comfort prediction (PPD) exhibits the most substantial degradation, including pronounced underprediction for highly uncomfortable designs.
- Indoor-air-quality prediction is comparatively stable under the tested climate conditions.
- DNN transfer learning provides substantial data-efficiency benefits when only limited future-climate simulations are available.
- At low future-data fractions, transfer learning can outperform training a DNN from scratch.
- With 36–40 future simulations, corresponding to 5% of the respective adaptation pools, DNN transfer learning achieves approximately 94% and 89% of the best full-future reference R² for 2050 and 2080, respectively.
- Increasing the adaptation fraction to 30% raises these values to approximately 100% and 98%, respectively.
- For PPD, fine-tuning with 30% of the future adaptation data reduces MAE by approximately 50% under 2050 conditions and 70% under 2080 conditions.
- Pooled present- and future-climate training improves the data efficiency of tree-based models, particularly XGBoost.

Together, these findings demonstrate that the number of additional physics-based simulations required for surrogate adaptation can be quantified empirically, and that adaptation requirements differ substantially across building-performance indicators.

## Reproducibility and Computational Materials

The research is supported by publicly archived computational materials intended to facilitate reproducibility and further methodological development.

The project repository includes the following research components:

- Synthetic present- and future-climate datasets.
- Data preprocessing and preparation procedures.
- Random Forest and XGBoost implementations.
- Deep Neural Network architectures and training workflows.
- Transfer-learning and layer-freezing experiments.
- Future-data fraction and simulation-budget analyses.
- Climate-induced domain-shift assessment.
- SHAP-based model interpretability.
- Bootstrap uncertainty quantification.
- Predictive-performance evaluation scripts.
- Data visualisation procedures.
- Model configurations and hyperparameter settings.

The future-climate experiments use independent test sets and repeated random seeds to reduce dependence on individual stochastic training runs.

## Data and Code Availability

The computational materials associated with this research are archived through GitHub and Zenodo.

**Zenodo DOI:** 10.5281/zenodo.20958845

**GitHub repository:** F-Dhghn/Building-Performance-ML-2025

The repository supports further research in:

- Building-performance surrogate modelling.
- Machine learning for EnergyPlus acceleration.
- Climate-resilient building simulation.
- Domain shift and predictive reliability.
- Transfer learning and data-efficient adaptation.
- Future-climate simulation budgeting.
- Multi-output building-performance prediction.

## Research Scope and Limitations

The future-climate experiments are based on synthetic EnergyPlus datasets generated for a single residential building in Sari, Iran. Future weather conditions are represented using CMIP6-based climate projections under the SSP2-4.5 scenario.

Consequently, the reported simulation budgets should be interpreted as **empirical, case-specific estimates**, rather than universal requirements for surrogate adaptation across building types, locations or climate projections.

The study also uses independent rather than paired design samples across climate conditions. Although the analysis examines distribution shifts and controls for selected differences in HVAC configurations and design composition, further validation using paired simulations would strengthen the attribution of predictive degradation specifically to climate change.

Future research directions include:

- Multi-GCM and multi-scenario climate ensembles.
- Evaluation across additional building typologies and climate regions.
- Additional CMIP6 climate projections and emissions pathways.
- Extreme-weather and heat-wave stress testing.
- Active-learning strategies for selecting informative future simulations.
- Advanced domain-adaptation and multi-source learning methods.
- Physics-informed machine learning.
- Validation against monitored real-building performance and occupant-related data.

## Research Theme

**Data-efficient and trustworthy machine-learning surrogates for climate-resilient building performance assessment, with emphasis on climate-induced domain shift, thermal comfort and future-simulation budgeting.**
