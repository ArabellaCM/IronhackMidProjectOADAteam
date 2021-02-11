# IronhackMidProject

This repository contains the group project by the OADA team for the Ironhack Mid-Bootcamp Project. Our objective was to understand the demographics and other characteristics of the bank's customers comparing those who accept a credit card offer and those who do not.

# Team
BootCamp : Ironhack Berlin Data Analytics Full-Time January Cohort /
Alice
Arabella 
Dina
Oliver
<br/>
# Code and Resources Used
- Python Version: 3.7 <br/>
- Packages: pandas, numpy, sklearn, matplotlib, seaborn <br/>

# Data Cleaning
The dataset was checked for duplicates.<br/>
The identifier field (Customer Number) was dropped.<br/>
The data columns were checked for null values. Null values were present in the numerical features and these were replaced with the median. <br/>
The data type of each column was checked. <br/>
The unique values and distribution of each categorical feature were checked - some subcategories are very underrepresented (e.g. Household Size) so they will be aggregated.<br/>
The distributions of each numerical variable were checked. The data fields Credit Cards Held, Homes Owned, Household Size, Bank Accounts Open   were of numeric data type but are in fact categoricals so they will be treated as categories in our analysis.<br/>
Boxplots were generated for numeric variables, it was clear that the data includes outliers that will be dealt with later.<br/>
Data columns were renamed and stylized as snake_case.<br/>


# EDA
We looked at:
Multicollinearity Matrix <br/>
VIF scores (the Quarters values were in a range of 476 - 871 <br/>
Generated 3 new columns to look for max, min, and range of quarterly values <br/>
Final columns: Average, Max, Min, Range <br/>
Chi-Squared on Max and Min (p=0.0)<br/> <br/>
Applied Log transformation to the 2 Numerical columns <br/>
Possible problem with them being binomial distributions? <br/>
Checked for multicollinearity between the categorical variables. <br/>
We run the chi2 test on each combination of 2 categorical variables. <br/>

# Transformation
Removing outliers: <br/>
 Using IQR limit setting <br/>
 + 1.5 for average_balance and min <br/>
 +1 for q3 <br/>
 Boxplots to check distributions <br/>

Transformation:Square Root transformation for ‘min’ and q3_balance <br/>
Encoding: OneHot Encoder <br/>
Scaling: Normalization <br/>
 
# Model Building
First, we transformed the data and split the data into train and test sets with a test size of 30%.
We tried three different models and evaluated them based on the recall value.
- Logistic Regression – Our final Model.
- Random Forest Classifier – Considering the imbalanced dataset, we would have expected this model to be the best, which was not true.
- KNN – We tested this model also assuming that it could handle the data imbalance.

# Model performance
The Logistic Regression model outperformed the other approaches on the test and validation sets. We considered the recall value to decide:
- Logistic Regression : Recall  = 0.7
- Random Forest Classifier: Recall = 0.3
- KNN: Recall = 0.31

# Visualization
- Tableau
