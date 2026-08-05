# Retail Customer Intelligence

End-to-end e-commerce customer analytics and repeat-purchase prediction using
the Online Retail II transaction dataset.

## Project Overview

This project transforms raw retail transaction records into:

- merchandise sales insights,
- RFM customer segments,
- data-driven customer clusters,
- cohort retention measurements,
- three-month repeat-purchase predictions,
- SHAP-based model explanations,
- actionable customer-management recommendations.

## Business Questions

The project addresses the following questions:

1. How should valid merchandise sales be separated from cancellations,
   adjustments and non-merchandise transactions?
2. Which months, countries and products generate the strongest merchandise
   performance?
3. Which customers generate the greatest value?
4. What distinct customer behaviour profiles exist?
5. How does customer activity change after the first observed purchase?
6. Can future three-month repeat purchase be predicted using historical
   customer behaviour?
7. Which customer behaviours drive the prediction model?

## Dataset

The project uses the Online Retail II transaction dataset.

The combined raw dataset contains approximately 1.07 million product-line
records covering December 2009 through December 2011.

The raw Excel file is not included in the repository. Instructions are
available in `data/raw/README.md`.

## Analytical Workflow

1. Data loading and structural inspection
2. Data-quality analysis
3. Transaction-type classification
4. Merchandise-sales definition
5. Monthly, country and product analysis
6. Exact cancellation matching
7. Customer-level feature engineering
8. RFM segmentation
9. K-Means customer clustering
10. Cohort retention analysis
11. Temporal repeat-purchase classification
12. SHAP model interpretation
13. Business recommendations

## Key Results

- Champions and Loyal Customers represented approximately 31.7% of identified
  customers while generating approximately 79.2% of customer merchandise
  value.
- K-Means identified three customer profiles:
  - Active High-Value Customers
  - Lapsing Occasional Customers
  - Inactive One-Time Customers
- Monthly active-customer retention generally remained around 18%–21% at the
  selected post-acquisition horizons.
- The final LightGBM model achieved:
  - ROC-AUC: 0.77
  - PR-AUC: 0.79
  - Balanced accuracy: 0.70
  - Precision: 0.76
  - Recall: 0.60
  - F1-score: 0.67
- SHAP identified invoice frequency, recency, observed purchase span and total
  spending as the strongest predictive signals.

## Modelling Strategy

The classification task predicts whether an existing customer will make at
least one retained merchandise purchase during the following three complete
months.

Features are calculated from the preceding twelve-month observation window.

The temporal evaluation design uses:

- three historical training snapshots,
- one validation snapshot,
- one untouched future holdout snapshot.

The validation period is used for model and threshold selection. The temporal
holdout is used only once for final evaluation.

## Customer Segments

### Active High-Value Customers

Recent, frequent and high-value customers with broad product engagement.

### Lapsing Occasional Customers

Customers with previous purchasing activity whose recency and frequency
indicate declining engagement.

### Inactive One-Time Customers

Customers with limited purchase history and long inactivity.

## Main Business Recommendations

- Protect high-value customers through loyalty and personalised service rather
  than unnecessary blanket discounts.
- Intervene when customer activity begins to decline instead of waiting for
  complete inactivity.
- Use low-cost onboarding and second-purchase campaigns for one-time customers.
- Prioritise campaign audiences using model probabilities, expected value and
  contact cost.
- Monitor seasonal changes, probability calibration and threshold performance.
- Evaluate campaign impact through controlled A/B tests.

## Repository Structure

```text
retail-customer-intelligence/
├── README.md
├── requirements.txt
├── .gitignore
├── notebooks/
│   └── retail_customer_intelligence.ipynb
└── data/
    └── raw/
        └── README.md


## Installation

Clone the repository and install the required packages:

```bash
pip install -r requirements.txt
```

Place the Online Retail II workbook at:

```text
data/raw/online_retail_II.xlsx
```

Then open and run:

```text
notebooks/retail_customer_intelligence.ipynb
```



## Limitations

- The dataset covers only approximately two years.
- December 2011 is incomplete.
- Transactions without Customer ID cannot be used in customer-level analyses.
- Exact cancellation matching does not capture every possible partial-return
  pattern.
- RFM and clustering are descriptive rather than causal.
- The repeat-purchase rate changes across temporal periods.
- SHAP explains model behaviour but does not establish causality.


## Author

**İbrahim Vatansever**  
Mathematical Engineering Student  
Yıldız Technical University