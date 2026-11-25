
# Fraud Detection – Error Slice Analysis Report

## 1. Evaluation Overview

- Total test transactions: 88,581
- Actual fraudulent transactions: 3,083
- False negatives: 1,667
- False positives: 4,583
- Fraud amount prevented: $341,403.18
- Missed fraud amount: $128,205.34

## 2. Error Analysis by Transaction Amount

| Amount Group | Transactions | Fraud Transactions | False Negatives | False Negatives % | False Positives |
| --- | --- | --- | --- | --- | --- |
| 0-50 | 29855 | 1257 | 881 | 70.08750994431185 | 77 |
| 50-100 | 24484 | 678 | 402 | 59.29203539823009 | 370 |
| 100-250 | 24999 | 683 | 310 | 45.387994143484626 | 1210 |
| 250-500 | 5666 | 271 | 62 | 22.878228782287824 | 990 |
| 500+ | 3577 | 194 | 12 | 6.185567010309279 | 1936 |

The model missed a higher proportion of fraudulent transactions
in lower transaction-amount groups. The false-negative rate
decreased as transaction amount increased in this test set.

## 3. Ten Costliest Missed Fraudulent Transactions

| Transaction_Amount | Predicted_Probability | Expected_Fraud_Loss |
| --- | --- | --- |
| 1949.69 | 0.0037 | 7.2077 |
| 1504.47 | 0.0091 | 13.677 |
| 1402.85 | 0.0076 | 10.6807 |
| 1402.85 | 0.0093 | 13.0498 |
| 1384.95 | 0.0076 | 10.5444 |
| 1224.0 | 0.0091 | 11.1273 |
| 1044.95 | 0.0076 | 7.9558 |
| 884.0 | 0.0144 | 12.7423 |
| 680.45 | 0.0144 | 9.8083 |
| 611.95 | 0.0076 | 4.6591 |

These are actual fraudulent transactions that the selected
BCE Isotonic model's $15 expected-loss policy approved.

## 4. Interpretation

The results show a trade-off between preventing fraud and
avoiding unnecessary declines.

Lower-value transactions had a higher false-negative rate.
Higher-value transactions were more likely to be declined
under the expected-loss policy.

This is an observation from the test data and does not
establish that transaction amount causes fraud or model errors.

## 5. Selected Decision Policy

The selected strategy is BCE Isotonic calibration with the
$15 expected-loss decision policy:

Decline a transaction when:

Predicted Fraud Probability x Transaction Amount > $15

## 6. Output Files

- error_slice_analysis_report.md
- error_slice_analysis_report.csv
- top_10_costliest_false_negatives.csv
