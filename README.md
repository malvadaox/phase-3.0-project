# SYRIATEL CUSTOMER CHURN PROJECT
______________________________________________________________________

## Table of Contents

1. [Project Overview](#Project-Overview)
   - [Objective](#Objective)
   - [Business Problem](#Business-Problem)
   - [Business understanding ](#Business-Understanding)
   - [Tools and Libraries Used](#tools-and-libraries-used)
2. [Steps and Methodology](#steps-and-methodology)
   - [Data Preprocessing](#data-preprocessing)
     - [Data Cleaning](#data-cleaning)
     - [Feature Engineering](#feature-engineering)
     - [Encoding Categorical Variables](#encoding-categorical-variables)
     - [Scaling](#scaling)
   - [Handling Class Imbalance](#handling-class-imbalance)
   - [Modeling](#modeling)
     - [Hyperparameter Tuning](#hyperparameter-tuning)
   - [Model Evaluation](#model-evaluation)
3. [Results and Insights](#results-and-insights)
4. [Recommendations](#Recommendations)
5. [Conclusion](#Conclusion)



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

### 1. **Data Preprocessing**

The dataset was preprocessed to handle any missing values, remove unnecessary columns, and encode categorical variables.

#### Data Cleaning:
- Removed irrelevant columns (e.g., `phone number`).
- Handled missing data by filling with the median of respective columns.

#### Feature Engineering:
- Created a new feature `total engagement`, which sums up the total usage of day, evening, and night minutes.
- Created a binary feature `high_service_calls`, indicating if a customer had more than 3 customer service calls.

#### Encoding Categorical Variables:
- **Label Encoding** was used for columns like `state`, `international plan`, and `voice mail plan`.


#### Scaling:
- The dataset was scaled using `StandardScaler` to ensure that numerical features are on a similar scale for model training.

### 2. **Handling Class Imbalance**
- After evaluating the model performance on the initial data, it was determined that the dataset suffers from class imbalance.
- **SMOTE** (Synthetic Minority Over-sampling Technique) was applied to balance the classes in the training data.
- **Class weights** were also applied in models like Logistic Regression and Random Forest to handle the imbalance.

### 3. **Modeling**

Two classification models were used:
- **Logistic Regression**: A baseline model for comparison.
- **Random Forest**: A more complex model with hyperparameter tuning.

#### Hyperparameter Tuning:
- **Grid Search** was used to find the optimal hyperparameters for the Random Forest model.
- We tuned the number of trees (`n_estimators`) and the maximum depth (`max_depth`) of the trees.

### 4. **Model Evaluation**

After training the models, we evaluated them using several metrics:
- **Accuracy**: Overall classification accuracy.
- **Classification Report**: Precision, Recall, and F1-Score for both classes (churned and non-churned).
- **ROC-AUC Score**: Evaluates the model's ability to distinguish between the two classes.
- **Confusion Matrix**: To visualize the true positive, false positive, true negative, and false negative predictions.

Visualizations such as the **Confusion Matrix** and **Feature Importance** (for Random Forest) were also generated to provide deeper insights into model performance.


