# Causal Inference Project

This repository contains my individual causality project submission. It includes two worked causal examples (with DAGs, identification, estimation, and diagnostics), a quiz section with 15 causality MCQs, and a link to a short video presentation.

---

## Repository Structure

```
Individual_YourName_CausalityTopic/
├── Causality_Notebook.ipynb
├── Example1_Dataset/
├── Example2_Dataset/
├── QuizQuestions.md
├── Video_Link.txt
└── README.md
```

---

## Contents

### 1) `Causality_Notebook.ipynb`
An end-to-end notebook with two causal analyses:

**Example 1 (Primary Dataset)**
- Dataset description and causal question  
- Treatment, outcome, and confounders  
- DAG construction and causal reasoning  
- Identification assumptions  
- Causal effect estimation and interpretation  
- Diagnostics and discussion of threats to validity  

**Example 2 (Lalonde / NSW Job Training)**
- Observational setup (NSW treated + non-experimental controls)  
- Baseline imbalance and confounding discussion  
- DAG + backdoor identification (DoWhy)  
- Propensity score modeling and overlap diagnostics  
- IPW (stabilized) + weight diagnostics  
- Trimming for common support  
- Propensity score matching (1-NN)  
- Covariate balance checks using standardized mean differences (SMD)  
- Outcome regression (OLS) and limitations under weak overlap  
- Comparison table of estimates across methods  

---

### 2) `Example1_Dataset/`
Dataset files used for Example 1.

---

### 3) `Example2_Dataset/`
Dataset files used for Example 2.

**Note:** If Example 2 loads NSW/PSID data from URLs in the notebook, this folder is included for backup copies and/or reproducibility where applicable.

---

### 4) `QuizQuestions.md`
15 multiple-choice questions on causal inference concepts, each with:
- 4 options
- One correct answer
- Explanation for why the correct answer is correct
- Brief notes on why the other options are incorrect

---

### 5) `Video_Link.txt`
A plain text file containing the video presentation link.

---

## How to Run

### Environment
- Python 3.10+ (3.11 also works)
- Jupyter Notebook / JupyterLab

### Required Libraries
- numpy
- pandas
- matplotlib
- scikit-learn
- statsmodels
- dowhy
- graphviz (system install may be required for rendering DAGs)

### Steps
1. Open `Causality_Notebook.ipynb`
2. Run cells from top to bottom
3. Confirm:
   - DAG renders correctly
   - Overlap / propensity score plots render
   - Effect estimates and comparison table appear

---

## Notes
This project emphasizes:
- Correct identification using causal graphs (backdoor reasoning)
- Practical diagnostics for observational methods (overlap, extreme weights, balance via SMD)
- Clear interpretation of estimates and limitations (positivity, functional form assumptions, unmeasured confounding)
