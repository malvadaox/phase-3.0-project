# SYRIATEL CUSTOMER CHURN PROJECT

## Table of Contents

1. [Project Overview](#project-overview)
2. [Objective](#objective)
3. [Business Problem](#business-problem)
4. [Business Understanding](#business-understanding)
5. [Data Source](#data-source)
6. [Data Exploration and Analysis (EDA)](#data-exploration-and-analysis-eda)
   - [Importing Necessary Libraries](#importing-necessary-libraries)
   - [Loading the Dataset](#loading-the-dataset)
   - [Data Analysis](#data-analysis)
7. [Data Cleaning](#data-cleaning)
8. [Data Preprocessing](#data-preprocessing)
   - [Dropping Irrelevant Columns](#dropping-irrelevant-columns)
   - [Encoding Categorical Variables](#encoding-categorical-variables)
   - [Scaling](#scaling)
   - [Defining Target and Predictors](#defining-target-and-predictors)
9. [Feature Engineering](#feature-engineering)
10. [Handling Class Imbalance](#handling-class-imbalance)
11. [Modeling](#modeling)
    - [Hyperparameter Tuning](#hyperparameter-tuning)
12. [Model Evaluation](#model-evaluation)
    - [Logistic Regression](#logistic-regression)
    - [Random Forest](#random-forest)
    - [Visualization](#visualization)
13. [Conclusion](#conclusion)
14. [Recommendations](#recommendations)



## Business Problem (continued)
SyriaTel, like most telecommunications companies, faces challenges in maintaining customer loyalty. Customers can choose from various providers, and churn (i.e., the rate at which customers leave) represents a significant source of revenue loss. High churn rates also lead to increased customer acquisition costs and decreased market share. Understanding which customers are likely to leave can help SyriaTel take targeted actions to improve retention, reduce churn, and ultimately boost profitability.

## Business Understanding
By accurately predicting customer churn, SyriaTel can:
1. **Identify at-risk customers**: Target high-risk customers who are likely to churn with tailored retention strategies such as personalized offers, improved customer service, or loyalty rewards.
2. **Optimize marketing spend**: Focus marketing efforts on retaining existing customers, reducing the need for costly customer acquisition.
3. **Improve customer experience**: By understanding the drivers of churn, SyriaTel can enhance its offerings, address pain points, and boost overall satisfaction, leading to higher customer loyalty.
4. **Reduce operational costs**: Lower churn can decrease the costs associated with acquiring new customers to replace lost ones, improving profitability.

## Data Source
The dataset used for this project is publicly available on Kaggle:  
[Churn in Telecoms Dataset](https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset)

---

## Data Exploration and Analysis (EDA)

### Importing Necessary Libraries
Python libraries such as `pandas`, `numpy`, `matplotlib`, `seaborn`, and `sklearn` were used for data manipulation, visualization, and modeling.

### Loading the Dataset
- Data from Syriatel was imported and explored for analysis.

### Data Analysis
- Summary statistics and distribution checks were conducted to understand data quality and characteristics.
- Key insights about data imbalance and feature distributions were noted.

---

## Data Cleaning
- **Irrelevant Columns**: Removed columns with no predictive value (e.g., phone number).
- **Missing Values and Duplicates**: No missing values or duplicates were found in the dataset.

---

## Data Preprocessing
The dataset was preprocessed to ensure it was ready for machine learning model training.

### Key Steps
1. **Dropping Irrelevant Columns**: Removed features with no meaningful contribution to the prediction task.
2. **Encoding Categorical Variables**: Transformed categorical data (e.g., `state`, `international plan`, and `voice mail plan`) into numerical representations using label encoding.
3. **Scaling**: Used `StandardScaler` to normalize numerical features, ensuring that they were on a similar scale.
4. **Defining Target and Predictors**: Split the dataset into dependent (target) and independent (predictor) variables.

### Feature Engineering
- Created a new feature, `total engagement`, as the sum of day, evening, and night minutes.
- Added a binary feature, `high_service_calls`, to flag customers with more than three customer service calls.

### Handling Class Imbalance
- Used **SMOTE** (Synthetic Minority Over-sampling Technique) to balance the dataset by generating synthetic samples for the minority class.
- Applied **class weights** in models like Logistic Regression and Random Forest to address the imbalance.

---

## Modeling

Two machine learning models were used:
1. **Logistic Regression**: A baseline model to evaluate performance.
2. **Random Forest**: A more complex model with hyperparameter tuning.

### Hyperparameter Tuning
- For the Random Forest model, **Grid Search** was used to optimize the following parameters:
  - `n_estimators`: Number of trees.
  - `max_depth`: Maximum depth of the trees.
- The optimal parameters were found to be close to the default settings, with little performance improvement after tuning.

---

## Model Evaluation

The models were evaluated using various metrics:

### Logistic Regression
- **Before SMOTE**:
  - Accuracy: 85.9%
  - Recall (Churn): 6% (poor at identifying churners)
  - ROC-AUC: 0.6997 (moderate)
- **After SMOTE**:
  - Accuracy: 85.7% (slightly decreased)
  - Recall (Churn): 17% (improved but still low)
  - ROC-AUC: 0.6303 (decreased due to noise introduced by SMOTE)

### Random Forest
- **Before Hyperparameter Tuning**:
  - Accuracy: 90%
  - Recall (Churn): 33% (significantly better than Logistic Regression)
  - ROC-AUC: 0.901 (excellent performance)
- **After Hyperparameter Tuning**:
  - Metrics remained largely the same, indicating near-optimal default parameters.

### Visualization
- Confusion matrices and ROC curves were plotted to better understand each model's performance.

---

## Conclusion
The churn prediction project successfully identified the **Random Forest** model as the optimal choice for predicting customer churn at Syriatel. By deploying this model, Syriatel gains the ability to:
- Proactively identify at-risk customers.
- Implement targeted retention strategies to reduce churn.
- Enhance customer satisfaction and loyalty, improving overall profitability.

---

## Recommendations
1. Focus on at-risk customers identified by the Random Forest model.
2. Implement personalized retention strategies, such as loyalty rewards, offers, and better customer service, to retain high-risk customers.
3. Regularly update the model with fresh data to maintain predictive accuracy over time.
4. Monitor key metrics (e.g., churn rates, customer satisfaction) to evaluate the impact of retention strategies.

