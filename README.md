\# Fraud Detection System: Concept Drift \& Probability Calibration



An advanced machine learning project for detecting fraudulent financial transactions using LightGBM, concept drift analysis, focal loss, probability calibration, and explainable AI.



\## Project Overview



Fraud detection is a challenging machine learning problem because fraudulent transactions are rare, transaction patterns evolve over time, and traditional classification models may produce poorly calibrated probabilities.



This project develops a fraud detection pipeline using the \*\*IEEE-CIS Fraud Detection dataset\*\*. It focuses on handling class imbalance, identifying concept drift, improving fraud probability estimates, and evaluating models using both statistical and business-oriented metrics.



The objective is not just to classify transactions as fraudulent or legitimate, but also to produce reliable fraud probabilities and support cost-sensitive decision-making.



\## Key Objectives



\- Develop a machine learning model for fraud detection.

\- Handle highly imbalanced transaction data.

\- Analyze concept drift and changes in transaction patterns.

\- Implement and compare Binary Cross-Entropy and Focal Loss.

\- Improve probability reliability through calibration.

\- Explain model predictions using SHAP.

\- Evaluate models using cost-sensitive metrics and Net Dollar Savings.



\## Technology Stack



| Category | Technologies |

|---|---|

| Programming | Python |

| Data Processing | Pandas, NumPy |

| Machine Learning | LightGBM, Scikit-learn |

| Imbalanced Learning | Focal Loss |

| Probability Calibration | Platt Scaling, Isotonic Regression |

| Explainable AI | SHAP |

| Visualization | Matplotlib |

| Development | Jupyter Notebook |

| Version Control | Git, GitHub |



\## Project Workflow



\### 1. Data Loading and Exploratory Data Analysis



\- Loaded and merged IEEE-CIS transaction and identity datasets.

\- Analyzed missing values and feature distributions.

\- Examined fraud distribution and class imbalance.

\- Created chronological training, validation, and test splits to reduce temporal data leakage.



\### 2. Baseline Model Development



\- Developed a baseline LightGBM classifier.

\- Evaluated performance using ROC-AUC, PR-AUC, precision, recall, and F1-score.

\- Used chronological validation to evaluate performance on future transactions.



\### 3. Concept Drift Analysis



\- Implemented adversarial validation to investigate differences between historical and future data.

\- Used Population Stability Index (PSI) to analyze feature distribution changes.

\- Examined conditional fraud rates and feature interactions.

\- Investigated temporal changes in fraud patterns.



\### 4. Advanced Model Development



\- Implemented a custom Focal Loss objective.

\- Compared Binary Cross-Entropy and Focal Loss approaches.

\- Evaluated the effect of different focal loss configurations.

\- Conducted feature ablation experiments to understand the contribution of engineered features.



\### 5. Probability Calibration



Implemented two calibration techniques:



\- \*\*Platt Scaling:\*\* Uses logistic regression to improve probability calibration.

\- \*\*Isotonic Regression:\*\* Uses a non-parametric approach to map model scores to calibrated probabilities.



Evaluated calibration using reliability diagrams and calibration metrics.



\### 6. Explainable AI using SHAP



\- Analyzed feature importance.

\- Examined individual prediction contributions.

\- Compared feature explanations between BCE and Focal Loss models.

\- Identified influential features associated with fraud predictions.



\### 7. Cost-Sensitive Evaluation and Net Dollar Savings



\- Analyzed false positives and false negatives.

\- Investigated high-cost missed fraud cases.

\- Compared decision thresholds.

\- Evaluated the financial impact of fraud detection decisions.

\- Implemented Net Dollar Savings analysis to compare the business value of different model configurations.



\## Model Evaluation



\### Baseline LightGBM Results



| Metric | Validation Result |

|---|---:|

| ROC-AUC | 0.91678 |

| PR-AUC | 0.58386 |

| Precision | 0.8462 |

| Recall | 0.3491 |

| F1-Score | 0.4943 |



These results represent the baseline model's chronological validation performance.



\### Probability Calibration and Threshold Evaluation



Selected thresholds from the calibration evaluation:



