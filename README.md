# Machine Learning for Building Performance Prediction
# Current Climate 
Evaluating Machine Learning Models for Sustainable Building Design: Energy, Emissions, and Comfort Metrics

Abstract

This study assesses six machine learning regression models—Random Forest (RF), K-Nearest Neighbors (KNN), Support Vector Regression (SVR), Artificial Neural Network (ANN), Extreme Gradient Boosting (XGBoost), and Linear Regression (LR)—for predicting building performance in a 79.35 m² residential unit in Sari, Iran (ASHRAE Zone 3A). The EnergyPlus model, calibrated with three years of utility data (2021–2023) per ASHRAE Guideline 14-2014, used a synthetic dataset of 1,826 configurations with 25 input variables. Five metrics were evaluated: Primary Energy Consumption (kWh), CO₂-equivalent Emissions (kg), Indoor Air Quality (IAQ, ppm), Predicted Percentage of Dissatisfied (PPD, %), and Visual Discomfort Hours (VDH, hr). The dataset was split into 60% training and 40% testing sets, with performance measured by RMSE, R², and MAPE. RF and XGBoost excelled, achieving test R² values of 0.9188–0.9578, reducing RMSE by up to 31% compared to LR (R²: 0.35–0.50). Hyperparameter tuning via Grid Search and Bayesian Optimization improved accuracy, with XGBoost reaching an R² of 0.9578 for IAQ. Sensitivity and SHAP analyses highlighted ventilation and HVAC as key drivers. Scenario analysis with 1,000 bootstrap iterations showed trade-offs: increased ventilation increased energy use by 110.7% and emissions by 76.2% but improved IAQ by 20.3%. Optimization reduced energy consumption by 34.3% and emissions by 38.1%, enhancing comfort. RF and XGBoost are robust for sustainable building design optimization.

# Integrated Framework for Climate-Resilient Building Performance Prediction Using ML and Simulations
# Future Climate Scenarios (2050 & 2080)
Adaptive Machine Learning Framework for Multi-Objective Building Performance Optimization Under Future Climate Scenarios

Abstract

Buildings are major contributors to global energy consumption and greenhouse-gas emissions, while climate change is expected to intensify cooling demand, carbon emissions, and occupant discomfort. Conventional building-performance simulations are computationally intensive, and machine-learning models trained solely on present-climate data may lose reliability under future conditions where representative training data are scarce. This study develops a transfer-learning-based machine-learning framework for predicting five key performance indicators—primary energy consumption, CO₂-equivalent emissions, indoor air quality, thermal discomfort, and visual discomfort—under 2050 and 2080 climate scenarios. A synthetic dataset was generated using EnergyPlus and jEPlus+EA for a calibrated residential building in Sari, Iran. Random Forest, XGBoost, and Deep Neural Network models were trained on present-climate data and adapted to future climates using limited future samples. A dedicated validation experiment compared zero-shot models with those incorporating 25% and 60% future-climate data. Predictive performance was assessed using MAE, RMSE, R², and bootstrap-based 95% confidence intervals. Incorporating future-climate information substantially improved prediction accuracy for energy, emissions, and thermal comfort, with greater benefits under the 2080 scenario. Tree-based models, particularly XGBoost, provided more consistent and stable performance than the DNN configurations. The surrogate models reduce evaluation time from hours to seconds. SHAP analysis identified ventilation, HVAC system type, and envelope characteristics as key drivers, while scenario analysis revealed important trade-offs among the five objectives. The proposed framework offers an explainable, uncertainty-aware, and computationally efficient approach for climate-adaptive building-performance prediction and multi-objective decision support.

# Future-Climate Reliability and Data-Efficient Adaptation
# Data-Efficient Adaptation of Building Performance Surrogates under Climate-Induced Domain Shift: Quantifying the Future-Simulation Budget

Abstract

Machine learning (ML) surrogate models are increasingly used to accelerate building performance simulation, yet their reliability under future climate conditions remains poorly quantified. Climate change induces a distribution shift between the present-climate data on which models are typically trained and the future-climate regimes in which they are expected to operate. This study quantifies that shift within the studied building and climate-scenario setting and evaluates the future-simulation budgets associated with several adaptation strategies for recovering predictive performance. Three multi-output surrogate families, Random Forest, XGBoost and a deep neural network (DNN), are trained on a present-climate parametric dataset (1,826 EnergyPlus simulations) and evaluated on independent 2050 and 2080 test sets generated under the SRES A2 scenario (HadCM3 / CCWorldWeatherGen). Five simultaneous targets are considered: primary energy consumption (PEC), CO₂-equivalent emissions, indoor air quality (zone CO₂), thermal comfort (PPD) and visual discomfort hours (VDH). Experimental regimes comprise zero-shot deployment, future-only (scratch) training, pooled present+future training, DNN transfer learning with partial layer freezing, and a full-future reference. Performance is reported with R², RMSE, MAE, bias (MBE), CV(RMSE) and Spearman rank correlation, together with bootstrap 95 % confidence intervals. Zero-shot application of present-climate models yields mean relative R² losses (averaged over the five targets) of approximately 10–27 % for 2050 and 29–33 % for 2080; losses for individual model–target pairs can be substantially larger (e.g., thermal comfort under 2080).

The central research question is:

How much future-climate simulation data are required to adapt an existing building-performance surrogate while maintaining reliable predictive performance?

The study evaluates three surrogate families:

Random Forest

XGBoost

Deep Neural Network (DNN)

A total of three synthetic climate-specific datasets are considered:

