# Julia Favaro's Project - CERN Summer Student 2025, Neutrino group
## TPs' analysis for the LArTPC performances

This repository contains the analysis for the CERN Summer Student 2025 project with the EP-NU group. The project focuses on the analysis of Trigger Primitives (TPs) for evaluating Liquid Argon Time Projection Chamber (LArTPC) performance. It involves comparing sensitivity thresholds, noise characteristics, detector response, and background rates between real and simulated ProtoDUNE data, with a specific focus on Argon-39 as part of the Offline Trigger Analysis.

Indico webpage of the 2025's program: [https://summerstudent.web.cern.ch/2025](https://summerstudent.web.cern.ch/2025)

### Description of the project
My study focuses on cosmic rays, which are expected to be the leading high-energy background activity in the Far Detector of the DUNE experiment. In particular, I compare cosmic ray data from the PDHD in both simulation and real data, examining how the properties of Trigger Primitives (TPs) depend on the track angle. By quantifying these variations, the goal is to provide insights that could inform the development of future online trigger strategies for more efficient data storage of the most physically interesting events.

The analysis aims to demonstrate the feasibility of using collection plane TP properties to accurately identify track angles, though estimation of out-of-plane angles may require additional information from induction planes, addressing clustering challenges associated with high-multiplicity, noisy real data.

#### For further information
- J. Favaro, K. Wawroska Trigger primitive simulation-data comparisons and cosmic data selection in ProtoDUNE Horizontal Drift detector. CERN Report, August 2025. (https://zenodo.org/records/16998968)
- K. Wawrowska. DUNE trigger simulation: TPG algorithm performance. Technical Report DUNE-TRIG-2025-08, CERN, August 2025
- C. Adams et al. Ionization Electron Signal Processing in Single Phase LArTPCs. I. Algorithm Description and Quantitative Evaluation with MicroBooNE Simulation. Journal of Instrumentation, 13(07):P07006, 2018.

### Repository structure

The repository is organized as follows:

-   `data/`: Contains the ROOT files used for the analysis.
    -   `muons_simtps_pdhd_n100.root`: A Monte Carlo simulation dataset of 100 single muon events.
    -   `pdhd_run03297*.root`: Real cosmic ray data from three different runs of the PDHD detector.
-   `src/`: Contains the Jupyter notebooks with the analysis code.
    -   `MC_data.ipynb`: Explores the simulated muon (MC) data. It analyzes detector response, correlates MC truth energy with visible TP energy, and visualizes track projections based on true particle kinematics.
    -   `RUN_test_event_run.ipynb` & `RUN_test_run.ipynb`: These notebooks offer a deep dive into specific events from the real data (run 32974). They include detailed noise analysis, threshold optimization, and track reconstruction using DBSCAN clustering and RANSAC linear fitting.
-   `pyproject.toml`: Defines the project metadata and Python dependencies.
  
### Key Analysis Components

-   **Data Loading:** Utilizes the `uproot` and `awkward-array` libraries to efficiently read and handle ragged TTree data from ROOT files within a Python environment.
-   **MC vs. Real Data Comparison:** Compares distributions of key TP properties (`TP_SADC`, `TP_peakADC`, `TP_TOT`) between simulated muons and real cosmic ray data to identify noise components and validate simulations.
-   **APA Activity Visualization:** Generates 2D event displays (channel vs. time) for each APA to visualize particle tracks and assess detector noise levels.
-   **Track Clustering and Fitting:** Implements `DBSCAN` to cluster TPs into potential tracks and `RANSAC` to fit linear models to these clusters, effectively identifying linear cosmic ray tracks in background noise.

###  Usage, modules and libraries

**Prerequisites**: 

-   Python 3.9 or higher.
-   A virtual environment manager like Conda is recommended.

**Dependencies**:

    - numpy - array and math functions
    - uproot - for manipulating ROOT TTrees
    - awkward- for working with ragged arrays
    - scipy - numerical methods 
    - matplotlib- plotting
    - pandas- for working with datasets structures
    
We used the library Uproot to read, write, and manipulate the ROOT files without installing ROOT itself.

The analysis can be run by executing the Jupyter notebooks located in the `src/` directory. The notebooks are designed to load data from the `data/` directory. Dataset kindly provided by the PD Far Detector CERN EP group.

### Authors and acknowledgment

-   **Author**: Julia Favaro

    I am a master's student at the University of Pisa (Italy), specializing in astroparticle physics and data analysis. In July and August 2025, I participated in the CERN Summer Student Program, working with the Neutrino group on the Proto-DUNE project. The dataset was kindly provided by the PD Far Detector CERN EP group.
-   **Supervisors:** Dr. Klaudia Wawroska (EP-DUNE Department, CERN). Special thanks to Dr. Alessandro Thea (EP-DUNE Department, CERN). 
  
### Project status

This project corresponds to the work completed during the summer student program, which finishes on August 29, 2025.