| Metric | BCE | Focal Loss (α = 0.75) |

|---|---:|---:|

| Selected Threshold | 0.16 | 0.33 |

| Precision | 0.4179 | 0.5973 |

| Recall | 0.4603 | 0.3326 |

| F1-Score | 0.4381 | 0.4273 |

| False Positives | 929 | 325 |

| False Negatives | 782 | 967 |



These results illustrate the trade-off between identifying more fraudulent transactions and reducing false alarms.



\*Note: These are threshold-selection evaluation results, not a claim of final independent test performance.\*



\## Visual Results



The repository includes visualizations covering:



\- ROC-AUC and PR-AUC comparisons.

\- Calibration reliability diagrams.

\- Concept drift analysis.

\- PSI feature distribution comparisons.

\- SHAP feature importance.

\- Temporal model performance.

\- Net Dollar Savings comparisons.

\- Confusion matrices.



Explore the `results/` directory for the generated graphs and evaluation reports.



\## Repository Structure



```text

Fraud-Detection-System/

│

├── notebooks/

│   ├── 01\_Data\_Loading\_and\_EDA.ipynb

│   ├── 02\_Advanced\_Implementation.ipynb

│   ├── 03\_Model\_Calibration\_Evaluation\_Explainability.ipynb

│   └── 04\_Net\_Dollar\_Savings.ipynb

│

├── models/

│   ├── bce\_model.pkl

│   ├── focal\_alpha75\_model.pkl

│   ├── lightgbm\_baseline.pkl

│   ├── isotonic\_regression.pkl

│   └── platt\_scaling.pkl

│

├── results/

│   ├── \*.csv

│   ├── \*.png

│   └── \*.md

│

├── .gitignore

└── README.md

```



\## Dataset



This project uses the \*\*IEEE-CIS Fraud Detection dataset\*\*, originally provided for a Kaggle competition.



Dataset source:



https://www.kaggle.com/competitions/ieee-fraud-detection



The original datasets are not included in this GitHub repository. Download them from Kaggle and place the required files in your local project data directory before running the notebooks.



\## Installation and Execution



\### 1. Clone the repository



```bash

git clone https://github.com/naghulpranav001/Fraud-Detection-System.git

cd Fraud-Detection-System

```



\### 2. Create a virtual environment



```bash

python -m venv .venv

```



Activate it on Windows:



```powershell

.venv\\Scripts\\activate

```



\### 3. Install dependencies



Install the required libraries used by the notebooks:



```bash

pip install pandas numpy scikit-learn lightgbm shap matplotlib seaborn jupyter pyarrow

```



\### 4. Download the dataset



Download the IEEE-CIS dataset from Kaggle and place its CSV files in the expected local data directory.



\### 5. Run the notebooks



Start Jupyter:



```bash

jupyter notebook

```



Execute the notebooks in the following order:



1\. `01\_Data\_Loading\_and\_EDA.ipynb`

2\. `02\_Advanced\_Implementation.ipynb`

3\. `03\_Model\_Calibration\_Evaluation\_Explainability.ipynb`

4\. `04\_Net\_Dollar\_Savings.ipynb`



Some notebook paths and intermediate artifacts may need to be configured for your local environment.



\## Key Learnings



This project provided practical experience in:



\- Handling highly imbalanced classification problems.

\- Building and evaluating LightGBM models.

\- Understanding concept drift and adversarial validation.

\- Implementing custom loss functions.

\- Probability calibration and threshold optimization.

\- Applying SHAP for model interpretability.

\- Evaluating machine learning systems using business-oriented metrics.

\- Building reproducible machine learning workflows.



\## Future Improvements



\- Develop automated concept drift monitoring.

\- Implement adaptive model retraining.

\- Explore ensemble learning approaches.

\- Build a real-time fraud prediction API.

\- Develop an interactive monitoring dashboard.

\- Integrate automated model performance tracking.



\## Author



\*\*Naghul Pranav\*\*



Computer Science Engineering



GitHub: https://github.com/naghulpranav001



\---



⭐ If you find this project interesting, feel free to explore the notebooks, results, and implementation.

