# Healthcare Claims Expenditure Analysis | Power BI

## 1. Project Overview.

This project focuses on analysing healthcare insurance claims to understand the relationship between claimed amounts and approved amounts, identify expenditure patterns, and determine the categories contributing most to overall claims expenditure.

Using Power BI, I explored a healthcare claims dataset containing 10,000 records to identify trends across insurance types, medical specialties, and submission periods.

The objective was to transform raw claims data into meaningful insights that could help management monitor healthcare expenditure and identify areas requiring further investigation.

## 2. Business Problem

Healthcare organisations need to understand how much is being claimed, how much is being approved, and where their expenditure is concentrated.

The analysis was guided by the following business questions:

- What is the total amount claimed compared with the total approved amount?
- What is the difference between claimed and approved amounts?
- Which insurance types account for the highest claim expenditure?
- How does claim expenditure change over time?
- Which medical specialties contribute most to total claims expenditure?
- Which periods recorded the highest claim amounts?

## 3. Tools Used

- **Power BI Desktop:** Data modelling, analysis, visualisation, and dashboard development.
- **Power Query:** Data inspection and preparation.
- **DAX:** Creating calculated measures and columns.
- **Microsoft Excel:** Supporting data inspection where necessary.

## 4. Data Preparation and Cleaning

Before building the dashboard, I examined the dataset to understand its structure and identify issues that could affect the analysis.

The preparation process included:

1. Imported the healthcare claims dataset into Power BI.
2. Inspected the available columns and checked the data types.
3. Reviewed missing values in important categorical fields.
4. Examined the claim submission date column to prepare it for time-based analysis.
5. Created additional date-related columns to support monthly analysis.
6. Reviewed claim amounts and approved amounts to ensure they could be used for numerical analysis.
7. Retained missing insurance and specialty categories for visibility rather than silently excluding their associated records.

I also examined the claim status and approved amount fields to understand how the recorded approval figures should be interpreted.

## 5. Data Analysis and DAX Measures

I created DAX measures to calculate the key metrics required for the analysis.

### Key Measures

**Total Claim Amount**
```DAX
Total Claim Amount =
SUM('healthcare_fraud_detection'[Claim_Amount])
```

**Total Approved Amount**
```DAX
Total Approved Amount =
SUM('healthcare_fraud_detection'[Approved_Amount])
```

**Claim Approval Gap**
```DAX
Claim Approval Gap =
[Total Claim Amount] - [Total Approved Amount]
```

**Approval Percentage**
```DAX
Approval Percentage =
DIVIDE(
    [Total Approved Amount],
    [Total Claim Amount],
    0
)
```

**Total Claims**
```DAX
Total Claims =
DISTINCTCOUNT('healthcare_fraud_detection'[Claim_ID])
```

### Additional Calculated Columns

I created a Month Name column using the FORMAT function and a Month Number column using the MONTH function.

These columns helped organise the data for monthly comparisons and chronological sorting.

## 6. Key Performance Indicators (KPIs)

The analysis produced the following overall metrics:

| KPI | Result |
|---|---:|
| Total Claim Amount | 5,728,044.06 |
| Total Approved Amount | 4,755,141.57 |
| Claim Approval Gap | 972,902.49 |
| Approval Amount / Claim Amount | 83.02% |
| Total Claims | 10,000 |

The approval percentage represents the ratio of recorded approved amounts to total claimed amounts. It should not be interpreted as the percentage of individual claims approved.

## 7. Dashboard Visualisations
[Healthcare Claims Dashboard](images/healthcare_claims_dashboard.png)

The Power BI dashboard was designed to provide a clear overview of healthcare claims expenditure.

The following visualisations were developed:

- **KPI Cards:** Display total claims, total claim amount, total approved amount, claim approval gap, and approval percentage.
- **Yearly Comparison:** Compares claimed and approved amounts across reporting years.
- **Insurance Type Analysis:** Compares total claim expenditure across different insurance types.
- **Monthly Trend Analysis:** Tracks changes in claimed and approved amounts over time.
- **Provider Specialty Analysis:** Identifies medical specialties contributing the highest claim expenditure.
- **Detailed Breakdown:** Supports further examination of expenditure across categories.

## 8. Key Findings

The analysis revealed several important observations:

1. The total claim amount was higher than the recorded approved amount, resulting in a difference of 972,902.49.

2. Medicare recorded the highest total claim amount among the insurance types, followed closely by Self-Pay and Medicaid.

3. Internal Medicine recorded the highest claim expenditure among the medical specialties, followed by General Practice.

4. December 2022 recorded the highest monthly claim amount, indicating a period that may require further investigation.

5. The overall ratio of approved amounts to claimed amounts was approximately 83.02%.

## 9. Business Recommendations

Based on the findings, the following actions are recommended:

- Investigate the difference between claimed and approved amounts by reviewing claim statuses and individual claim records.
- Examine expenditure across insurance types to understand differences in claim volumes and average claim values.
- Investigate Internal Medicine and General Practice to understand the factors contributing to their higher claim expenditure.
- Review December 2022 claims to identify the factors responsible for the expenditure peak.
- Monitor monthly claim trends to identify unusual increases and support better expenditure planning.

These findings highlight areas for further investigation and should not be treated as evidence of fraud or inappropriate spending.

## 10. Conclusion

This project provided an opportunity to apply Power BI to a healthcare claims business problem.

Through data preparation, DAX calculations, and interactive visualisations, I was able to examine the relationship between claimed and approved amounts, compare expenditure across insurance categories and medical specialties, and identify periods with higher claim activity.

The project strengthened my understanding of how data analysis can support financial monitoring, operational decision-making, and evidence-based business recommendations.

---

**Project Category:** Data Analytics | Healthcare

**Tool:** Microsoft Power BI

**Role:** Aspiring Data Analyst
