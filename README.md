# d-HyMoLAP: dimensionally consistent reformulation of HyMoLAP rainfall-runoff model.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

## Overview
This repository contains the code and data for the d-HyMoLAP (dimensionally consistent reformulation of HyMoLAP rainfall-runoff model) study, a parsimonious rainfall-runoff model evaluated across 1,172 catchments from the CAMELS-FR (549) and CAMELS-GB (623) large-sample datasets. The model achieves competitive performance using only four parameters $(μ, λ, Q_s, q_s)$ and two climatic inputs (precipitation and potential evapotranspiration).

## Repository Structure
```
├── Data.zip                                                # CAMELS-FR catchment attributes and simulation results
├── dHyMoLAP_Calibration_Period_Analysis.ipynb
├── dHyMoLAP_Model_CAMELS_FR.ipynb                          # d-HyMoLAP model implementation for CAMELS-FR
├── dHyMoLAP_Model_CAMELS_GB.ipynb                          # d-HyMoLAP model implementation for CAMELS-GB
├── dHyMoLAP_Parameter_Sensitivity_Analysis.ipynb
├── dHyMoLAP_Parameters_Analysis_Interpretability.ipynb
├── dHyMoLAP_Performance_Sensitivity_Analysis.ipynb
├── d_HyMoLAP_Descriptive_Stats_Params_Performance.ipynb
├── d_HyMoLAP_Performance_Based_Feature_Selection.ipynb
├── d_HyMoLAP_Simulation_Plots_FR_GB_Catchments.ipynb
├── HyMoLAP_Model_CAMELS_FR.ipynb                           # Original HyMoLAP model implementation for CAMELS-FR
├── HyMoLAP_Model_CAMELS_GB.ipynb                           # Original HyMoLAP model implementation for CAMELS-GB
├── requirements.txt                                        # Python package dependencies
└── README.md                                               # This file
```

## Notebooks

### 1. `d_HyMoLAP_Descriptive_Stats_Params_Performance.ipynb`
**Descriptive Statistics: Parameters and Performance**
- Summary statistics for calibrated parameters $(μ, λ, Q_s, q_s)$ across CAMELS-FR and CAMELS-GB
- Performance metrics (NSE, RMSE) distributions
- Comparison between HyMoLAP and d-HyMoLAP

### 2. `dHyMoLAP_Calibration_Period_Analysis.ipynb`
**Calibration Period Sensitivity Analysis**
- Impact of calibration period length (3-15 years) on model performance
- Evaluation across 50 randomly selected CAMELS-FR catchments
- Fixed validation period (2016-2020) analysis
- Violin plots showing NSE distribution vs. calibration length

### 3. `dHyMoLAP_Model_CAMELS_FR.ipynb`
**d-HyMoLAP Model Implementation for CAMELS-FR**
- Model calibration across 549 CAMELS-FR catchments
- Parameter optimization using Nelder-Mead algorithm
- Training/validation split and performance evaluation

### 4. `dHyMoLAP_Model_CAMELS_GB.ipynb`
**d-HyMoLAP Model Implementation for CAMELS-GB**
- Model calibration across 623 CAMELS-GB catchments
- Parameter optimization and performance metrics
- Comparison with CAMELS-FR results

### 5. `dHyMoLAP_Parameter_Sensitivity_Analysis.ipynb`
**Morris Sensitivity Analysis**
- Global sensitivity analysis using Morris method
- Elementary effects for all four parameters $(μ, λ, Q_s, q_s)$
- Averaged results across 20 CAMELS-FR catchments
- Parameter ranking by influence on NSE

### 6. `dHyMoLAP_Parameters_Analysis_Interpretability.ipynb`
**Parameter Attribution to Hydroclimatic Controls**
- Spearman rank correlations between parameters and 200+ catchment attributes
- Top 15 correlates for each parameter $(μ, λ, Q_s, q_s)$
- Parameter correlation analysis
- Correlation heatmaps by parameter

### 7. `dHyMoLAP_Performance_Sensitivity_Analysis.ipynb`
**Performance Sensitivity to Hydroclimatic Factors**
- NSE performance analysis across hydroclimatic gradients
- Factors: mean annual precipitation, catchment wetness (Q/P), solid precipitation fraction, hydrological zones, catchment area
- Statistical tests (Spearman correlation, ANOVA)
- Performance stratification by factor categories

