# F.O.R.W.A.R.D: An interpretable AI framework for target prioritization using end-to-end human evidence

## Overview
F.O.R.W.A.R.D (Framework for Outcome-based Research and Drug Development) is an interpretable, machine-learning–guided framework that integrates clinical-trial transcriptomics with Boolean implication logic to prioritize drug targets. F.O.R.W.A.R.D defines a remission-associated transcriptional state and computes outcome-aligned target scores based on network connectivity to this state.

**Intended use:** discovery-stage target prioritization and portfolio triage.  
**Not intended use:** calibrated probability estimates or patient-level clinical decision-making.

---

## Quick start
1. Install dependencies from `requirements.txt`.
2. Open and run `PreCSN_IBD_pipeline.ipynb`.
3. Confirm outputs are written to `Results/` (TI, CI, LoAI tables).

---

## What this repository contains

### Primary entry point
- `PreCSN_IBD_pipeline.ipynb`: end-to-end workflow to compute TI, CI, and LoAI scores for targets

### Supporting notebooks
- `composite_score_AUC.ipynb`: composite score and ROC–AUC calculations
- `Multivariate and Univariate analysis.ipynb`: univariate and multivariate regression analyses
- `LRT_AIC_BIC.ipynb`: LRT, AIC, and BIC comparisons for full vs reduced models
- `PDO_analysis.ipynb`: univariate and multivariate analysis in PDO cohorts

### Core modules
- `StepMiner.py`: binarization (high/low) using StepMiner thresholds
- `bone.py`: Boolean implication statistics and scoring utilities
- `HegemonUtil.py`: transcriptomics utilities

---

## Installation

### Prerequisites
- Python 3.8 or higher
- Jupyter Notebook or JupyterLab

### Install dependencies
We recommend installing from the pinned environment file:

```bash
pip install -r requirements.txt
