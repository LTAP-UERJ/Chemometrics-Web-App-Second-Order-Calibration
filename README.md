# Chemometrics Web App — Second Order Calibration

![Status](https://img.shields.io/badge/Status-Active-green)
![Version](https://img.shields.io/badge/Release-V2-orange)
![License](https://img.shields.io/badge/License-Proprietary%20%2F%20INPI%20Registered-red.svg)
![R](https://img.shields.io/badge/R%20Version-4.3.0%2B-blue.svg)

Developed by the **Process Analytical Technology Laboratory (LTAP-UERJ)** in international collaboration with **CONICET**, this application is a comprehensive tool for multi-way tensor decomposition, second-order calibration, and analyte quantification exploiting the **Second-Order Advantage** in complex chemometric datasets (e.g., EEM fluorescence matrices, LC-DAD data).

---

## 🔗 Quick Links

* **Online Web App:** [Access on Shinyapps.io](https://ltap.shinyapps.io/second_order_calibration/)
* **Software Registration (INPI):** [LTAP-UERJ CWA — Registros de Software](https://sites.google.com/view/ltap-uerj/cwa)
* **Support & Licensing:** [licarion@gmail.com](mailto:licarion@gmail.com) | [ltapuerj@gmail.com](mailto:ltapuerj@gmail.com)

---

## 👥 Developers & Authors

This module was developed by an international multidisciplinary team of chemometrics researchers:

| Author | Affiliation | Profile / Contact |
| :--- | :--- | :--- |
| **[Paulo Sérgio de Oliveira Cezário](http://lattes.cnpq.br/5098915046998337)** | LTAP — UERJ | [Lattes Profile](http://lattes.cnpq.br/5098915046998337) |
| **[Aderval Severino Luna](http://lattes.cnpq.br/0294676847895948)** | LTAP — UERJ | [Lattes Profile](http://lattes.cnpq.br/0294676847895948) |
| **[José Licarion Pinto Segundo Neto](http://lattes.cnpq.br/5267552018296169)** | LTAP — UERJ | [Lattes Profile](http://lattes.cnpq.br/5267552018296169) |
| **[Fabricio Chiappini](https://www.researchgate.net/profile/Fabricio-Chiappini)** | CONICET | [ResearchGate Profile](https://www.researchgate.net/profile/Fabricio-Chiappini) |
| **[Benjamín Ángel Pisaroni](https://bicyt.conicet.gov.ar/fichas/p/benjamin-angel-pisaroni)** | CONICET | [CONICET Profile](https://bicyt.conicet.gov.ar/fichas/p/benjamin-angel-pisaroni) |
| **[Héctor Casimiro Goicoechea](https://www.researchgate.net/profile/Hector-Goicoechea)** | CONICET | [ResearchGate Profile](https://www.researchgate.net/profile/Hector-Goicoechea) |
| **[Alejandro Cesar Olivieri](https://www.researchgate.net/profile/Alejandro-Olivieri)** | CONICET | [ResearchGate Profile](https://www.researchgate.net/profile/Alejandro-Olivieri) |

---

## 🆕 Version History (Change Log)

### **V2 — Current Release**
* **Memory & Resource Optimization:** Optimized reactive memory management (`suspendWhenHidden`, explicit garbage collection `gc()`) for seamless deployment on free-tier ShinyApps cloud containers.
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

## 🛠️ Technical Stack & Environment

### **Build & Compilation Environment**
* **Language Runtime:** `R (>= 4.3.0)`

### **Core R Dependencies & Libraries**
| Package | Version / Scope | Purpose |
| :--- | :--- | :--- |
| **`shiny`** | `^1.8.0` | Reactive application framework and web server architecture. |
| **`shinydashboard`** | `^0.7.2` | Dashboard layout structure and sidebar navigation UI. |
| **`plotly`** | `^4.10.0` | Interactive 2D/3D surface plots, contours, and spectral graphics. |
| **`DT`** | `^0.30` | DataTables interface for dataset preview and interactive tabular outputs. |
| **`ggplot2`** | `^3.4.0` | High-quality statistical graphics rendering. |
| **`reshape2`** | `^1.4.4` | Data reshaping and matrix-to-long format conversion for multi-way arrays. |
| **`pracma`** | `^2.4.2` | Advanced numerical analysis, matrix math, and numerical integration functions. |
| **`ptw`** | `^1.9-15` | Parametric Time Warping, baseline correction, and peak alignment. |
| **`multiway`** | `^1.0-6` | PARAFAC, N-PLS, and multi-way array algorithms. |
| **`eemR`** | `^1.0.1` | EEM data reading, fluorescence excitation-emission matrix tools. |
| **`staRdom`** | `^0.2.8` | PARAFAC analysis and EEM fluorescence data processing. |
| **`ggResidpanel`** | `^0.3.0` | High-level regression model residual diagnostic panels. |
| **`GGally`** | `^2.1.2` | Extension of ggplot2 for multi-variable scatter matrices. |
| **`ellipse`** | `^0.4.5` | Ellipse drawing for bivariate confidence intervals and PCA score plots. |
| **`parsnip`** | `^1.1.0` | Tidy interface for unified model fitting and prediction. |

---

## 💻 Access & Execution

This application is distributed under closed-source terms (the underlying `app.R` source code is not publicly distributed). Access is available through two deployment targets:

1. **🌐 Online Web Version (Shinyapps.io):**
   * Access directly via web browser without installing R or any dependencies:
   * 🔗 **[https://ltap.shinyapps.io/second_order_calibration/](https://ltap.shinyapps.io/second_order_calibration/)**

2. **🖥️ Desktop Executable Version:**
   * Standalone Windows executable bundle (`.exe`) with an embedded runtime environment. No prior R installation required on the target machine.
   * Contact the authors or laboratory for desktop installer requests.

---

## ⚠️ Methodological Guidelines

> [!IMPORTANT]
> **Critical recommendations for second-order calibration:**
> - Perform **Blank Correction** and **Scattering Removal** (Raman & Rayleigh) prior to PARAFAC or MCR-ALS modeling to avoid fitting scatter artifacts as mathematical components.
> - Evaluate the number of factors using **CORCONDIA** (Core Consistency Diagnostic) in PARAFAC: values above 80–90% indicate a valid trilinear model.
> - Exploit the **Second-Order Advantage**: target analytes can be accurately quantified even in complex samples containing unmodeled, unknown interferents.

---

## 📜 License & Intellectual Property Protection

> [!CAUTION]
> **All Rights Reserved — Intellectual Property Protection (INPI)**
> 
> This software, its interface designs, compiled binaries, and underlying algorithmic implementations are protected under Intellectual Property laws (Brazilian Software Law No. 9.609/98 and Industrial Property Law No. 9.279/96) and registered at the **National Institute of Industrial Property (INPI)**. 

### **Terms of Use & Protection Clause:**
1. **Mandatory Attribution:** Any academic work, study, publication, software integration, or presentation utilizing or referencing this application **must explicitly credit** the authors (**Paulo Sérgio de Oliveira Cezário, Aderval Severino Luna, José Licarion Pinto Segundo Neto, Fabricio Chiappini, Benjamín Ángel Pisaroni, Héctor Casimiro Goicoechea, Alejandro Cesar Olivieri**) and the **Process Analytical Technology Laboratory (LTAP-UERJ / CONICET)**.
2. **Prohibition of Unauthorized Reproduction & Redistribution:** Copying, modifying, decompiling, reverse engineering, re-licensing, sub-licensing, mirroring, or redistributing the binary executables or deployment packages without explicit prior written consent from LTAP-UERJ is strictly prohibited.
3. **Non-Commercial Use Only:** The application may only be used for personal, educational, or non-commercial academic research purposes unless a specific commercial license has been granted by LTAP-UERJ.
4. **Disclaimer of Liability:** LTAP-UERJ, CONICET, and the developers accept no responsibility or liability for damages, misinterpretation, or loss resulting from the use of this software or its generated datasets. The software is provided "as is", without warranties of any kind.

For licensing inquiries or commercial use permissions, please contact [licarion@gmail.com](mailto:licarion@gmail.com) or [ltapuerj@gmail.com](mailto:ltapuerj@gmail.com).

---

## 📧 Contact & Institutional Support

**Process Analytical Technology Laboratory (LTAP/UERJ)** & **CONICET**

We acknowledge financial and institutional support from **UERJ** (Programa Pró-Ciência and INOVUERJ), **FAPERJ** (JCNE and CNE research scholarships), **CONICET**, **CNPq** (Universal Grant 404077/2023-4), and **CAPES**.

---

<p align="center">
  <a href="https://www.ltapuerj.com.br/">LTAP-UERJ</a> •
  <a href="https://www.uerj.br/">UERJ</a> •
  <a href="https://www.conicet.gov.ar/">CONICET</a> •
  <a href="https://www.faperj.br/">FAPERJ</a> •
  <a href="https://www.gov.br/cnpq/pt-br">CNPq</a> •
  <a href="https://www.gov.br/capes/pt-br">CAPES</a>
</p>
