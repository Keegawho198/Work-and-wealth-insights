# Work & Wealth 
Authored by: Keegan, Natasha, Lishi & Mike
----------

This project is a machine learning project aiming to train a model able to adequately predict an association (with >75% accuracy or R2 > 0.8) based on publically available data.
We were keen to evaluate the labour market and the impact of employment upon discretionary expenditure.

Datasets:
Obtained from the Australian Bureau of Statistics are:
1. Labour Force - https://www.abs.gov.au/statistics/labour/employment-and-unemployment/labour-force-australia/latest-release#data-downloads
2. Lending Indicators - https://www.abs.gov.au/statistics/economy/finance/lending-indicators/latest-release#data-downloads
3. Monthly Household Spending Indicators - https://www.abs.gov.au/statistics/economy/finance/monthly-household-spending-indicator/latest-release#data-downloads

Both datasets are available under the Creative Commons Attribution Internation Licence 4.0, whereby the ABS is the original creator of this data and does not endorse this project.

----------
Question to answer:
----------

Can a machine learning model predict the total amount of committed travel loans based upon economic indicators?
Total travel loans committed as a surrogate for spending on non-essential items / discretionary expenditure.

Data Handling/ETL:
Data tables were cleaned, merged and checked for duplicates and null values.
Outliers were estimated and removed from the data set.
Data required normalisation and standarisation prior to development of the model

Dates from 01-2014 -> 09-2024 (limit of data from Travel Loans)

Model Features from the original data sets:
1. Employed Males (Full Time)
2. Employed Females (Full Time)
3. Employment-To-Population Ratio (Males)
4. Employment-To-Population Ratio (Females)
5. Food Spend (Household)
6. Clothing & Footwear Spend (Total)
7. Month
8. Year

![Fig1_data_histogram](https://github.com/user-attachments/assets/6cd8bca8-f6d0-4d32-abb8-55da9e9fcef9)
Fig.1. Detailing the data spread and distribution of values

![Fig2_correlation_matrix](https://github.com/user-attachments/assets/3a968985-ca3a-44a5-b905-b03542d74a66)
Fig.2. Correlation matrix, after which we removed poorly correlated data - Employed Males (Full Time), Month and Year

-----------
Model choice:
-----------
We are aware of the limitations of our data, namely small sized dataset with multiple variables that may not have linear relationships.

As such we opted to test / develop one of the following models:
1. Random Forest Regressor
2. Gradient Boosted Model
3. SVR

-----------
Random Forest Regressor Trees:
-----------

![Fig5_Decision Tree for Random Forest Regressor (1)](https://github.com/user-attachments/assets/0fa32c1b-68ae-4622-8da9-ad8f1a272045)
Fig.3. Random Forest Regressor Model Tree

We initially chose a random forest regressor model, which had a R² Score on Test Data: 0.7320.

Given this was suboptimal, we opted to attempt hyperparameter tuning.
The best hyperparameter settings were: bootstrap: True, max_depth: None, max_features: log2, min_samples_leaf: 1, min_samples_split: 2, n_estimators: 1942
R² Score on Test Data: 0.7634 which was a modest improvement on the previous model. However on cross-valiation the R2 score was 0.8382

------------
Feature Importance of Random Forest Regressor:
------------

![Fig3_feature importance](https://github.com/user-attachments/assets/13b26dda-eaad-4648-96f6-120fc1c1a970)
Fig.4. Feature Importance of Random Forest Regressor Model
Key Features in this model focused on employment data - Female Employed (Full Time), Employment-To-Population Ratio (Males), and Employment-to-Population Ratio (Females). Interestingly, clothing and footwear expenditure proved to be of lower significance. 

------------
Learning Curves:
------------

![Fig4_Learning Curve](https://github.com/user-attachments/assets/e4700d12-c919-49fe-b9a4-a4ec997a2a3a)
Fig.5. Learning curve based on training size.
Learning curve indicates significant improvement with training size. 

------------
SVR & GBR Models (with hyperparameter tuning):
------------
Although our inital model proved to have reasonable performance, we pursued other models to see if we could improve on our results.
Our SVR model used the following parameters: {'C': 100, 'degree': 2, 'epsilon': 1.0, 'gamma': 'scale', 'kernel': 'rbf'}
SVR test R² Score: 0.6630911256666858

Our GBR model using the following hyperparamters: {'learning_rate': 0.09687887310208573, 'max_depth': 3, 'min_samples_leaf': 2, 'min_samples_split': 2, 'n_estimators': 500, 'subsample': 0.93378481193262}
R² Score on Test Data: 0.8193
Best R² Score from RandomizedSearchCV: 0.2895

The SVR model did not perform well on our testing data compared to our Random Forest Regressor, so we chose not to use it further.
Our GBR initially proved promising, however it performed very poorly on further testing.

-----------
Findings
-----------

Random Forest Regressor Model proved to be the best
Strong correlation with economic datapoints, less so with spending (interestingly)
Strongest predictor was Female Employment (Full Time)

-----------
Limitations
-----------

Data set is small, limited definition of discretionary expenditure and the model has large variability / error.
Further modelling could consider time-based analysis (but this is tricky with the current data)
We could expand the definition of employment data (use seek job adverts etc)
Could expand definition of discretionary spend to include expenditure of all non essential goods and services.

-----------
Libraries and Dependencies:
-----------
Data Processing: Pandas/Numpy, SQL

Modelling: sklearn, scipy

Visualisations: Pandas, matplotlib, graphviz

----------
Thank You
