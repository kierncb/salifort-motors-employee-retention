# Salifort Motors: Employee Retention Analysis

*Capstone project for the Google Advanced Data Analytics Professional Certificate*

**Skills demonstrated:** EDA & data cleaning · feature engineering · logistic regression · class-imbalanced model evaluation · stakeholder-facing recommendations

## Summary

Salifort Motors' HR team wanted to know why employees were leaving and whether at-risk employees could be flagged in advance. Using 14,999 employee records, I found that **turnover is driven by overwork, not underperformance** — and built a logistic regression model to test whether it's predictable from the data.

## Key Findings

- Employees with **7 projects left the company 100% of the time**; workload is the single strongest turnover signal.
- Employees logging **240+ hours/month** clustered at near-zero satisfaction and high turnover — but long hours barely moved evaluation scores or promotion odds.
- Employees near the **4-year tenure mark** who left showed unusually low satisfaction, suggesting a stalled-progression risk point.
- Employees with **6+ years tenure rarely left** at all.

## Model Performance — the honest version

Overall accuracy was 82%, but that number is inflated by class imbalance (83% stayed / 17% left). What matters is how well the model catches employees who actually leave:

| | Precision | Recall | F1 | Support |
|---|---|---|---|---|
| Predicted would **not** leave | 0.86 | 0.93 | 0.90 | 2,321 |
| Predicted **would leave** | **0.44** | **0.26** | **0.33** | 471 |
| **Accuracy** | | | **0.82** | 2,792 |

**Bottom line:** the model misses roughly 3 in 4 employees who actually leave. It's a solid first pass and a useful interpretable baseline, but it's not yet reliable enough to act on directly — recall on the "left" class is the metric to improve, not overall accuracy.

## Recommendations for Stakeholders

- Cap the number of projects that employees can work on.
- Consider promoting employees who have been with the company for at least four years, or conduct further investigation about why four-year tenured employees are so dissatisfied.
- Either reward employees for working longer hours, or don't require them to do so.
- If employees aren't familiar with the company's overtime pay policies, inform them about this. If the expectations around workload and time off aren't explicit, make them clear.
- Hold company-wide and within-team discussions to understand and address the company work culture, across the board and in specific contexts.
- High evaluation scores should not be reserved for employees who work 200+ hours per month. Consider a proportionate scale for rewarding employees who contribute more/put in more effort.

---
---

| File | Description |
|---|---|
| `saliford_motors_analysis.ipynb` | Full analysis — EDA, cleaning, modeling, organized via the PACE framework |
| `HR_capstone_dataset.csv` | Source data (14,999 records) — [Kaggle: HR Analytics and Job Prediction](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction) |
| `confusion_matrix.png` | Test-set confusion matrix for the logistic regression model |



| Variable | Description |
|---|---|
| `satisfaction_level` | Employee-reported job satisfaction (0–1) |
| `last_evaluation` | Score from last performance review (0–1) |
| `number_project` | Number of projects assigned |
| `average_monthly_hours` | Average hours worked per month |
| `tenure` | Years at the company |
| `work_accident` | Whether the employee had a workplace accident |
| `left` | Whether the employee left (target variable) |
| `promotion_last_5years` | Promoted in the last 5 years? |
| `department` | Employee's department |
| `salary` | Salary tier (low/medium/high) |

