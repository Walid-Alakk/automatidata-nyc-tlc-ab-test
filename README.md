# automatidata-nyc-tlc-ab-test

**Course 3 End-of-Course Project | Google Advanced Data Analytics Certificate**  
*The Power of Statistics*

---

## Project Overview

This project continues the Automatidata fictional workplace scenario. As a data analyst at **Automatidata**, I conducted an A/B test on the 2017 NYC Yellow Taxi Trip dataset to determine whether payment type (credit card vs. cash) has a statistically significant effect on fare amount — a key question raised by the New York City Taxi & Limousine Commission (TLC).

---

## Business Goal

Analyze whether credit card customers pay statistically significantly higher fares than cash customers, and communicate findings to both technical (Automatidata) and non-technical (TLC) stakeholders.

---

## Dataset

**2017 Yellow Taxi Trip Data** — provided by NYC TLC

| Property | Value |
|---|---|
| Rows | 22,699 |
| Columns | 18 |
| Missing values | 0 |
| A/B Groups | Credit card (type 1) vs. Cash (type 2) |

---

## Repository Structure

```
Course 3 _ The Power of Statistics/
├── Activity_ Course 3 _ ...project lab.py      # Main analysis script (all responses filled in)
├── Activity_ Course 3 _ ...project lab.ipynb   # Jupyter notebook version
├── Course3_Statistical_Analysis_Report.docx    # Full statistical analysis report
├── Course3_Executive_Summary.pptx              # 9-slide executive presentation
├── course3_plots/                              # All 6 generated charts (PNG, 150 DPI)
│   ├── 01_mean_fare_by_payment.png
│   ├── 02_boxplot_fare_by_payment.png
│   ├── 03_hist_fare_by_payment.png
│   ├── 04_trip_count_by_payment.png
│   ├── 05_ttest_result.png
│   └── 06_mean_fare_with_ci.png
└── README.md
```

---

## Methodology (PACE Framework)

### Plan
- **Research question**: Does payment type significantly affect fare amount?
- **H₀**: No difference in mean fare between credit card and cash customers
- **Hₐ**: There is a difference in mean fare between the two groups
- **Significance level**: α = 0.05

### Analyze & Construct
- Computed descriptive statistics across all 22,699 records
- Grouped mean fare by payment type
- Identified data quality anomalies (negative fares, extreme outliers)

### Execute
- Ran two-sample Welch's t-test (`scipy.stats.ttest_ind`, `equal_var=False`)
- Interpreted results and communicated findings with business context

---

## Key Results

| Metric | Value |
|---|---|
| Credit card mean fare | $13.43 |
| Cash mean fare | $12.21 |
| Difference | ~$1.22 |
| T-statistic | 6.8668 |
| P-value | < 0.0001 |
| Decision | **Reject H₀** |

The difference is statistically significant at α = 0.05. Credit card customers pay higher average fares.

---

## Business Insights

- The ~$1.22 fare gap likely reflects that longer, higher-value trips (e.g., airport runs) are disproportionately paid by credit card.
- Payment type can serve as a revenue signal for TLC — credit card trips yield more trackable revenue.
- Encouraging credit card adoption may improve driver income visibility, since cash tips are not recorded in the dataset.

---

## Assumptions & Limitations

- **Self-selection bias**: Customers choose their payment method — this is not a true randomized experiment. Causal conclusions cannot be drawn.
- **Confounders**: The difference may be driven by trip distance or RatecodeID (airport rates), not payment type itself.
- **Cash tip underreporting**: ~33% of trips are cash; tips recorded as $0, biasing any tip analysis.
- **Data quality**: `fare_amount` min = -$120, max = $999.99 — cleaning required before modeling.

---

## Recommended Next Steps

1. Clean anomalous records before regression model training
2. Conduct multivariate analysis to separate payment type effect from confounders
3. Expand tip analysis using credit card records only
4. Proceed to Course 4: regression model (`fare_amount` ~ `trip_distance` + time features)
5. Build Tableau stakeholder dashboard for TLC executives

---

## Tools & Technologies

- Python 3 | pandas | numpy | scipy.stats | matplotlib | seaborn
- Jupyter Notebook / Python script
- Microsoft Word (statistical analysis report)
- Microsoft PowerPoint (executive summary)

---

## Author

**Walid** | Data Analyst at Automatidata (fictional scenario)  
Google Advanced Data Analytics Certificate — Course 3

---

## Related

- **Course 1**: `automatidata-nyc-tlc-foundations` — initial data inspection
- **Course 2**: `automatidata-nyc-tlc-eda` — full exploratory data analysis
