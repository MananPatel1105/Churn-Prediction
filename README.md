# Telco Customer Churn Prediction

This project aims to predict customer churn for a telecommunications company using machine learning. The dataset used contains various attributes related to customer demographics, account information, and service usage. The final model is deployed as a web application using Flask.

## Table of Contents
- [Installation](#installation)
- [Dataset Information](#dataset-information)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Data Preprocessing](#data-preprocessing)
- [Model Training](#model-training)
- [Model Evaluation](#model-evaluation)
- [Web Application](#web-application)
- [Conclusion](#conclusion)
- [References](#references)

## Installation

To get started with the project, Install the required Libraries

-`Python`
-`Numpy`
-`Scikit-Learn`
-`pickle`

## Dataset Information

The dataset contains various features related to customer demographics, account information, and services used. Here are the key attributes:

- `SeniorCitizen`
- `MonthlyCharges`
- `TotalCharges`
- `gender`
- `Partner`
- `Dependents`
- `PhoneService`
- `MultipleLines`
- `InternetService`
- `OnlineSecurity`
- `OnlineBackup`
- `DeviceProtection`
- `TechSupport`
- `StreamingTV`
- `StreamingMovies`
- `Contract`
- `PaperlessBilling`
- `PaymentMethod`
- `tenure`

## Exploratory Data Analysis (EDA)

Initial analysis involves loading the dataset, examining its structure, and summarizing key statistics. This helps in understanding the distribution of data and identifying any missing values.

Key observations from EDA:
1. The average tenure is approximately 32.37 months.
2. The average monthly charge is around $64.76.
3. A significant percentage of customers have a high monthly charge and short tenure, correlating with higher churn rates.

## Data Preprocessing

### Handling Missing Values

The `TotalCharges` column was initially non-numeric. After converting it to numeric, there were 11 missing values. These were dropped since they represent a small fraction (0.15%) of the dataset.

### Feature Engineering

- **Tenure Groups**: Customers were binned into tenure groups (e.g., 1-12 months, 13-24 months).
- **Dropping Unnecessary Columns**: Columns like `customerID` and `tenure` were removed.

### Encoding Categorical Variables

Categorical variables were converted into dummy variables using `pd.get_dummies`.

### Target Variable

The target variable `Churn` was converted to a binary numeric variable (Yes=1, No=0).

## Model Training

### Decision Tree Classifier

A decision tree model was trained with the following parameters:
- Criterion: Gini
- Max Depth: 6
- Min Samples Leaf: 8

### Random Forest Classifier

A random forest model was trained with:
- Number of Estimators: 100
- Criterion: Gini
- Max Depth: 6
- Min Samples Leaf: 8

### Handling Imbalanced Data

The dataset is imbalanced, with a majority of customers not churning. To address this, SMOTEENN (Synthetic Minority Over-sampling Technique and Edited Nearest Neighbors) was used for resampling.

## Model Evaluation

Models were evaluated based on accuracy, precision, recall, and F1-score. The Random Forest classifier performed better than the Decision Tree classifier.

Confusion matrices and classification reports were generated for both models.

## Web Application

A Flask web application was developed to deploy the model. Users can input customer details and get predictions on whether a customer is likely to churn.

### Running the Web Application

To run the web application:

```bash
python app.py
```

Navigate to `http://127.0.0.1:5000/` in your web browser to access the application.

## Conclusion

Key insights from the analysis:
1. Customers with electronic check payments are more likely to churn.
2. Month-to-month contract customers have higher churn rates.
3. Lack of online security and tech support are significant churn indicators.
4. Non-senior citizens tend to churn more.

## References

1. [Telco Customer Churn Dataset](https://www.kaggle.com/blastchar/telco-customer-churn)
2. [Scikit-learn Documentation](https://scikit-learn.org/stable/user_guide.html)
3. [Flask Documentation](https://flask.palletsprojects.com/en/2.0.x/)

---

This README provides a comprehensive overview of the Telco Customer Churn Prediction project. For any further questions or contributions, please open an issue or submit a pull request on the GitHub repository.
