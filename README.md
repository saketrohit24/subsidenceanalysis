# InSAR-Based Subsidence Analysis & Component Decomposition

[![Python Version](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)


> **Project Overview:**  
> This project focuses on the analysis of land subsidence in California's Central Valley using InSAR (Interferometric Synthetic Aperture Radar) data. By applying advanced statistical methods—specifically Principal Component Analysis (PCA) and Independent Component Analysis (ICA)—the project separates subsidence signals into elastic and inelastic components, identifies artifacts, and ultimately provides calibrated data for groundwater models (e.g., C2VSim). Detailed scripts perform geospatial data preprocessing, multi-band GeoTIFF creation, time series visualization, and component decomposition.

---

## Table of Contents

- [Introduction](#introduction)
- [Dataset](#dataset)
- [Features](#features)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Visualizations](#Visualizations)
- [Related Publications](#related-publications)
- [Contributing](#contributing)
- [References](#References)
  

---

## Introduction

Subsidence—the gradual sinking of the ground—is a significant issue in California's Central Valley, with over 30 feet of sinking recorded between 1925 and 1977 and additional loss observed from 1988 to 2018. This project addresses the following challenges:

- **Data Inconsistencies:** Variability in InSAR spatial coverage and artifacts (pixel offsets) leading to sudden jumps in subsidence values.
- **Component Separation:** Using ICA to isolate seasonal elastic deformation (often correlated with groundwater pumping) and inelastic, long-term trends.
- **Model Calibration:** Leveraging PCA-derived inelastic components as targets for calibrating groundwater models such as C2VSim.
- **Visualization & Analysis:** Providing time series, spatial plots, and CSV outputs to compare simulation data against InSAR measurements.

---
## Dataset
https://gis.water.ca.gov/arcgisimg/rest/services/SAR

---
## Features

- **Data Preprocessing:**  
  - Extraction and clipping of geospatial raster data using a polygon from a KMZ file.
  - Filtering of invalid values and handling of spatial inconsistencies.
  
- **Multi-Band GeoTIFF Generation:**  
  - Stacking and sorting of raster data by date.
  - Metadata extraction and integration for each time step.
  
- **Time Series Analysis:**  
  - Visualization of minimum subsidence trends over time.
  - Extraction and export of subsidence data for further analysis.
  
- **Component Decomposition:**  
  - **ICA:** Separation of independent components to isolate seasonal (elastic) and long-term (inelastic) deformation.
  - **PCA:** Extraction of dominant spatial and temporal patterns, with the first principal component (PC1) accounting for most variance.
  - Comparative visualization of PCA and ICA results.
  
- **Advanced Visualization:**  
  - Scatter plots for spatial patterns.
  - Dual-axis time series plots to compare simulation and InSAR data.
  - Exporting of component values to CSV for further research and model calibration.

---

## Project Structure
insar-subsidence-analysis/
├── MyNotebook.ipynb
└── README.md

---
## Installation

### Clone the Repository

Open your terminal and run:

```bash
git clone https://github.com/saketrohit24/isubsidenceanalysis.git
cd subsidence-analysis
```

### Set Up a Virtual Environment

It is recommended to create a virtual environment to manage your Python dependencies:

```bash
# Create a virtual environment using Python 3
python3 -m venv venv

# Activate the virtual environment (macOS/Linux)
source venv/bin/activate

# On Windows:
venv\Scripts\activate
```

### Install Required Dependencies

If you have a `requirements.txt` file (or if you decide to add one as your project evolves), install the dependencies:

```bash
pip install -r requirements.txt
```
---

## Visualizations
ICA Components::
![InSAR Analysis](https://github.com/saketrohit24/subsidenceanalysis/blob/main/images/1.png)

This analysis applies Independent Component Analysis (ICA) to InSAR-derived subsidence data:

IC1 captures seasonal deformation from groundwater pumping.
IC2 may represent a multi-decadal trend in subsidence.
IC3 closely matches inelastic subsidence, aligning with the Corcoran 'Subsidence Bowl.'

PCA Components:

![InSAR Analysis](https://github.com/saketrohit24/subsidenceanalysis/blob/main/images/2.png)
This analysis applies Principal Component Analysis (PCA) to InSAR-derived subsidence data:

PC1 captures 98% of total variance, primarily representing seasonal elastic deformation.

ICA & PCA on C2VSim Simulated Subsidence :
![InSAR Analysis](https://github.com/saketrohit24/subsidenceanalysis/blob/main/images/3.png)
ICA decomposition does not show clear seasonal trends
PCA results suggest that PC1 represents inelastic subsidence, capturing the primary deformation pattern over time.

---
## Related Publications
This work was presented as a poster at AGU 
- Decomposition of Inelastic and Elastic Components of Total Subsidence for Model Calibration Evaluation – [AGU Conference, 2024]
- Link: https://bit.ly/subsidenceanalysis

---
## Contributing 
Contributions are welcome! This project applies statistical techniques for subsidence decomposition, but other approaches can also be explored.

How to Contribute?
1. Fork this repository and clone it.
2. Create a new branch for your contributions.
3. Enhance the methods (e.g., alternative decomposition techniques).
4. Submit a pull request with your improvements.
- If you test a new technique, share your results, and I’d love to discuss them!
- You can also use this code for your own work—just fork it and modify as needed.

---
## References

- Hyvärinen, A., & Oja, E. (2000). Independent component analysis: algorithms and applications. *Neural Networks: The Official Journal of the International Neural Network Society, 13*(4-5), 411–430. [https://doi.org/10.1016/s0893-6080(00)00026-5](https://doi.org/10.1016/s0893-6080(00)00026-5)

- Chaussard, E., & Farr, T. G. (2019). A new method for isolating elastic from inelastic deformation in aquifer systems: Application to the San Joaquin Valley, CA. *Geophysical Research Letters, 46*, 10800–10809. [https://doi.org/10.1029/2019GL084418](https://doi.org/10.1029/2019GL084418)


