# FORWARD: A Learning Framework for Logical Network Perturbations to Prioritize Targets for Drug Development

## Overview
FORWARD (**Framework for Outcome-based Research and Drug Development**) is a machine-learning-driven framework designed to prioritize drug targets by leveraging logical network perturbations. This approach integrates Boolean Implication Networks with clinical trial data to identify gene signatures associated with therapeutic remission. FORWARD evaluates whether targeting specific genes can induce remission-associated molecular signatures, thereby improving drug development decision-making.

## Key Features
- **Boolean Implication Networks**: Establish logical relationships between genes.
- **Therapeutic Index (TI) Calculation**: Quantifies the likelihood that targeting a gene will induce remission-associated genes.
- **Connectivity Index (CI) Calculation**: Evaluates how strongly a target gene is connected to remission-associated genes.
- **Likelihood of Approval Index (LoAI)**: Integrates TI and CI scores to predict a drug target's potential clinical success.
- **Real-World Data Integration**: Uses transcriptomic data from randomized clinical trials for training and validation.
- **Predictive Target Ranking**: Identifies optimal drug targets for phase 3 success based on transcriptomic response markers.

## Installation
### Prerequisites
Ensure that you have the following dependencies installed before using FORWARD:
- Python (>=3.8)
- R (>=4.0)
- Required Python packages:
  ```bash
  pip install numpy pandas scipy networkx matplotlib seaborn scikit-learn opencv-python pillow json5
  ```
- Additional Python libraries:
  ```bash
  pip install pprint os-sys pickle5
  ```
- Required R packages:
  ```r
  install.packages(c("ggplot2", "dplyr", "tidyverse"))
  ```

### Clone the Repository
```bash
git clone https://github.com/sasinha7290/FORWARD.git
cd FORWARD
```

## Usage
### Computing FORWARD Score
The main pipeline for computing **FORWARD scores** of target genes is `PreCSN_IBD_pipeline.ipynb`. This notebook integrates transcriptomic datasets, applies **Boolean implication analysis**, and evaluates therapeutic potential using **network connectivity metrics**.

#### **1. Prepare Input Data**
   - Ensure gene expression and metadata files are formatted correctly.
   - Place input files in the `data/` directory.
   - The **34-gene remission signature** is defined in `34.txt`.
   - The list of drug **target genes** for analysis is in `target_gene.txt`.

#### **2. Run the FORWARD Pipeline**
   Open and execute `PreCSN_IBD_pipeline.ipynb` using Jupyter Notebook:
   ```bash
   jupyter notebook PreCSN_IBD_pipeline.ipynb
   ```

#### **3. Key Computational Steps**
   - **Boolean Representation of Gene Expression**: Converts gene expression data into binary values (high/low) using the `StepMiner` algorithm.
   - **Boolean Implication Statistics**: Identifies regulatory relationships between drug target genes and the **34-gene remission signature**.
   - **Therapeutic Index (TI) Computation**: Measures the likelihood that targeting a gene will induce the remission-associated signature.
   - **Connectivity Index (CI) Calculation**: Evaluates the strength of a target gene’s connection to the remission signature.
   - **Likelihood of Approval Index (LoAI)**: Aggregates TI and CI to predict a drug's likelihood of success.
   - **Visualization**: Generates violin plots, ROC curves, and **volcano plots** for target evaluation.

#### **4. Example Command to Compute FORWARD Scores**
   Run the following script within the notebook to compute scores:
   ```python
   from bone import MacAnalysis
   ana = MacAnalysis()
   ana.getGSE14580()
   processData(ana, ['target_gene.txt'], 1)
   ```

   - **Example Target Analysis**: `target_gene.txt` contains `PRKAB1`, which is evaluated using the pipeline.
   - **Result Interpretation**: The computed FORWARD score for `PRKAB1` is found in `result_agonist.txt`.

#### **5. Output Files**
   - **Results Directory**: Computed FORWARD scores stored in `results/`
   - **Figures Directory**: ROC-AUC curves, violin plots, and volcano plots for target evaluation.

## Repository Components
- **`PreCSN_IBD_pipeline.ipynb`**: Main notebook for computing FORWARD scores.
- **`StepMiner.py`**: Implements StepMiner algorithm for binary expression conversion.
- **`HegemonUtil.py`**: Utility functions for transcriptomics data handling.
- **`bone.py`**: Core computational module for Boolean implication network processing.
- **`explore.conf`**: Configuration file specifying datasets used in analysis.
- **`34.txt`**: Defines the **34-gene remission signature**.
- **`target_gene.txt`**: List of drug **target genes** for evaluation.
- **`result_agonist.txt`**: Stores computed FORWARD scores for agonist targets.

## Example
A sample dataset is provided in the `data/` folder. You can run the tool using:
```bash
python forward.py --input data/sample_data.csv --output results/sample_output.csv
```

## Contributing
Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature-branch`).
3. Commit changes (`git commit -m 'Add new feature'`).
4. Push to your branch (`git push origin feature-branch`).
5. Open a pull request.

## Contact
For any questions or collaboration inquiries, please contact **Saptarshi Sinha** at [sasinha@health.ucsd.edu].

---
### **Reference**
This tool was developed as part of the study:
> **FORWARD: A Learning Framework for Logical Network Perturbations to Prioritize Targets for Drug Development**  
> Authors: Saptarshi Sinha, Ella McLaren, Madhubanti Mullick, Siddharth Singh, Brigid S. Boland, and Pradipta Ghosh  
> University of California San Diego, Institute for Network Medicine.

