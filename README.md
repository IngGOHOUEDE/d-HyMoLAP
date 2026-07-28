# d-HyMoLAP: A Dimensionally Consistent Reformulation of the HyMoLAP Rainfall–Runoff Model

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

---

## Overview

This repository contains the complete implementation, analyses, and supporting data accompanying the study:

> **d-HyMoLAP: A Dimensionally Consistent Reformulation of the HyMoLAP Rainfall–Runoff Model**

d-HyMoLAP is a parsimonious conceptual rainfall–runoff model derived from the original HyMoLAP framework by introducing two physically motivated scaling parameters ($Q_s$ and $q_s$), thereby restoring dimensional consistency while preserving the original Lagrangian ordinary differential equation (ODE) formulation.

The model is evaluated on **1,172 catchments** from two large-sample hydrological datasets:

- **CAMELS-FR:** 549 French catchments
- **CAMELS-GB:** 623 British catchments

The repository includes:

- d-HyMoLAP implementation
- Original HyMoLAP implementation
- HBV benchmark implementation
- Large-sample calibration and evaluation
- Calibration period analysis
- Morris global sensitivity analysis
- Parameter attribution analysis
- Performance diagnostics
- SHAP interpretability analyses
- GLUE uncertainty quantification
- Ablation study
- Hydrograph visualization

---

# Repository Structure

```text
.
├── Data.zip
│
├── dHyMoLAP_Model_CAMELS_FR.ipynb
├── dHyMoLAP_Model_CAMELS_GB.ipynb
│
├── HyMoLAP_Model_CAMELS_FR.ipynb
├── HyMoLAP_Model_CAMELS_GB.ipynb
│
├── HBV_Model_CAMELS_FR.ipynb
├── HBV_Model_CAMELS_GB.ipynb
│
├── Models_Comparison_Feature_Selection.ipynb
│
├── dHyMoLAP_Calibration_Period_Analysis.ipynb
│
├── dHyMoLAP_Parameter_Sensitivity_Analysis.ipynb
├── dHyMoLAP_Parameters_Analysis_Interpretability.ipynb
├── dHyMoLAP_Performance_Sensitivity_Analysis.ipynb
│
├── d_HyMoLAP_Performance_Based_Feature_Selection.ipynb
│
├── d_HyMoLAP_GLUE_Uncertainty_Quantification.ipynb
│
├── Ablation_Analysis_dHyMoLAP_CAMELS_FR.ipynb
├── Ablation_Analysis_dHyMoLAP_CAMELS_GB.ipynb
│
├── d_HyMoLAP_Descriptive_Stats_Params_Performance.ipynb
├── d_HyMoLAP_Simulation_Plots_FR_GB_Catchments.ipynb
│
├── requirements.txt
└── README.md
```

---

# Notebook Description

## 1. `dHyMoLAP_Model_CAMELS_FR.ipynb`

### d-HyMoLAP implementation (CAMELS-FR)

Main calibration and evaluation workflow of d-HyMoLAP on the CAMELS-FR dataset.

Main tasks:

- rainfall–runoff simulation
- Nelder–Mead calibration
- training/validation evaluation
- parameter estimation
- performance metrics computation
- export of calibrated parameters and simulations

---

## 2. `dHyMoLAP_Model_CAMELS_GB.ipynb`

### d-HyMoLAP implementation (CAMELS-GB)

Same workflow as above for the CAMELS-GB dataset.

Outputs include:

- calibrated parameters
- validation performance
- simulated discharge
- summary statistics

---

## 3. `HyMoLAP_Model_CAMELS_FR.ipynb`

### Original HyMoLAP implementation (CAMELS-FR)

Implements the original HyMoLAP model to provide the baseline comparison against d-HyMoLAP.

---

## 4. `HyMoLAP_Model_CAMELS_GB.ipynb`

### Original HyMoLAP implementation (CAMELS-GB)

Large-sample implementation of the original HyMoLAP on CAMELS-GB.

---

## 5. `HBV_Model_CAMELS_FR.ipynb`

### HBV benchmark model (CAMELS-FR)

Calibration and evaluation of the HBV conceptual rainfall–runoff model using the same experimental protocol adopted for d-HyMoLAP.

Outputs are used for direct benchmarking.

---

## 6. `HBV_Model_CAMELS_GB.ipynb`

### HBV benchmark model (CAMELS-GB)

HBV implementation on CAMELS-GB under the same calibration and validation protocol.

---

## 7. `Models_Comparison_Feature_Selection.ipynb`

### Comparative SHAP analysis

Identifies the hydroclimatic and physiographic conditions under which

- d-HyMoLAP outperforms HyMoLAP
- d-HyMoLAP outperforms HBV

