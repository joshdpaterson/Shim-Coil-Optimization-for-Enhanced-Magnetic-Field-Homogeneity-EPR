# Energy Calibration and Resolution for Scintillation and Semiconductor Detectors

This repository contains the code and analysis from my MSc Physics project at the **University of Glasgow**, focused on evaluating detector systems for **quantitative measurement of Naturally Occurring Radioactive Materials (NORMs)**.  

The project compared a range of scintillator and semiconductor detectors — **NaI, LYSO, BGO, CsI, plastic scintillators, and HPGe** — by performing **energy calibration, Gaussian peak fitting, and resolution analysis**. The aim was to determine which detectors are most suitable for field-based NORM monitoring and laboratory confirmation.

---

## Project Overview

The main goals of this project were:

- Perform **energy calibration** of multiple detectors using standard gamma-ray sources  
- Extract **Gaussian peak fits** from multi-channel analyser (MCA) spectra  
- Quantify **energy resolution as a function of gamma-ray energy**  
- Compare scintillator detectors with **high-resolution HPGe** for isotope identification  
- Assess practical suitability of detectors for **field deployment** versus **laboratory confirmation**  

**Key Findings:**  
- Resolution–energy relationships followed the expected ∝ 1/√E dependence  
- **NaI** performed best for routine, portable gamma-ray spectroscopy of NORMs  
- **LYSO** and **BGO** showed improved performance at higher energies  
- **CsI** and **plastic scintillators** were limited by low light yield  
- **HPGe** offered superior resolution for isotope identification but required cryogenic cooling  

---

## Repository Structure

```
notebooks/
  Calibration_and_Fitting.ipynb    # Gaussian peak fitting & calibration workflow
  Resolution_Analysis.ipynb        # Energy resolution vs. energy plots for each detector
  Detector_Comparison.ipynb        # Cross-comparison of scintillator and semiconductor performance
  NORM_Sample_Analysis.ipynb       # Application to real NORM samples

assets/                            # Figures & spectra used in the README and notebooks
data/                              # Data files that can be ran in the code from a NaI and HPGe detector
README.md
requirements.txt
LICENSE
```

---

## Quickstart

Clone the repository and set up a virtual environment:

```bash
git clone https://github.com/joshdpaterson/Energy-Calibration-Resolution-for-Scintillation-and-Semiconductor-Detectors
cd Energy-Calibration-Resolution-for-Scintillation-and-Semiconductor-Detectors
python -m venv .venv
source .venv/bin/activate        # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```

Open and run the notebooks in the `notebooks/` folder.

---

## Example Workflows

### Calibration and Gaussian Fitting (`Calibration_and_Fitting.ipynb`)
- Extracts photopeak centroids and FWHM from standard sources  
- Fits calibration curves (channel number → energy)  
- Demonstrates calibration for NaI, LYSO, BGO, CsI, plastic, and HPGe detectors  

### Resolution Analysis (`Resolution_Analysis.ipynb`)
- Plots detector resolution (% FWHM) as a function of energy  
- Confirms theoretical **1/√E scaling** due to counting statistics  

### Detector Comparison (`Detector_Comparison.ipynb`)
- Benchmarks detector types side by side  
- Identifies trade-offs between resolution, efficiency, cost, and portability  

### NORM Sample Measurements (`NORM_Sample_Analysis.ipynb`)
- Applies calibrated detectors to real environmental samples (e.g., sand, pitchblende)  
- Compares spectra between scintillators and HPGe for isotope identification  

---

## Technical Stack

- **Python** (`numpy`, `scipy`, `matplotlib`, `pandas`)  
- **Jupyter Notebooks** for reproducible workflows  
- **Gaussian peak fitting** with `scipy.optimize.curve_fit`  
- **Energy calibration** and resolution analysis  
- **Data visualization** for spectra and performance comparison  

---

## Results

- NaI was identified as the **optimal field detector** for NORM monitoring  
- HPGe achieved the **highest energy resolution (~0.2–0.3% at 662 keV)**, enabling unambiguous isotope identification, but with limited portability  
- Scintillators followed the expected statistical resolution dependence, validating theoretical models  
- NORM samples (e.g., Hunterston beach sand, pitchblende) showed characteristic peaks that were only fully resolved with HPGe  

---

## License

MIT License — see [LICENSE](./LICENSE).

---

## Contact

If you have questions about detector calibration, resolution analysis, or applications to NORM monitoring, please open an issue or reach out.
