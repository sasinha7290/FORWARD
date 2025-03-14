# FORWARD: A Learning Framework for Logical Network Perturbations to Prioritize Targets for Drug Development

## Overview
FORWARD (**Framework for Outcome-based Research and Drug Development**) is a machine-learning-driven framework designed to prioritize drug targets by leveraging logical network perturbations. This approach integrates Boolean Implication Networks with clinical trial data to identify gene signatures associated with therapeutic remission. FORWARD evaluates whether targeting specific genes can induce remission-associated molecular signatures, thereby improving drug development decision-making.

## Key Features
- **Boolean Implication Networks**: Establish logical relationships between genes.
- **Therapeutic Index (TI) Calculation**: Quantifies the likelihood that targeting a gene will induce remission-associated genes.
- **Connectivity Index (CI) Calculation**: Evaluates how strongly a target gene is connected to remission-associated genes.
- **Likelihood of Approval Index (LoAI)**: Integrates TI and CI scores to predict a drug target's potential clinical success.
- **Real-World Data Integration**: Uses transcriptomic data from randomized clinical trials for training and validation.

## Installation
### Prerequisites
Ensure that you have the following dependencies installed before using FORWARD:
- Python (>=3.8)

- Required Python packages:
  ```bash
  pip install numpy pandas scipy networkx matplotlib seaborn scikit-learn opencv-python pillow json5
  ```
- Additional Python libraries:
  ```bash
  pip install pprint os-sys pickle5
  ```

### Clone the Repository
```bash
git clone https://github.com/sasinha7290/FORWARD.git
cd FORWARD
```

## Usage
### Computing FORWARD Score
The main pipeline for computing **FORWARD scores** of target genes is `PreCSN_IBD_pipeline.ipynb`. This notebook integrates transcriptomic datasets (stored at **processed_dataset** directory), applies **Boolean implication analysis**, and evaluates therapeutic potential using **network connectivity metrics**.

#### **1. Prepare Input Data**
   - Ensure gene expression and metadata files are formatted correctly (example dataset is provided in **processed_dataset** directory).
   - The **34-gene remission signature** is defined in `34.txt` (kept in ***Gene_signature** directory).
   - The list of drug **target genes** for analysis is in `target_gene.txt`.

#### **2. Run the FORWARD Pipeline**
   Open and execute `PreCSN_IBD_pipeline.ipynb` using Jupyter Notebook (Required codes: bone.py, HegemonUtil.py, StepMiner.py):
   ```bash
   jupyter notebook PreCSN_IBD_pipeline.ipynb
   ```

#### **3. Key Computational Steps**
   - **Boolean Representation of Gene Expression**: Converts gene expression data into binary values (high/low) using the `StepMiner` algorithm.
   - **Boolean Implication Statistics**: Identifies regulatory relationships between drug target genes and the **34-gene remission signature**.
   - **Therapeutic Index (TI) Computation**: Measures the likelihood that targeting a gene will induce the remission-associated signature.
   - **Connectivity Index (CI) Calculation**: Evaluates the strength of a target gene’s connection to the remission signature.
   - **Likelihood of Approval Index (LoAI)**: Aggregates TI and CI to predict a drug's likelihood of success.
   - **Example Target Analysis**: `target_gene.txt` contains `PRKAB1`, which is evaluated using the pipeline.
   - **Results Directory**: Computed FORWARD scores stored in `Results/`
   - **Result Interpretation**: The computed FORWARD score for `PRKAB1` is found in `result_agonist.txt', or, 'result_antagonist.txt` along with its TI based on the type of target.

## Repository Components
- **`PreCSN_IBD_pipeline.ipynb`**: Main notebook for computing FORWARD scores.
- **`StepMiner.py`**: Implements StepMiner algorithm for binary expression conversion.
- **`HegemonUtil.py`**: Utility functions for transcriptomics data handling.
- **`bone.py`**: Core computational module for Boolean implication network processing.
- **`explore.conf`**: Configuration file specifying datasets used in analysis.
- **`target_gene.txt`**: List of drug **target genes** for evaluation.
- **`composite_score_AUC.ipynb`**: Notebook showing composite score and area under the curve calculation using the bone framework.
- **`Multivariate and Univariate analysis.ipynb`**: Notebook showing multivariate and univariate calculation using the bone framework.


## Contact
For any collaboration inquiries, please contact **Pradipta Ghosh** at [prghosh@health.ucsd.edu].
For any technical/computational inquiries, please contact **Saptarshi Sinha** at [sasinha@health.ucsd.edu].

---
### **Reference**
This tool was developed as part of the study:
> **FORWARD: A Learning Framework for Logical Network Perturbations to Prioritize Targets for Drug Development**  
> Authors: Saptarshi Sinha, Ella McLaren, Madhubanti Mullick, Siddharth Singh, Brigid S. Boland, and Pradipta Ghosh  
> University of California San Diego, Institute for Network Medicine.

