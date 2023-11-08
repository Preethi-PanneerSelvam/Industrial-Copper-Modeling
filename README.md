# Industrial Copper Modeling Readme

## Problem Statement
The copper industry faces challenges related to sales and pricing data, which can be less complex but suffer from issues like skewness and noisy data. Dealing with these challenges manually is time-consuming and may not lead to optimal pricing decisions. Additionally, capturing leads and classifying them into potential customers is another challenge for the industry. In this context, we aim to build machine learning models to address these issues.

1. **Regression Model**: For optimizing pricing decisions.
2. **Classification Model**: To evaluate and classify leads based on their likelihood of becoming customers.

The STATUS variable is used to distinguish between success (WON) and failure (LOST) and any other data points are removed.

## Approach

### 1) Data Understanding
- Identify variable types (continuous, categorical) and their distributions.
- Convert 'Material_Reference' values starting with '00000' to null.
- Treat reference columns as categorical variables.
- The 'INDEX' variable may not be useful.

### 2) Data Preprocessing
- Handle missing values with mean/median/mode.
- Treat outliers using IQR or Isolation Forest from the sklearn library.
- Identify skewness in the dataset and apply appropriate data transformations (e.g., log transformation for the target variable, boxcox transformation, etc.) to handle high skewness in continuous variables.
- Encode categorical variables using suitable techniques (one-hot encoding, label encoding, ordinal encoding) based on their nature and relationship with the target variable.

### 3) EDA (Exploratory Data Analysis)
- Visualize outliers and skewness (before and after treatment) using Seaborn's boxplot, distplot, and violinplot.

### 4) Feature Engineering
- Engineer new features if applicable, aggregating or transforming existing features to create more informative representations of the data.
- Drop highly correlated columns using a heatmap.

### 5) Model Building and Evaluation
- Split the dataset into training and testing/validation sets.
- Train and evaluate different classification models (e.g., ExtraTreesClassifier, XGBClassifier, Logistic Regression) using appropriate evaluation metrics such as accuracy, precision, recall, F1 score, and the AUC curve.
- Optimize model hyperparameters using techniques like cross-validation and grid search.
- Interpret the model results and assess its performance based on the defined problem statement.
- Repeat the same steps for the regression model.

### 6) Model GUI
- Utilize the Streamlit module to create an interactive page with the following features:
   - Task input (Regression or Classification).
   - An input field for entering each column value except 'Selling_Price' for regression models and except 'Status' for classification models.
   - Perform the same feature engineering, scaling, transformation steps used for training the ML model and predict the new data from Streamlit, displaying the output.

### 7) Tips
- Use the pickle module to dump and load models (e.g., encoder - one-hot/label/str.cat.codes, scaling models - standard scaler, ML models).
- First, fit and then transform in separate lines, and use transform only for unseen data.

This readme provides an overview of the approach and steps taken in the Industrial Copper Modeling project to address challenges in the copper industry related to sales, pricing, and lead classification. The project involves data preprocessing, feature engineering, model building, and the creation of an interactive Streamlit-based GUI for making predictions.