using classification models together with SHAP explanations.

---

## 8. `dHyMoLAP_Calibration_Period_Analysis.ipynb`

### Calibration period analysis

Investigates the influence of calibration record length on parameter estimation and predictive performance.

The notebook evaluates calibration periods ranging from 3 to 15 years while maintaining a fixed validation period.

---

## 9. `dHyMoLAP_Parameter_Sensitivity_Analysis.ipynb`

### Morris global sensitivity analysis

Performs global parameter sensitivity analysis using the Morris elementary effects method.

Outputs include

- μ*
- σ
- global parameter ranking

for

- μ
- λ
- Qs
- qs

---

## 10. `dHyMoLAP_Parameters_Analysis_Interpretability.ipynb`

### Parameter attribution analysis

Investigates relationships between calibrated parameters and more than 200 catchment descriptors using Spearman rank correlation.

Analyses include

- parameter–attribute correlations
- parameter interdependence
- heatmaps
- top correlated descriptors

---

## 11. `dHyMoLAP_Performance_Sensitivity_Analysis.ipynb`

### Performance diagnostics

Evaluates model performance across hydroclimatic gradients including

- precipitation
- catchment wetness
- snow influence
- hydrological zones
- catchment area

using

- Spearman correlation
- ANOVA
- performance stratification

---

## 12. `d_HyMoLAP_Performance_Based_Feature_Selection.ipynb`

### Performance-based SHAP analysis

Uses Random Forest and XGBoost regression models together with SHAP values to identify the catchment characteristics controlling d-HyMoLAP predictive performance.

This notebook corresponds to the regression-based SHAP analysis presented in the manuscript.

---

## 13. `d_HyMoLAP_GLUE_Uncertainty_Quantification.ipynb`

### GLUE uncertainty analysis

Implements Generalized Likelihood Uncertainty Estimation (GLUE) to quantify parameter uncertainty and predictive uncertainty for representative catchments.

Outputs include

- behavioural parameter distributions
- prediction intervals
- uncertainty envelopes
- parameter identifiability assessment

---

## 14. `Ablation_Analysis_dHyMoLAP_CAMELS_FR.ipynb`

### Ablation analysis (CAMELS-FR)

Evaluates the contribution of the proposed scaling parameters by progressively removing

- $q_s$
- $Q_s$

and comparing four model configurations:

- Phase I: d-HyMoLAP
- Phase II: $q_s=1$
- Phase III: $Q_s=1$
- Phase IV: Original HyMoLAP

---

## 15. `Ablation_Analysis_dHyMoLAP_CAMELS_GB.ipynb`

### Ablation analysis (CAMELS-GB)

Repeats the complete ablation experiment on CAMELS-GB.

---

## 16. `d_HyMoLAP_Descriptive_Stats_Params_Performance.ipynb`

### Descriptive statistics

Summarizes

- calibrated parameter distributions
- model performance
- descriptive statistics
- comparison among HyMoLAP, d-HyMoLAP and HBV

across both datasets.

---

## 17. `d_HyMoLAP_Simulation_Plots_FR_GB_Catchments.ipynb`

### Hydrograph visualization

Generates representative observed versus simulated hydrographs for selected CAMELS-FR and CAMELS-GB catchments.

Catchments are selected according to different performance quantiles to illustrate both successful and challenging simulations.

---
# Data

The repository contains all files required to reproduce the analyses presented in the manuscript.

## 1. Model Simulation Results

The `Data.zip` archive contains the calibrated parameters and model performance metrics for all rainfall–runoff models evaluated in this study.

### d-HyMoLAP

- `dHyMoLAP_Simulation_Data_CAMELS_FR.csv`
- `dHyMoLAP_Simulation_Data_CAMELS_GB.csv`

These files contain

- calibrated parameters ($\mu$, $\lambda$, $Q_s$, $q_s$)
- calibration and validation performance metrics
- simulated discharge
- summary statistics

---

### Original HyMoLAP

- `HyMoLAP_Simulation_Data_CAMELS_FR.csv`
- `HyMoLAP_Simulation_Data_CAMELS_GB.csv`

These files provide the baseline results used for comparison with d-HyMoLAP.

---

### HBV

- `HBV_Simulation_Data_CAMELS_FR.csv`
- `HBV_Simulation_Data_CAMELS_GB.csv`

These files contain the calibrated HBV benchmark results used throughout the comparative analyses.

---

## 2. CAMELS-FR Catchment Attributes

The repository contains all CAMELS-FR physiographic, climatic, and hydrological descriptors used throughout the interpretability analyses.

Included files are

