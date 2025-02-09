# project_4
Authored by: Keegan, Natasha, Lishi & Mike
----------

This project is a machine learning project aiming to train a model able to adequately predict an association (with >75% accuracy) based on publically available data.
We were keen to evaluate the labour market and the impact of employment upon discretionary expenditure.

Datasets:
Obtained from the Australian Bureau of Statistics are:
1. Labour Force - https://www.abs.gov.au/statistics/labour/employment-and-unemployment/labour-force-australia/latest-release#data-downloads
2. Lending Indicators - https://www.abs.gov.au/statistics/economy/finance/lending-indicators/latest-release#data-downloads

Both datasets are available under the Creative Commons Attribution Internation Licence 4.0, whereby the ABS is the original creator of this data and does not endorse this project.

----------
Question to answer:
----------

Can a machine learning model predict the total amount of committed travel loans based upon economic indicators?
Total travel loans committed as a surrogate for spending on non-essential items / discretionary expenditure.

Data Handling/ETL:
Data tables were cleaned, merged and checked for duplicates and null values. nil existed
Data required normalisation and standarisation prior to development of the model

Dates from 01-2015 -> 09-2024 (limit of data from Travel Loans)

Model Features from the data sets:
1. Employed Males (Full Time)
2. Employed Females (Full Time)
3. Employment-To-Population Ratio (Males)
4. Employment-To-Population Ratio (Females)
5. Food Spend (Household)
6. Clothing & Footwear Spend (Total)

Model choice:
As Month as a categorical variable, and opted to choose Random Forest Regressor Modelling with hyperparameter tuning.
We later encoded this variable, but did not pursue a linear regression approach (linear regression not suitable for string/categorical variables).

-----------
Random Forest Regressor Trees:
-----------
![image](https://github.com/user-attachments/assets/3dd20c19-a29a-41b8-872f-e221082a7e2b)
![image](https://github.com/user-attachments/assets/25d12403-7b81-4616-a0e7-3225f81f04a2)
![image](https://github.com/user-attachments/assets/0a792bf1-d7f0-4b22-b129-ae4f4fe4cea7)

Metrics:
R² Score	0.794	
MAE (Mean Absolute Error)	5.96
MSE (Mean Squared Error)	60.04	
RMSE (Root Mean Squared Error)	7.75	
MAPE (Mean Absolute Percentage Error)	39.14%	

The model has a reasonable R2 score. However, it is clear there is a large error margin, and therefore it is not yet optimised.
As such, further hyperparameter tuning was performed to see if this improves on the metrics.

Post Hyperparameter tuning results:
![image](https://github.com/user-attachments/assets/c783e3bf-f100-4f92-89bb-30af825817a8)
![image](https://github.com/user-attachments/assets/0143956e-8ac7-4996-96c1-6f8ba6993ce1)

![image](https://github.com/user-attachments/assets/8150eca0-f1d0-4a10-b5be-2e5711cabd0e)

Post hyperparameter tuning there are minor improvements in the model across all metrics indicating better predictive power.

-----------
Here is a supertree visualisation of the model:
*** need to upload SVG in a working way ***
------------
Feature Importance:
------------

![image](https://github.com/user-attachments/assets/7b518118-d2c6-4140-9d84-1eacc95f61a0)

You can see key features in this model focus on Full Time Employment for females, Employment-to-population ratio for males, Full-time Employment for males and Food expenditure. 
-----------
Libraries and Dependencies:
-----------
Data Processing: Pandas/Numpy

Modelling:
sklearn, scipy

Visualisations: Pandas, matplotlib, graphviz, supertree

----------
Thank You
