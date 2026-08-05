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

## Project Structure
- `data/` — raw and processed datasets
- `notebooks/` — exploratory data analysis and modeling notebooks
- `models/` — trained models and artifacts
- `dashboards/` — visual insights and Power BI reports
- `sql/` — query files and data transformation scripts

## Objective
The primary objective is to build a fraud detection pipeline that is interpretable, regionally relevant, and effective for institutions operating in East Africa. The analysis aims to support decision-making by identifying fraud risk factors, recommending mitigation strategies, and highlighting the importance of tailored fraud prevention solutions in developing digital financial markets.
