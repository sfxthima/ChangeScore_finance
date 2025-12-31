# Fintech Portfolio Project - Transaction Risk Analysis

## Overview

This project is a hands-on exploration of financial transaction risk analysis using a synthetic dataset of customer transactions. The goal is to identify unusual or potentially high-risk transactions by calculating a Change Score for each transaction based on three key components:

1. RegionScore: flags transactions in unusual countries compared to a customer's typical behavior
2. FrequencyScore: captures deviations in the number or timing of transactions
3. AmountScore: highlights unusually large or small transactions relative to the customer's average spending

The project integrates SQL via SQLite for baseline calculations, Python with Pandas for data processing, and visualization for insights.

---

## Project Structure

```
FintechPortfolio/
├─ ChangeScore.ipynb                # Main notebook with analysis
├─ data/
│   └─ transaction.xlsx             # Raw dataset
├─fintech.db                        # SQLite database with transaction table
├─ output/
│   └─ ChangeScore_output.csv       # Final transactions with ChangeScore
├─ plots/
│   └─ top_transactions.png         # Top flagged transactions visualization
├─ README.md                        # This file
```

---

## Methodology

1. Data Preparation
   Load transactions from CSV or Excel into a SQLite database. Clean missing or invalid entries for Customer_ID, Amount_in_euros, and Country_of_Transaction.

2. Baseline Calculations
   Amount baseline calculates average spending per customer.
   Frequency baseline calculates average number of transactions per day.
   Region baseline identifies typical transaction countries per customer using SQL window functions.

3. Change Score Computation
   Combine the three component scores using a weighted formula:

```
ChangeScore = w1*RegionScore + w2*FrequencyScore + w3*AmountScore
```

Weights can be adjusted depending on which behavior matters most.

4. Visualization
   Top flagged transactions are visualized using bar charts and bubble charts.
   Distribution of ChangeScore is shown via histograms to highlight outliers.

5. Output
   ChangeScore_output.csv contains all transactions with their calculated scores.
   top_transactions.png highlights the most unusual transactions for portfolio demonstration.

---

## Tools and Technologies

Python (Pandas, Numpy, Matplotlib, Seaborn) for data processing and visualization
SQLite for SQL calculations
Jupyter Notebook for workflow documentation and interactive analysis

---

## Key Takeaways

Combining SQL and Python allows robust baseline computations.
Weighted ChangeScore captures complex patterns like high-value transactions in unusual locations.
Visualization makes patterns and anomalies easy to communicate in a portfolio or professional setting.

---

## Notes

All data used is synthetic for portfolio purposes.
The project demonstrates an end-to-end fintech risk analysis workflow from data ingestion to processing, scoring, and visualization.

---

## Next Steps

Expand the dataset to include more transaction features such as merchant category, payment method, and device information.
Experiment with different weight combinations in the Change Score formula to optimize anomaly detection.
Implement real-time scoring by connecting the workflow to a streaming transaction system.
Use machine learning models for predictive risk scoring, comparing results with the weighted formula.
Add interactive visualizations or dashboards for easier exploration of flagged transactions.

---

