# Shim Coil Optimization for Enhanced Magnetic Field Homogeneity (EPR)

This repository contains the code from my BSc Physics project on designing and optimizing shim coils to improve magnetic field homogeneity in a high-field **Electron Paramagnetic Resonance (EPR)** spectrometer.  Completed in 2020 using the HiPER EPR Spectrometer at the University of St Andrews.

The project involved:
- Fitting experimental magnetic field data with polynomials  
- Modeling coil-generated magnetic fields using Biot–Savart–based formulas  
- Optimizing coil geometries and currents with **SciPy’s BFGS algorithm**  
- Visualizing 3D coil configurations to check manufacturability  

**Relevance:** This project demonstrates quantitative modeling, optimization under constraints, and simulation of complex systems.

---

## Repository Structure

```
notebooks/
  3D_Coil_Plotting.ipynb    # Generate interactive 3D coil geometry visualizations
  BField_Fitting.ipynb      # Fit polynomial models to measured external field data
  Coil_Optimization.ipynb   # Optimize coil parameters (BFGS) to minimize inhomogeneity
  Sum_BFields.ipynb         # Compose coil fields + external field and evaluate homogeneity

assets/                     # Example figures exported from notebooks
README.md
requirements.txt
LICENSE
```

---

## Quickstart

Clone the repository and set up a virtual environment:

```bash
git clone https://github.com/joshdpaterson/Shim-Coil-Optimization-for-Enhanced-Magnetic-Field-Homogeneity-EPR
cd Shim-Coil-Optimization-for-Enhanced-Magnetic-Field-Homogeneity-EPR
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

## Results

Using the optimization framework developed in this project, coil designs were produced that significantly improved magnetic field homogeneity compared to earlier approaches.

- The optimized 5-coil configuration achieved an **average field error of only 0.029 G** across a sample region of *[-60 mm, –5 mm]*, compared with errors greater than 0.4 G in previous designs.  
- This corresponds to a relative homogeneity of approximately **1 part in 10⁶** within the sample volume, given the ~3 T external field.  
- The design also allowed a **larger usable sample volume**, roughly doubling the effective region compared to previous holders.  
- These improvements were confirmed in simulation and partially validated experimentally, showing narrower EPR linewidths when shimming was applied.  

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
