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
Multicollinearity Matrix 
After running the multicollinearity checks (heat map, VIF) it was clear that the numerical features were very related to each other (VIF value > 20). <br/>
Feature extraction was done. The following features were extracted: <br/>
- “max_quarter”, “min_quarter” (the quarters with the highest and lowest balances). Reasoning : To see if there was any seasonality<br/>
-  “max”, “min” (the highest and lowest balances)<br/>
Reasoning: To see if a lower or higher balance affected the likelihood of the offer being accepted<br/>
-  “range” (the difference between max and min balances)<br/>
Reasoning:  To see if a larger variability throughout the year affected the likelihood of the offer being accepted<br/>
The multicollinearity was checked again with the new features and there was a high correlation between “max” and “average_balance” and “max” and “range” so “max” was dropped.<br/>
“q1_balance”, “q2_balance” and “q4_balance” were also dropped. “q3_balance” was kept as it was more related to the target.<br/>
Performed Chi-Squared on Categoricals. <br/>



# Transformation
Removing outliers: <br/>
 Using IQR threshold setting <br/>
 + 1.5 for min <br/>
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
