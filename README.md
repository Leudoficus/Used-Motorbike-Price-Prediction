# Used-Motorbike-Price-Prediction
In this portfolio I try to predict used price of motorbike using Used Price Honda 2016 dataset. This dataset denote list of stock unit from NPL (Non-Perfomed Loan) customer which has been acquired by the finance company. In short, finally these units will be distribute in the next day to reduce company loss.
Therefore, I try to predict the used price using Linier regression method as a baseline model. Furthermore using several others method as a Lasso, Ridge, Decision Tree Regressor, Random Forest Regressor, Gradient Boosting Regressor, K-Neighbors Regressor. And in the end obtain the best model using Gradient Boosting Regressor method to predict used price of motorbike.

## **Exploratory Data Analisys**
I analyze there are several important point before the modelling. among others are :
1. feature CATEGORY, BRAND MODEL TYPE, MODEL, TYPE, CODE ENGINE turned out to have been represented by **GROUP MODEL TYPE**, so that in the next part these features  CATEGORY, BRAND MODEL TYPE, MODEL, TYPE, CODE ENGINE will be drop.
2. **DOCUMENT** with **STNK Y** have higher average SOLD PRICE than STNK N even though the different is not significant. even in CONDITION GRADE A,B,C,D.
3. In **CONDITION GRADE 'D'** in year 2011-2013 there is no significant different on **SOLD PRICE**. And in the age of vehicle in fifth & sixth years old (year 2010-2011), the different of **SOLD PRICE** between **CONDITION GRADE 'C' & 'D'** is not significant also. most likely because of the high damage rate. So that the buyer does not take into account the market price, but it takes more into account the price of spare parts, and the high cost of repair services.
4. otherwise for the age less than 1 year old (year 2016), the **CONDITION GRADE** does not affect the **SOLD PRICE** unless unit with very bad condition (CONDITION GRADE 'D').
5. On the scatterplot I made, **CONDITION GRADE 'A'** have a characteristic lower **LOST PART** than a Grade B furthermore grade C and D, besides that it also has a higher **SOLD PRICE** compared with condition grade B next C and D.
6. feature **MARKET PRICE, NEW PRICE, SOLD PRICE MINIMUM** have the similar characteristic to the **SOLD PRICE**. Linierly, the higher MARKET PRICE, NEW PRICE, SOLD PRICE MINIMUM affect to the higher SOLD PRICE formed in accordance with the grade A tend to be in higher SOLD PRICE, then condition grade B tend to be lower than condition grade B and so on in condition grade C & D.

## Summary
### 1. Insight :
Based on analysis model,
- feature **NEW PRICE** become the most impact feature to predict **SOLD PRICE**.
- feature **YEAR** become the sceond most impact feature to predict **SOLD PRICE**.
- feature **LOST PART, GROUP MODEL TYPE, CONDITION GRADE** still affect features to predict **SOLD PRICE** but it not too significant if compared with NEW PRICE and YEAR.
- at the same time feature **DOCUMENT** have very small impact to predict feature **SOLD PRICE**.
- the result of tuning hyperparameter with **Gradient Boosting Regressor** model have the result of **Mean Average Error** in the ammount of **709166.0635159286**. which means there are margin error as big as +- 709.166,06 point to the prediction result.
- while **R2 Score** value as big as **0.9159404231650905** which means SOLD PRICE predict using Gradient Boosting Regressor model can be predicted with accuracy up to 91,59%.

### 2 Recomendations :
- to predict **SOLD PRICE** of used motorbike, stakeholders must pay attention and must have a **New Price** reference from the model and type of motorbike for sale.
- after that, production year (**YEAR**) become the second parameters what to pay attention to when predicting **SOLD PRICE** of used motorbike.
- whereas the **CONDITION GRADE** and **model type** of motorbike only a supporting factors to predict **SOLD PRICE**.
