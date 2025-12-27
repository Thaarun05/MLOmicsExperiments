# MLOmicsExperiments
# 01_environment_check.ipynb

## Overview

This notebook verifies the execution environment and establishes a validated baseline for running multi-omics breast cancer modeling experiments. It ensures that all required libraries, data access mechanisms, and core modeling components are correctly installed and functional before downstream analysis.

In addition to environment validation, the notebook performs an initial end-to-end sanity check of the data pipeline and modeling stack using publicly hosted multi-omics breast cancer datasets.

---

## Objectives

- Confirm correct installation of PyTorch and core Python dependencies  
- Validate compatibility between `datasets`, `huggingface_hub`, and filesystem dependencies  
- Verify access to hosted multi-omics datasets via Hugging Face  
- Load and inspect representative molecular modalities (mRNA, methylation, CNV, miRNA)  
- Run baseline single-omics and late-fusion classification experiments  
- Log results using MLflow to confirm experiment tracking functionality  

---

## Environment Setup

The notebook installs and validates the following key dependencies:

- **PyTorch** (with torchvision and torchaudio)
- **Hugging Face datasets & hub**
- **fsspec** (version-locked for compatibility)
- **scikit-learn**
- **pandas / numpy**
- **MLflow**

A Python kernel restart is intentionally triggered after dependency reinstallation to guarantee a clean runtime state.

---

## Data Access

Datasets are pulled directly from the Hugging Face Hub using authenticated API calls. The notebook:

- Lists available files in the target dataset repository  
- Downloads representative omics files (e.g., CNV, mRNA, methylation)  
- Performs basic schema and identifier sanity checks  

This confirms both network access and dataset integrity.

---

## Modeling Checks

The notebook runs lightweight but meaningful modeling checks to validate the ML stack:

### Single-Omics Baselines
- Independent classifiers trained per modality  
- Probability outputs generated for fusion experiments  

### Late Fusion
- Uniform weighted late fusion across modalities  
- Macro-F1 and accuracy evaluation  

### Stacked Late Fusion
- Meta-classifier trained on modality probability outputs  
- Comparison against uniform fusion  

Coefficient inspection is included to confirm that learned fusion weights align with biological signal strength across modalities.

---

## Experiment Tracking

All fusion experiments are logged using **MLflow**, verifying:

- Run creation  
- Metric logging  
- Reproducibility of experimental artifacts  

This ensures the environment is ready for large-scale experimentation.

---

## Expected Outcome

Successful execution confirms that:

- The Python environment is stable and reproducible  
- External datasets are accessible  
- Multi-omics pipelines execute end-to-end without failure  
- Fusion modeling and experiment tracking function as intended  

This notebook serves as the **gateway validation step** before any full-scale modeling, benchmarking, or productization work.

---

## Notes

- This notebook is not intended for final model performance reporting  
- Results are used strictly for verification and sanity checking  
- Downstream notebooks assume this environment check has passed  
