# SYRIATEL CUSTOMER CHURN PROJECT
______________________________________________________________________




## Project Overview
The objective of this project is to develop a machine learning model that can predict whether a customer is likely to discontinue their relationship with SyriaTel in the near future. By identifying at-risk customers, the model will enable SyriaTel to take proactive measures to prevent churn, improve customer retention, and optimize retention strategies, ultimately reducing customer loss.

## Objective
- Build a classification model that predicts whether a customer will churn or not based on various customer data (e.g., usage statistics, service calls, etc.).
- Address class imbalance to improve model performance on the minority class (churners).


## Business Problem
SyriaTel, like most telecommunications companies, faces a challenge in maintaining customer loyalty. Customers can choose from various providers, and churn (i.e., the rate at which customers leave) represents a significant source of revenue loss. High churn rates also lead to increased customer acquisition costs and decreased market share. Understanding which customers are likely to leave can help SyriaTel take targeted actions to improve retention, reduce churn, and ultimately boost profitability.

## Business Understanding
By accurately predicting customer churn, SyriaTel can:

1.Identify at-risk customers: Target high-risk customers who are likely to churn with tailored retention strategies such as personalized offers, improved customer service, or loyalty rewards.
2.Optimize marketing spend: Focus marketing efforts on retaining existing customers, reducing the need for costly customer acquisition.
3.Improve customer experience: By understanding the drivers of churn, SyriaTel can enhance its offerings, address pain points, and boost overall satisfaction, leading to higher customer loyalty.
4.Reduce operational costs: Reducing churn can lower the costs associated with acquiring new customers to replace lost ones, thus improving profitability.

## DATA SOURCE
https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset


## Data Exploration and Analysis (EDA)

### Importing Necessary Libraries
- Python libraries such as `pandas`, `numpy`, `matplotlib`, `seaborn`, and `sklearn` were used for data manipulation, visualization, and modeling.

### Load the Dataset
- Data from Syriatel was imported for analysis.

### Analysis of the Data
- Summary statistics and distribution checks were conducted to understand data quality.
---

## Data cleaning
-Removed irrelevant columns(e.g, phone number)

### Identifying Missing Values and Duplicates
- The dataset was checked for missing values and duplicates, findings were it had none.

### Handling Missing Values and Duplicates
- No measure was taken asthere no missing values or duplicates.

---

## Data Preprocessing
If the dataset was pre-processed to handle any missing values, remove unecessary columns, and encode categorical data

### Dropping Irrelevant Columns
- Columns with no predictive value were removed.

### Encoding Categorical Variables
- Categorical features were transformed into numerical formats using one-hot encoding.

### Dependent (y) and Independent Variables (X)
- Target (churn) and predictors were clearly defined.

---

## Feature Engineering:
- Created a new feature `total engagement`, which sums up the total usage of day, evening, and night minutes.
- Created a binary feature `high_service_calls`, indicating if a customer had more than 3 customer service calls.

#### Encoding Categorical Variables:
- **Label Encoding** was used for columns like `state`, `international plan`, and `voice mail plan`.


#### Scaling:
- The dataset was scaled using `StandardScaler` to ensure that numerical features are on a similar scale for model training.

###  **Handling Class Imbalance**
- After evaluating the model performance on the initial data, it was determined that the dataset suffers from class imbalance.
- **SMOTE** (Synthetic Minority Over-sampling Technique) was applied to balance the classes in the training data.
- **Class weights** were also applied in models like Logistic Regression and Random Forest to handle the imbalance.
----
##  **Modeling**

Two classification models were used:
- **Logistic Regression**: A baseline model for comparison.
- **Random Forest**: A more complex model with hyperparameter tuning.

#### Hyperparameter Tuning:
- **Grid Search** was used to find the optimal hyperparameters for the Random Forest model.
- We tuned the number of trees (`n_estimators`) and the maximum depth (`max_depth`) of the trees.

###  **Model Evaluation**

After training the models, we evaluated them using several metrics:
- **Accuracy**: Overall classification accuracy.
- **Classification Report**: Precision, Recall, and F1-Score for both classes (churned and non-churned).
- **ROC-AUC Score**: Evaluates the model's ability to distinguish between the two classes.
- **Confusion Matrix**: To visualize the true positive, false positive, true negative, and false negative predictions.

-Visualizations such as the **Confusion Matrix**  (for Random Forest) were also generated to provide deeper insights into model performance.
-
##  Recommendations
- Focus on at-risk customers identified by the Random Forest model.
- Improve customer engagement by addressing common churn reasons.
- Continuously monitor and refine the model with updated data.