### 8. `d_HyMoLAP_Performance_Based_Feature_Selection.ipynb`
**SHAP-Based Feature Importance Analysis**
- Random Forest and XGBoost models trained on NSE predictions
- SHAP (SHapley Additive exPlanations) values for feature importance
- Consensus ranking of top 20 catchment characteristics

### 9. `d_HyMoLAP_Simulation_Plots_FR_GB_Catchments.ipynb`
**Hydrograph Visualization**
- 2×2 subplot hydrographs for selected CAMELS-FR and CAMELS-GB catchments
- Quantile-based catchment selection (10th/90th percentile NSE)
- Observed vs. simulated discharge time series

### 10. `HyMoLAP_Model_CAMELS_FR.ipynb`
**Original HyMoLAP Model Implementation for CAMELS-FR**
- Baseline model calibration for comparison with d-HyMoLAP
- Performance evaluation across CAMELS-FR catchments

### 11. `HyMoLAP_Model_CAMELS_GB.ipynb`
**Original HyMoLAP Model Implementation for CAMELS-GB**
- Baseline model calibration for comparison with d-HyMoLAP
- Performance evaluation across CAMELS-GB catchments
  
## Data
The `Data.zip` file contains:
#### Model Results
- `dHyMoLAP_Simulation_Data_CAMELS_FR.csv` - Calibrated parameters and performance metrics of d-HyMoLAP on CAMELS-FR
- `dHyMoLAP_Simulation_Data_CAMELS_GB.csv` - Calibrated parameters and performance metrics of d-HyMoLAP on CAMELS-GB
- `HyMoLAP_Simulation_Data_CAMELS_FR.csv`  - Calibrated parameters and performance metrics of HyMoLAP on CAMELS-FR
- `HyMoLAP_Simulation_Data_CAMELS_GB.csv`  - Calibrated parameters and performance metrics of HyMoLAP on CAMELS-GB

#### Catchment Attributes (11 files)
- `CAMELS_FR_climatic_statistics.csv` - Climate variables
- `CAMELS_FR_hydrological_signatures.csv` - Flow regime characteristics
- `CAMELS_FR_hydroclimatic_statistics_joint_availability_yearly.csv` - Water balance metrics
- `CAMELS_FR_topography_general_attributes.csv` - Elevation, slope, terrain indices
- `CAMELS_FR_geology_attributes.csv` - Lithology fractions
- `CAMELS_FR_hydrogeology_attributes.csv` - Aquifer properties
- `CAMELS_FR_soil_general_attributes.csv` - Soil texture, depth, water capacity
- `CAMELS_FR_land_cover_attributes.csv` - CORINE land cover classes
- `CAMELS_FR_station_general_attributes.csv` - Station metadata
- `CAMELS_FR_site_general_attributes.csv` - Site characteristics
- `CAMELS_FR_catchment_nestedness_information.csv` - Nested catchment relationships
- `CAMELS_FR_human_influences_dams.csv` - Dam impacts

**Total features:** 200+ catchment characteristics organized by category (climate, hydrology, topography, geology, hydrogeology, soil, land cover, etc.)

### CAMELS-GB (671 catchments)
**Due to file size, CAMELS-GB data is hosted separately:**

