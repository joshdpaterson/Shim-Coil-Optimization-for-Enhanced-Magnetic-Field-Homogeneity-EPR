# Shim Coil Optimization for Enhanced Magnetic Field Homogeneity (EPR)

This repository contains the code from my BSc Physics project on designing and optimizing shim coils to improve magnetic field homogeneity in a high-field **Electron Paramagnetic Resonance (EPR)** spectrometer.  

The project involved:
- Fitting experimental magnetic field data with polynomials  
- Modeling coil-generated magnetic fields using Biot–Savart–based formulas  
- Optimizing coil geometries and currents with **SciPy’s BFGS algorithm**  
- Visualizing 3D coil configurations to check manufacturability  

**Relevance:** This project demonstrates quantitative modeling, optimization under constraints, and simulation of complex systems — skills that are directly applicable to quantitative finance and other data-driven fields.

---

## Repository Structure

```
notebooks/
  3D_Coil_Plotting.ipynb    # Generate interactive 3D coil geometry visualizations
  BField_Fitting.ipynb      # Fit polynomial models to measured external field data
  Coil_Optimization.ipynb   # Optimize coil parameters (BFGS) to minimize inhomogeneity
  Sum_BFields.ipynb         # Compose coil fields + external field and evaluate homogeneity

assets/                     # Example figures exported from notebooks (optional)
README.md
requirements.txt
.gitignore
LICENSE
```

---

## Quickstart

Clone the repository and set up a virtual environment:

```bash
git clone https://github.com/<your-username>/shimcoil-epr-optimization.git
cd shimcoil-epr-optimization
python -m venv .venv
source .venv/bin/activate        # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```

Open the notebooks in `notebooks/` and run them in sequence.

---

## Project Overview

### External Field Modeling (`BField_Fitting.ipynb`)
- Fits a polynomial to experimental superconducting magnet data.  
- Compares multiple fitting ranges and selects the most accurate near the sample region.  

### Coil Field Modeling (`Sum_BFields.ipynb`)
- Computes magnetic fields of multiple coils (radius, turns, layers, z-position, current).  
- Combines coil fields with the external field to evaluate homogeneity.  
- Reports metrics: mean error, peak positive/negative deviations, flatness across a defined sample range.  

### Optimization (`Coil_Optimization.ipynb`)
- Uses **`scipy.optimize.minimize` (BFGS)** to tune coil parameters.  
- Supports overlapping coils with different radii to improve results.  
- Applies bounds to reflect practical limits (wire size, current supply, holder geometry).  

### 3D Coil Visualization (`3D_Coil_Plotting.ipynb`)
- Produces 3D plots of coil geometries for manufacturability checks.  
- Useful for identifying overlaps or impractical designs.  

---

## Technical Stack

- Python (`numpy`, `scipy`, `matplotlib`, `ipywidgets`)  
- Jupyter Notebooks for reproducible workflows  
- Numerical optimization (BFGS)  
- Data visualization and result interpretation  

---

## Key Concepts

- Adaptation of the Biot–Savart law for efficient on-axis coil field calculations  
- Optimization under physical and experimental constraints  
- Local vs. global minima in multi-parameter systems  
- Homogeneity metrics tailored to sample volume and experiment design  

---

## Reproducibility Notes

- Sample window often set to `z ∈ [-60 mm, -5 mm]`  
- Coil length estimated as number of turns × wire diameter  
- Orthocyclic winding assumed when modeling multiple layers  
- Coil currents constrained by laboratory power supply limits  

---

## License

MIT License — see [LICENSE](./LICENSE).

---

## Contact

If you have questions about the modeling, optimization methods, or broader applications, please open an issue or reach out.
