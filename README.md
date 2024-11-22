# Credit Card Fraud Detection using Machine Learning

## 1. Introduction

### 1.1 Problem Statement
Credit card fraud is a major financial problem that causes significant losses each year. Traditional methods of fraud detection struggle to keep up with the high volume of transactions. This project aims to leverage machine learning algorithms to detect fraudulent credit card transactions effectively.

### 1.2 Project Objective
The goal of this project is to build a machine learning model that detects fraudulent credit card transactions. Specific objectives include:
- **Fraud detection**: Build a model that classifies transactions as legitimate or fraudulent.
- **Comparison of different models**: Evaluate the performance of various models such as CatBoost, XGBoost, and LightGBM.
- **Use of evaluation metrics**: Focus on precision, recall, F1-score, and ROC AUC to evaluate the models, considering class imbalance.

## 2. Data Exploration

### 2.1 Columns and Their Descriptions
The dataset consists of the following columns:
- **trans_date_trans_time**: Timestamp of the transaction.
- **cc_num**: Encrypted credit card number.
- **merchant**: Merchant or store where the transaction occurred.
- **category**: Category of the transaction (e.g., groceries, entertainment).
- **amt**: Transaction amount.
- **first, last**: Cardholder's first and last names.
- **gender**: Gender of the cardholder.
- **street, city, state, zip**: Cardholder’s address details.
- **lat, long**: Latitude and longitude of the cardholder's address.
- **city_pop**: Population of the city.
- **job**: Cardholder's occupation.
- **dob**: Date of birth of the cardholder.
- **trans_num**: Unique transaction number.
- **is_fraud**: Target column indicating whether the transaction is fraudulent.

### 2.2 Exploratory Data Analysis (EDA)
- **Size of dataset**: 1,296,675 rows and 24 columns.
- **Missing data**: No missing values except in `merch_zipcode`.
- **Data types**: Various data types, including integers, floats, and objects (strings).
- **Duplications**: No duplicated rows.
- **Imbalance in fraud detection**: Only 0.58% of transactions are fraudulent.

### 2.3 Data Visualization
- **Fraud distribution**: Visualization of fraudulent transactions.
- **Distribution of fraud by category**: Bar chart to explore fraud across different categories.
- **Transaction amounts**: Histograms for numerical features.
- **Time-based fraud patterns**: Visualizations of fraud transactions by month, year, hour, and day of the week.

## 3. Data Manipulation

### 3.1 Detecting and Removing Outliers
- Outliers are detected in the **amt** (transaction amount) column using a threshold of 2700. This results in the removal of 430 outliers (0.03% data loss).

### 3.2 Dropping Unnecessary Features
The following columns were removed for model training:
- `Unnamed: 0`, `first`, `last`, `street`, `city`, `state`, `zip`, `trans_num`, `unix_time`, and `merch_zipcode`.

### 3.3 Feature Creation
- New features were created from the `trans_date_trans_time` column, including:
  - `trans_year`, `trans_month`, `trans_day`, `trans_season`, `trans_weekday`, `trans_hour`, `trans_minute`, and `trans_second`.
- The **age** of the cardholder at the time of the transaction was also calculated.
- **Geographical distance** between the cardholder and merchant using latitude and longitude was computed using the `geopy` library.

### 3.4 Encoding
Categorical features were encoded using appropriate techniques to prepare the dataset for model training.

## 4. Model Training

### 4.1 Model Selection
We experimented with different machine learning models, including:
- **CatBoost**
- **XGBoost**
- **LightGBM**

### 4.2 Evaluation Metrics
The models were evaluated using:
- **Precision**, **Recall**, **F1-Score**, and **ROC AUC** to account for the class imbalance and ensure reliable performance.

## 5. Results
The model comparison results show the effectiveness of **XGBoost** in detecting fraudulent transactions with the highest **F1-score** and **ROC AUC**.

## 6. Conclusion
This project demonstrates the potential of machine learning algorithms in detecting credit card fraud. Future improvements can be made by tuning hyperparameters and incorporating additional data sources.

## 7. Acknowledgments
- The dataset used in this project is available from [Kaggle: Credit Card Transactions Dataset](https://www.kaggle.com/datasets/priyamchoksi/credit-card-transactions-dataset).
- Special thanks to all contributors for their valuable work in the field of fraud detection.

