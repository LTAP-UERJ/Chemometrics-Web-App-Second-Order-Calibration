# Chemometrics Web App — Second Order Calibration

![Status](https://img.shields.io/badge/Status-Active-green)
![Version](https://img.shields.io/badge/Release-V2-orange)
![License](https://img.shields.io/badge/License-Proprietary%20%2F%20INPI%20Registered-red.svg)
![R](https://img.shields.io/badge/Language-R-blue.svg)

Developed by the **Process Analytical Technology Laboratory (LTAP-UERJ)**, this application is a comprehensive tool for multi-way tensor decomposition, second-order calibration, and analyte quantification exploiting the **Second-Order Advantage** in complex chemometric datasets (e.g., EEM fluorescence matrices, LC-DAD data).

---

## 🔗 Quick Links

* **Online Version:** [Access the Web App](https://ltap.shinyapps.io/second_order_calibration/)
* **Software Registration (INPI):** [LTAP-UERJ CWA — Registros de Software](https://sites.google.com/view/ltap-uerj/cwa)
* **Support/Feedback:** [ltapuerj@gmail.com](mailto:ltapuerj@gmail.com)

---

## 🆕 Version History (Change Log)

### **V2 — Current Release**
* **Memory & Resource Management:** Optimized reactive memory footprint (`suspendWhenHidden`, explicit garbage collection `gc()`) for seamless deployment on free-tier ShinyApps cloud containers.
* **Advanced EEM Preprocessing Pipeline:** Integrated multi-type scattering removal algorithms (1st/2nd Order Raman and Rayleigh scattering with custom bandwidths), data range cropping, and automated missing value interpolation.
* **Interactive Multi-Mode Visualizations:** Dynamic 2D contour and 3D surface landscapes using `plotly`, with modal pop-up expanders and mode profile breakdown (A-mode scores, B-mode/C-mode spectral profiles).
* **Multi-Language Architecture:** Full internationalization supporting English, Portuguese, Spanish, French, Italian, Chinese, and Russian.
* **CWA Workspace Serialization:** Direct export/import of state and tensor arrays via `.RData` format for cross-module integration across the CWA platform.

### **V1 — Initial Release**
* Core implementation of PARAFAC (Parallel Factor Analysis) with non-negativity and unimodality constraints.
* Core MCR-ALS (Multivariate Curve Resolution — Alternating Least Squares) engine with initial guess selection (SIMPLISMA / Pure Variables / EFA).
* Basic EEM file import (.csv, .xlsx, .txt) for calibration and test sets.
* Pseudo-univariate calibration models and regression diagnostics (RMSEP, REP%, R²).

---

## 🚀 Key Features

### 📥 Multi-Way Data Import & Management
* Multi-file upload for Calibration, Test, Calibration Blank, and Test Blank datasets (`.xlsx`, `.xls`, `.csv`, `.txt`).
* Flexible axis assignment (B-mode and C-mode wavelength alignment).
* Automated Blank Subtraction (averaging multiple blank matrices and subtracting from sample matrices).
* Full 2D Contour and 3D Surface visualization with interactive rotation, zoom, and expander modals.

### 🧹 Preprocessing & Scattering Removal
| Step | Description |
| :--- | :--- |
| **Blank Correction** | Automated subtraction of single or averaged blank matrices from sample EEMs. |
| **Wavelength Trimming** | Slicing specific Excitation (B-mode) and Emission (C-mode) wavelength ranges. |
| **Scattering Removal** | Elimination of 1st and 2nd Order Raman and Rayleigh scattering lines with adjustable widths. |
| **Interpolation** | Automated interpolation over missing or zeroed scattering regions to maintain matrix structure. |
| **Baseline Correction** | Asymmetric Least Squares (ALS) and Peak Alignment (PTW) for baseline drift compensation. |
| **Compare & Accept** | Side-by-side diagnostic comparison of raw vs. preprocessed EEM landscapes. |

### 🧩 PARAFAC (Parallel Factor Analysis)
| Feature | Description |
| :--- | :--- |
| **Trilinear Decomposition** | Decomposes multi-way arrays into score vectors (A-mode) and spectral signatures (B-mode & C-mode). |
| **Constraint Library** | Non-negativity, Smoothness, Orthogonality, Unimodality, and Monotonicity applied per mode. |
| **Loss & Scaling Norms** | Fmax, Frobenius norm, 1-norm, Infinity norm, Spectral 2-norm, and Scalar rescaling. |
| **Model Diagnostics** | Core Consistency Diagnostic (**CORCONDIA**), residual analysis, and factor loading plots. |
| **Pseudo-Univariate Calibration** | Linear regression between resolved A-mode scores and reference analyte concentrations. |

### 🔀 MCR-ALS (Multivariate Curve Resolution — Alternating Least Squares)
| Feature | Description |
| :--- | :--- |
| **Initial Guess Selection** | Automated determination of initial spectral profiles using SIMPLISMA, EFA, or SVD pure variables. |
| **ALS Optimization** | Iterative resolution of concentration profiles ($C$) and spectral profiles ($S^T$). |
| **Constrained Resolution** | Non-negativity (concentration/spectra), Unimodality, Closure, and Equality constraints. |
| **Second-Order Quantitation** | Accurate quantification of target analytes even in the presence of uncalibrated interferents. |

### 📊 Diagnostic & Results
* **Performance Metrics:** Root Mean Square Error of Prediction (**RMSEP**), Relative Error of Prediction (**REP%**), Coefficient of Determination ($R^2$), and Bias.
* **Component Profiles:** Interactive Plotly graphics displaying resolved spectral profiles against experimental data.
* **Downloadable Results:** Export resolved scores, loadings, predicted concentrations, and summary reports.

---

## 💾 Installation & Usage

### **How to Run (R/RStudio)**
After downloading or cloning the module, open `app.R` in the RStudio environment and click the **"Run App"** button (or execute `shiny::runApp()`).

### **R Dependencies**
This application requires R v4.0.0+ and the following R packages:
```r
shiny
shinydashboard
plotly
DT
ggplot2
reshape2
pracma
abind
ptw