📂 **[Download CAMELS-GB Data](https://drive.google.com/drive/folders/1B1WY5IIUp6aAWx_UeQOMXc9eEGBNzfFC?usp=sharing)**
The Google Drive folder contains time series data 

## Requirements

- Python >= 3.8
- See `requirements.txt` for package dependencies

## Installation
```bash
# Clone repository
git clone https://github.com/IngGOHOUEDE/d-HyMoLAP.git
cd d-HyMoLAP

# Extract data
unzip Data.zip

# Install dependencies
pip install -r requirements.txt

# Or install in a virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### Google Colab

All dependencies are pre-installed in Google Colab. Simply upload the notebooks and run!

### Running Notebooks
Open any notebook in Jupyter/Google Colab:
```bash
jupyter notebook dHyMoLAP_Calibration_Period_Analysis.ipynb
```

## Citation

If you use this code in your research, please cite:
```bibtex
@article{gohouede2025dimensionally,
  title={A dimensionally consistent reformulation of the {HyMoLAP} rainfall--runoff model: interpretability and robustness across {CAMELS} datasets},
  author={Gohouede, Lionel C\'edric and Hou\'enafa, Sianou Ez\'eckiel and Biao, Eli\'ezer Iboukoun and Johnson, Olatunji and Sezen, Cenk},
  journal={[Journal Name]},
  year={2025},
  note={In preparation}
}
```
## References

### CAMELS Datasets
- **CAMELS-FR:** Delaigue, O., Guimarães, G. M., Brigode, P., Génot, B., Perrin, C., Soubeyroux, J.-M., Janet, B., Addor, N., and Andréassian, V. (2024). CAMELS-FR dataset: a large-sample hydroclimatic dataset for France to explore hydrological diversity and support model benchmarking. *Earth System Science Data*, 16(1), 197–224. https://doi.org/10.5194/essd-16-197-2024

- **CAMELS-GB:** Coxon, G., Addor, N., Bloomfield, J. P., Freer, J., Fry, M., Hannaford, J., ... and Woods, R. (2020). CAMELS-GB: hydrometeorological time series and landscape attributes for 671 catchments in Great Britain. *Earth System Science Data*, 12(4), 2459–2483. https://doi.org/10.5194/essd-12-2459-2020

### Original HyMoLAP Model
- **HyMoLAP Development:** Alamou, E. (2011). *Application du principe de moindre action à la modélisation pluie-débit*. PhD thesis, Université d'Abomey-Calavi, Benin.
  
## Citation

If you use this code or data in your research, please cite:
```bibtex
@article{gohouede2025dimensionally,
  title={A dimensionally consistent reformulation of the {HyMoLAP} rainfall--runoff model: interpretability and robustness across {CAMELS} datasets},
  author={Gohouede, Lionel C\'edric and Hou\'enafa, Sianou Ez\'eckiel and Biao, Eli\'ezer Iboukoun and Johnson, Olatunji and Sezen, Cenk},
  journal={[Journal Name]},
  year={2025},
  note={In preparation}
}
```

**Corresponding author:** Lionel Cédric Gohouede ([gohouedecedric@gmail.com](mailto:gohouedecedric@gmail.com))

---

## References

### CAMELS Datasets
- **CAMELS-FR:** Delaigue, O., Guimarães, G. M., Brigode, P., Génot, B., Perrin, C., Soubeyroux, J.-M., Janet, B., Addor, N., and Andréassian, V. (2024). CAMELS-FR dataset: a large-sample hydroclimatic dataset for France to explore hydrological diversity and support model benchmarking. *Earth System Science Data*, 16(1), 197–224. https://doi.org/10.5194/essd-16-197-2024

- **CAMELS-GB:** Coxon, G., Addor, N., Bloomfield, J. P., Freer, J., Fry, M., Hannaford, J., ... and Woods, R. (2020). CAMELS-GB: hydrometeorological time series and landscape attributes for 671 catchments in Great Britain. *Earth System Science Data*, 12(4), 2459–2483. https://doi.org/10.5194/essd-12-2459-2020

### Original HyMoLAP Model
- **HyMoLAP Development:** Alamou, E. (2011). *Application du principe de moindre action à la modélisation pluie-débit*. PhD thesis, Université d'Abomey-Calavi, Benin.
---

## Contact

For questions or collaborations, please contact:

**Lionel Cédric Gohouede**  
📧 Email: [gohouedecedric@gmail.com](mailto:gohouedecedric@gmail.com)  
🔗 GitHub: [@IngGOHOUEDE](https://github.com/IngGOHOUEDE)

---

## Acknowledgments

We gratefully acknowledge:
- The **CAMELS-FR** team (Delaigue et al., 2024) for providing open-access hydroclimatic data for French catchments
- The **CAMELS-GB** team (Coxon et al., 2020) for providing open-access data for British catchments
- **Abel Afouda** and **Eric Alamou** for the original development of the HyMoLAP model framework
- The large-sample hydrology community for advancing open science in catchment modeling

---

**Last Updated:** February 2025

## License

This project is licensed under the MIT License.

<details>
<summary>Click to view MIT License</summary>
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
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

</details>

---
