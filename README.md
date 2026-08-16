# Credit Card Fraud Detection Project

## Introduction
This project demonstrates a complete fraud detection workflow for credit card transactions using Python, SQL, Power BI, and Machine Learning. The goal is to identify patterns that distinguish fraudulent transactions from legitimate activity and to build a reliable model that helps financial institutions reduce loss, improve customer trust, and strengthen fraud prevention.

## Business Questions
This analysis is guided by the following core business questions:
1. Who is committing fraud?
2. When does fraud occur most frequently?
3. Which transaction patterns indicate potential fraud?
4. How can financial institutions reduce losses and improve fraud detection?

## Relevance in Uganda and East Africa
Credit card fraud is a growing concern in Uganda and the broader East African region, where digital payments and mobile banking adoption are expanding rapidly. Fraud detection models are especially valuable because:
- Financial institutions in the region are increasing digital transaction volume, which raises exposure to sophisticated fraud schemes.
- Consumers and businesses depend on safe payment ecosystems to build trust in digital financial services.
- Early fraud detection reduces operational costs and supports regulatory compliance in fast-evolving markets.
- Locally relevant models can help banks and payment providers tailor fraud prevention to transaction patterns common in Uganda and neighboring markets.

Key fraud types relevant to the region include:
  - Mobile money fraud
  - Bank transaction fraud
  - Identity theft
  - Account takeover
  - Fake merchant transactions
  - Loan application fraud

## Key Observations
- The dataset contains 100,000 transactions with no missing values in the numeric fields.
- `TransactionID` and `MerchantID` behave like identifier fields rather than meaningful numerical predictors.
- Transaction amounts range from approximately 1.05 to 4,999.77, with a mean and median near the midpoint, indicating a wide but balanced amount distribution.
- The target variable `IsFraud` is highly imbalanced: only about 1% of transactions are fraudulent. This requires modeling techniques that emphasize fraud recall and class imbalance handling rather than raw accuracy.
- Categorical fields such as transaction type and location need additional exploration, as they can provide important context for fraud patterns.

## EDA Findings
- Fraud is rare: only 1% of transactions are labeled fraudulent, so models should prioritize sensitivity and class imbalance mitigation.
- Highest transaction volume months are `2024-07`, `2024-03`, `2023-12`, `2024-05`, `2024-08`, and `2024-09`, suggesting peak spending periods.
- Transaction volume is broadly distributed across the week, with slightly higher totals on weekends.
- High-value transaction activity is concentrated in afternoon and early morning hours, notably around 16:00, 04:00, 12:00, 06:00, 15:00, 14:00, 21:00, and 10:00.
- Locations with the highest fraud rates include `New York`, `San Diego`, `Houston`, `Phoenix`, `San Antonio`, `Dallas`, `Los Angeles`, `Chicago`, `Philadelphia`, and `San Jose`.
- Average transaction amounts in these high-fraud locations are similar to the dataset average, indicating that location may be a stronger fraud signal than transaction amount alone.
- `refund` transactions are slightly more fraud-prone than `purchase` transactions, with fraud rates of approximately 1.0114% and 0.9886%, respectively.
- Several merchant-location pairs show very high fraud rates in small samples, including merchants in Los Angeles, Dallas, New York, San Diego, and Chicago. These require deeper review.

## Feature Engineering and Modeling Notebook Coverage
This notebook focuses on preparing the fraud dataset for supervised learning and building the foundation of the classification pipeline.

### What was covered
- Reviewed the raw transaction dataset and inspected the structure, variable types, and unique values.
- Identified the target variable (`IsFraud`) and the fields that should be excluded from modeling, such as `TransactionID` and `MerchantID`, which behave more like identifiers than predictive features.
- Examined the class distribution and confirmed that fraud is highly imbalanced, making standard accuracy insufficient as a primary model metric.
- Converted the transaction date into a datetime format and engineered new time-based features such as:
  - `TransactionHour`
  - `TransactionDay`
  - `TransactionMonth`
  - `TransactionYear`
- Prepared the feature matrix by dropping non-predictive identifiers and the target variable.
- Split the data into training and testing sets using `train_test_split` with `test_size=0.2` and `stratify=y` to preserve the fraud rate in both subsets.
- Verified the class distribution in both the training and testing sets to confirm consistency with the original dataset.
- Defined preprocessing steps for the model pipeline:
  - numeric features: `StandardScaler`
  - categorical features: `OneHotEncoder`
- Used `ColumnTransformer` to apply the correct transformations to each feature type in a clean and reproducible way.
- Fitted the preprocessing transformer on the training data only and transformed the test data using the same configuration to avoid data leakage.
- Evaluated model quality using multiple metrics, including:
  - `accuracy_score`
  - `precision_score`
  - `recall_score`
  - `f1_score`
  - `confusion_matrix`
  - `classification_report`

### Key takeaway
The notebook demonstrates the standard machine learning workflow for fraud detection: understanding the dataset, engineering useful features, preserving data integrity during splitting, preprocessing appropriately, and evaluating results using metrics designed for imbalanced classification problems.

## Project Structure
- `data/` — raw and processed datasets
- `notebooks/` — exploratory data analysis and modeling notebooks
- `models/` — trained models and artifacts
- `dashboards/` — visual insights and Power BI reports
- `sql/` — query files and data transformation scripts

## Objective
The primary objective is to build a fraud detection pipeline that is interpretable, regionally relevant, and effective for institutions operating in East Africa. The analysis aims to support decision-making by identifying fraud risk factors, recommending mitigation strategies, and highlighting the importance of tailored fraud prevention solutions in developing digital financial markets.