Climate condition	Simulations
Present climate	1,826
2050	909
2080	991
The same 107 design and system input features are used across the climate conditions, while five performance targets are predicted simultaneously:

Primary Energy Consumption (PEC)

CO₂-equivalent emissions

Indoor Air Quality (zone CO₂)

Predicted Percentage of Dissatisfied (PPD)

Visual Discomfort Hours (VDH)

Future weather files are generated using CCWorldWeatherGen v1.9, based on a Meteonorm baseline weather file and HadCM3 climate-change factors under the SRES A2 scenario.

Experimental Framework
The future-climate experiments compare five modelling regimes:

1. Zero-shot deployment
Models trained exclusively on present-climate simulations are directly applied to future-climate test data without adaptation.

2. Future-only training
Models are trained from scratch using only a limited number of future-climate simulations.

3. Pooled training
Present- and future-climate samples are combined and used to retrain the tree-based models.

4. DNN transfer learning
A DNN trained on present-climate data is fine-tuned using a limited number of future-climate simulations.

Different layer-freezing strategies are also evaluated to examine how much of the source representation can be retained during adaptation.

5. Full-future reference
Models trained using the complete future-climate adaptation pool provide a reference for evaluating the performance recovered by data-efficient adaptation.

Future Simulation Budget
A central feature of this study is the explicit conversion of future-data fractions into additional EnergyPlus simulations.

Future adaptation is evaluated at:

5%

10%

20%

30%

50%

75%

100%

For example:

5% = 36 simulations for 2050

5% = 40 simulations for 2080

30% = 218 simulations for 2050

30% = 238 simulations for 2080

This allows model adaptation to be interpreted not only in terms of data percentage, but also in terms of the computational budget required to generate additional physics-based simulations.

Climate-Induced Domain Shift
The study evaluates predictive degradation when present-climate surrogates are deployed under future climates.

Domain changes are examined using:

Squared Maximum Mean Discrepancy (MMD²)

Target-distribution changes

Zero-shot R² degradation

RMSE and MAE

Mean Bias Error (MBE)

CV(RMSE)

Spearman rank correlation

Bootstrap confidence intervals are also calculated for key zero-shot configurations.

The analysis indicates that climate-induced performance degradation is target-dependent. Thermal comfort prediction, particularly PPD, shows substantially greater degradation than indoor-air-quality prediction under the tested future-climate scenarios.

The study therefore treats surrogate reliability as a multi-output and target-dependent problem, rather than assuming that climate shift affects all building-performance indicators equally.

Main Findings
Under the tested building and climate-scenario setting:

Present-climate models experience measurable degradation when deployed zero-shot under future climates.

Mean relative R² losses are approximately 10–27% for 2050 and 29–33% for 2080, depending on model family.

Thermal comfort (PPD) exhibits particularly strong degradation under the 2080 climate.

Indoor-air-quality prediction is comparatively stable.

DNN transfer learning provides substantial data-efficiency benefits when future-climate data are scarce.

At very low future-data fractions, transfer learning can substantially outperform DNN training from scratch.

Pooled present+future training improves the data efficiency of tree-based models, particularly XGBoost.

The adaptation framework explicitly links predictive recovery to the number of additional EnergyPlus simulations required.

The results are intended to provide an empirical basis for budgeting future-climate simulations when adapting building-performance surrogate models.

Reproducibility
This repository provides the computational materials required to reproduce the reported analyses, including:

Synthetic datasets

Data preprocessing procedures

Random Forest implementation

XGBoost implementation

Deep Neural Network implementation

Transfer-learning workflows

Layer-freezing experiments

Data-efficiency analysis

Domain-shift analysis

SHAP-based interpretability

Bootstrap uncertainty quantification

Performance evaluation scripts

Visualisation scripts

Model configuration and hyperparameter settings

The future-climate study uses fixed test sets and repeated random seeds to improve reproducibility and reduce dependence on a single stochastic training run.

Data and Code Availability
The synthetic datasets and computational materials associated with this research are publicly archived through GitHub and Zenodo.

Zenodo DOI:
10.5281/zenodo.20958845

GitHub:
F-Dhghn/Building-Performance-ML-2025

The repository is intended to support reproducible research on:

Building-performance surrogate modelling

Machine learning for EnergyPlus acceleration

Climate-resilient building simulation

Domain shift and model reliability

Transfer learning

Data-efficient adaptation

Simulation-budget optimisation

Multi-objective building performance prediction

Research Scope and Limitations
The future-climate experiments are based on synthetic EnergyPlus datasets generated for a controlled building and climate-scenario setting. Future weather conditions are represented using the HadCM3 / SRES A2 climate pathway through CCWorldWeatherGen.

Accordingly, the reported adaptation budgets should be interpreted as scenario- and case-specific empirical results, rather than universal simulation requirements.

Future extensions include:

Multi-GCM and multi-scenario climate ensembles

CMIP5/CMIP6 climate projections

Additional building typologies and climate regions

Extreme-weather and heat-wave stress testing

Active learning for selecting informative future simulations

Multi-source and advanced domain-adaptation methods

Physics-informed machine learning

Validation against monitored real-building data

Data-Efficient Adaptation of Building Performance Surrogates under Climate-Induced Domain Shift: Quantifying the Future-Simulation Budget.

Research Theme
EnergyPlus → Machine Learning → Domain Shift → Transfer Learning → Climate-Resilient Building Performance

The broader research objective is to develop computationally efficient and scientifically interpretable surrogate-modelling frameworks capable of supporting building design and optimisation under changing climatic conditions.