- `CAMELS_FR_climatic_statistics.csv`
- `CAMELS_FR_hydrological_signatures.csv`
- `CAMELS_FR_hydroclimatic_statistics_joint_availability_yearly.csv`
- `CAMELS_FR_topography_general_attributes.csv`
- `CAMELS_FR_geology_attributes.csv`
- `CAMELS_FR_hydrogeology_attributes.csv`
- `CAMELS_FR_soil_general_attributes.csv`
- `CAMELS_FR_land_cover_attributes.csv`
- `CAMELS_FR_station_general_attributes.csv`
- `CAMELS_FR_site_general_attributes.csv`
- `CAMELS_FR_catchment_nestedness_information.csv`
- `CAMELS_FR_human_influences_dams.csv`

These datasets provide more than **200 catchment descriptors**, including

- climate
- hydrological signatures
- water balance
- topography
- geology
- hydrogeology
- soils
- land cover
- human influences

used for

- parameter attribution
- SHAP analyses
- performance interpretation

---

## 3. CAMELS-GB Dataset

Due to file size limitations, the CAMELS-GB forcing and attribute data are hosted separately.

📂 **Download CAMELS-GB dataset**

https://drive.google.com/drive/folders/1B1WY5IIUp6aAWx_UeQOMXc9eEGBNzfFC?usp=sharing

The folder contains

- meteorological forcing
- discharge observations
- catchment attributes

required to reproduce the CAMELS-GB experiments.

---

# Requirements

The code was developed using

- Python ≥ 3.8

Required Python packages are listed in

```
requirements.txt
```

---

# Installation

Clone the repository

```bash
git clone https://github.com/IngGOHOUEDE/d-HyMoLAP.git

cd d-HyMoLAP
```

Extract the data

```bash
unzip Data.zip
```

Install the required packages

```bash
pip install -r requirements.txt
```

or using a virtual environment

```bash
python -m venv venv

# Linux / macOS
source venv/bin/activate

# Windows
venv\Scripts\activate

pip install -r requirements.txt
```

---

# Running the Notebooks

Launch Jupyter Notebook

```bash
jupyter notebook
```

or Jupyter Lab

```bash
jupyter lab
```

Each notebook can be executed independently.

For reproducing the complete study, the recommended execution order is

1. dHyMoLAP model calibration
2. HyMoLAP model calibration
3. HBV model calibration
4. Descriptive statistics
5. Performance diagnostics
6. Morris sensitivity analysis
7. Parameter attribution analysis
8. SHAP analyses
9. GLUE uncertainty analysis
10. Ablation analysis
11. Hydrograph visualization

---

# Google Colab

All notebooks are fully compatible with **Google Colab**.

After cloning or uploading the repository,

1. upload `Data.zip`,
2. extract the archive,
3. install the dependencies from `requirements.txt`,
4. execute the notebooks normally.

---

# Citation

If you use this repository in your research, please cite

> **(Citation will be added after publication.)**

---

# References

## CAMELS-FR

Delaigue, O., Guimarães, G. M., Brigode, P., Génot, B., Perrin, C., Soubeyroux, J.-M., Janet, B., Addor, N., & Andréassian, V. (2024).

**CAMELS-FR: A large-sample hydroclimatic dataset for France to explore hydrological diversity and support model benchmarking.**

*Earth System Science Data*, **16**, 197–224.

https://doi.org/10.5194/essd-16-197-2024

---

## CAMELS-GB

Coxon, G., Addor, N., Bloomfield, J. P., Freer, J., Fry, M., Hannaford, J., et al. (2020).

**CAMELS-GB: Hydrometeorological time series and landscape attributes for 671 catchments in Great Britain.**

*Earth System Science Data*, **12**, 2459–2483.

https://doi.org/10.5194/essd-12-2459-2020

---

## Original HyMoLAP

Alamou, E. (2011).

**Application du principe de moindre action à la modélisation pluie-débit.**

Ph.D. Thesis,

Université d'Abomey-Calavi,

Benin.

---

# Contact

For questions, suggestions, or collaborations, please contact

**Lionel Cédric Gohouede**

Email:
gohouedecedric@gmail.com

GitHub:
https://github.com/IngGOHOUEDE

---

# Acknowledgments

The authors gratefully acknowledge

- the **CAMELS-FR** team for providing open-access hydroclimatic data;
- the **CAMELS-GB** team for making the Great Britain dataset publicly available;
- **Prof. Eric Alamou** and **Prof. Abel Afouda** for the original development of the HyMoLAP framework;
- the large-sample hydrology community for promoting open science and reproducible hydrological modelling.

---

# License

This project is distributed under the **MIT License**.

```
MIT License

Copyright (c) 2025 Lionel Cédric Gohouede

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```
