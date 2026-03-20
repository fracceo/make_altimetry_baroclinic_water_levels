# make_altimetry_baroclinic_water_levels

A workflow for generating **altimetry‑derived baroclinic water levels** for use in **2D Delft3D FM** models.  
The goal is to create a **globally consistent, repeatable method** for constructing time‑varying baroclinic water levels based on satellite altimetry products.

This repository is part of the broader effort to develop a method that can later be applied **anywhere in the world**, starting with a test case in the **North Sea**.


## Objectives

- Produce **time‑varying altimetry‑derived baroclinic water levels** suitable as boundary or correction fields for DCSM and other depth‑averaged Delft3D FM models.
- Build a workflow / Jupyter Notebook that generalizes to **any region of interest** once data sources are available.
- Ensure all components use a **consistent vertical reference surface**.



## Workflow Steps (North Sea Prototype)

This repository implements the following tasks:

1. **Combine DTU25 MSS and the regional geoid (TUD)**  
   - Construct a base mean sea surface consistent with the regional geoid.

2. **Compute long‑term sea‑level trend from ESA CCI SL data (NERSC)**  
   - Extract and prepare long‑term trends to include background changes in sea‑level height.

3. **Compute SA and SSA components from EOT20 (TUD)**  
   - Derive baroclinic steric contributions (seasonal and sub‑seasonal).

4. **Merge all components into an MDT field**  
   - Combine MSS + geoid + long‑term trends + SA/SSA.  
   - Adjust to a single consistent vertical reference (Deltares + TUD).


## Repository Contents (suggested)
```
make_altimetry_baroclinic_water_levels/
├── src/
│   ├── compute_mss_geoid.py
│   ├── compute_trend_cci.py
│   ├── compute_sa_ssa.py
│   ├── merge_to_mdt.py
│   ├── correct_tide_gauges.py
│   ├── compare_mdt.py
│   └── prepare_dcsf_boundary.py
├── notebooks/
│   ├── 01_prepare_inputs.ipynb
│   ├── 02_compute_components.ipynb
│   ├── 03_merge_mdt.ipynb
│   ├── 04_validation.ipynb
│   └── 05_dcsf_run.ipynb
└── README.md
```
