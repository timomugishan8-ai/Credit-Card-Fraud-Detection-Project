# Exploratory Data Analysis Report

## Overview
This report summarizes the key findings from the fraud dataset visualizations and derived statistics. The dataset contains 100,000 credit card transactions, with `IsFraud` indicating fraudulent activity.

## Dataset balance
- Total transactions: 100,000
- Non-fraud transactions: 99,000 (99.0%)
- Fraud transactions: 1,000 (1.0%)

The dataset is highly imbalanced toward non-fraud transactions, so analysis should account for the low fraud prevalence.

## Time period insights
### Month
- Highest total transaction volume months: `2024-07`, `2024-03`, `2023-12`, `2024-05`, `2024-08`, `2024-09`.
- These months represent the largest aggregate amounts, suggesting periods of elevated spending activity.

### Day of week
- Total transaction amount is relatively even across weekdays and weekends.
- The top days by total amount are: Saturday, Sunday, Tuesday, Wednesday, Friday, Thursday, Monday.
- This indicates that large transaction volume is distributed broadly across the entire week, with slightly more activity on weekends.

### Hour of day
- Highest transaction amounts occur during these hours: `16`, `04`, `12`, `06`, `15`, `14`, `21`, `10`.
- Late afternoon and early morning hours appear among the top contributors.
- This may suggest a mix of normal business hours and unusual transaction timing associated with higher amounts.

## Location and fraud insights
### Fraud rate by location
- Top locations by fraud rate were: `New York`, `San Diego`, `Houston`, `Phoenix`, `San Antonio`, `Dallas`, `Los Angeles`, `Chicago`, `Philadelphia`, `San Jose`.
- Fraud rates are still low overall, ranging around 0.8% to 1.16% for the highest-risk locations.
- Average transaction values in these top locations are all around the mid-2,400 to mid-2,500 range.

### Location conclusions
- `New York` and `San Diego` have the highest observed fraud rates, despite being major transaction centers.
- The average transaction amount for the top fraud-risk locations remains similar to the dataset average, so location appears to matter more for fraud probability than transaction size alone.

## Fraud and transaction amount
- A boxplot comparing `Amount` for fraud vs non-fraud transactions was created.
- Because transaction amount distributions are likely skewed, the plot helps identify whether fraud values are generally higher or contain more extreme outliers.
- The high-level insight is that fraud can occur across a wide amount range, but visual comparison is necessary to confirm whether fraud amounts concentrate at the top end.

## Transaction type insights
### Fraud rate by transaction type
- `refund` has a slightly higher fraud rate at `1.0114%`
- `purchase` has a fraud rate of `0.9886%`

### Transaction type conclusions
- `refund` transactions are marginally more likely to be fraudulent than `purchase` transactions in this dataset.
- Because the fraud rates are close, both transaction types should remain under scrutiny.

## Merchant fraud rate insights
### Top merchants by fraud rate (minimum 10 transactions)
- Highest fraud rates were observed for merchant-location pairs such as:
  - Merchant `112` in `Los Angeles` (20.0% fraud, 10 transactions)
  - Merchant `959` in `Dallas` (20.0% fraud, 10 transactions)
  - Merchant `216` in `New York` (20.0% fraud, 15 transactions)
  - Merchant `204` in `San Diego` (20.0% fraud, 10 transactions)
  - Merchant `837` in `Chicago` (20.0% fraud, 10 transactions)
- The average amounts for these top-risk merchant-location combinations vary, but are generally in the range of 1,500 to 3,200.

### Merchant conclusions
- A small number of merchant-location pairs show very high fraud rates, but the sample sizes are also small.
- These merchants should be flagged for deeper review, especially those with at least 10 transactions and a fraud rate above 18%.

## Recommended focus areas
- Monitor `New York` and `San Diego` for fraud risk due to their elevated fraud rates.
- Inspect `refund` transactions more closely, as they are slightly more fraud-prone than purchases.
- Review high-fraud merchant-location pairs with low transaction counts carefully, as they may represent either real risk or statistical noise.
- Use hour-of-day patterns to search for abnormal high-amount activity in both evening and early morning periods.

## Notes
- Because fraud is only 1% of the dataset, any model or dashboard should respect class imbalance.
- Additional feature engineering and higher-resolution time segmentation may sharpen these findings further.
