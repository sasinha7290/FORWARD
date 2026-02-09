# FORWARD: F.O.R.W.A.R.D: An interpretable AI framework for target prioritization using end-to-end human evidence

## Overview
FORWARD (Framework for Outcome-based Research and Drug Development) is an interpretable, machine-learning–guided framework that integrates clinical-trial transcriptomics with Boolean implication logic to prioritize drug targets. FORWARD defines a remission-associated transcriptional state and computes outcome-aligned target scores based on network connectivity to this state.

**Intended use:** discovery-stage target prioritization and portfolio triage.  
**Not intended use:** calibrated probability estimates or patient-level clinical decision-making.

---

## What this repository contains
**Primary entry point**
- `PreCSN_IBD_pipeline.ipynb`: end-to-end workflow to compute TI, CI, and LoAI for targets

**Supporting notebooks**
- `composite_score_AUC.ipynb`: composite score and ROC–AUC calculations
- `Multivariate and Univariate analysis.ipynb`: univariate and multivariate regression analyses
- `LRT_AIC_BIC.ipynb`: LRT, AIC, and BIC comparisons for full vs reduced models
- `PDO_analysis.ipynb`: univariate and multivariate analysis in PDO cohorts

**Core modules**
- `StepMiner.py`: binarization (high/low) using StepMiner thresholds
- `bone.py`: Boolean implication network utilities and scoring
- `HegemonUtil.py`: transcriptomics utilities

---

## Installation

### Prerequisites
- Python >= 3.8
- Jupyter Notebook (or JupyterLab)

### Install required packages
```bash
pip install numpy pandas scipy networkx matplotlib seaborn scikit-learn opencv-python pillow json5
