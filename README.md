# Used-Motorbike-Price-Prediction
I predicted the price of used motorbikes using the Used Honda 2016 Price dataset from one of financial company in Indonesia. This dataset listed the stock units from NPL (Non-Performed Loan) customers which had been acquired by the finance company. 

This stock unit is a loss to the company, they need to distribute them to reduce company losses. 

To help the company set the price for the distribution, I predicted the price using the dataset mentioned above. 

I predicted the price with the Linear regression method as a baseline model. This model is a standard model to make predictions. 

I reviewed several other methods as a comparison such as Lasso, Ridge, Decision Tree Regressor, Random Forest Regressor, Gradient Boosting Regressor, and K-Neighbors Regressor. 

## **Process Outline**
To predict the price of used motorbikes, I did several process step-by-step such as Data Understanding, Data Cleaning & Preprocessing, Exploratory Data Analysis, Feature Engineering, Modelling, Tuning Hyperparameter, Insight & Recommendation.

## **Data Understanding**
This dataset consist of 3204 rows and 15 columns with two type of data : categorical & numerical. So that I grouped it into 2 kind of data : categorical data & numerical data. 

Categorical data consist of 9 columns : BRAND MODEL TYPE, CATEGORY, GROUP MODEL TYPE, MODEL, TYPE, DOCUMENT, CHASIS NUMBER, CODE ENGINE, CONDITION GRADE.
Numerical data consist of 6 columns : YEAR, LOST PART, NEW PRICE, SOLD PRICE MINIMUM, MARKET PRICE, SOLD PRICE.

## **Data Cleaning & Preprocessing**
I did checked Missing Value & Duplicated Rows, but I did'nt get any missing value & duplicated rows in this dataset. 

Next, I continued to check outliers in numerical data. actually, There are many outliers in numerical data. but I seen this outliers is still make sense, so did'nt drop any columns for this process.

But, after understand the data, I decided to drop 7 columns because some features already represented by GROUP MODEL TYPE such as BRAND MODEL TYPE, CATEGORY, MODEL, TYPE, CHASIS NUMBER, CODE ENGINE. 
And feature SOLD PRICE MINIMUM I drop also because I think this feature not to affected to predict sold price of used motorbike.

So that, after droped several features, there only 8 columns behind, that is : GROUP MODEL TYPE, YEAR, DOCUMENT, LOST PART, CONDITION GRADE, NEW PRICE, MARKET PRICE, SOLD PRICE.

## **Exploratory Data Analisys**
I analyzed the data,then I've got several important point in the data :
1. There are none columns with normal distribution in numerical data.
2. Most of the data is in CATEGORY Scooter and Cub. with GROUP MODEL TYPE REVO FI, BEAT FI ALL NEW and BEAT FI.
3. **DOCUMENT** with **STNK Y** have higher average SOLD PRICE than STNK N even though the different is not significant. even in CONDITION GRADE A,B,C,D.
5. In **CONDITION GRADE 'D'** in year 2011-2013 there is no significant different on **SOLD PRICE**. And in the age of vehicle in fifth & sixth years old (year 2010-2011), the different of **SOLD PRICE** between **CONDITION GRADE 'C' & 'D'** is not significant also. most likely because of the high damage rate. So that the buyer does not take into account the market price, but it takes more into account the price of spare parts, and the high cost of repair services.
6. otherwise for the age less than 1 year old (year 2016), the **CONDITION GRADE** does not affect the **SOLD PRICE** unless unit with very bad condition (CONDITION GRADE 'D').
7. On the scatterplot I made, **CONDITION GRADE 'A'** have a characteristic lower **LOST PART** than a Grade B furthermore grade C and D, besides that it also has a higher **SOLD PRICE** compared with condition grade B next C and D.
8. feature **MARKET PRICE, NEW PRICE, SOLD PRICE MINIMUM** have the similar characteristic to the **SOLD PRICE**. Linierly, the higher MARKET PRICE, NEW PRICE, SOLD PRICE MINIMUM affect to the higher SOLD PRICE formed in accordance with the grade A tend to be in higher SOLD PRICE, then condition grade B tend to be lower than condition grade B and so on in condition grade C & D.

## **Feature Engineering**
The data modeling process cannot process categorical data. Therefore I did encoding for categorical data left behind (GROUP MODEL TYPE, DOCUMENT, CONDITION GRADE).

Then, I checked relationship between features to check multicollinierity in this data. I found very high correlation between MARKET PRICE and NEW PRICE (0,92). And based on previous scatterplot in EDA, MARKET PRICE and NEW PRICE have similar character into SOLD PRICE. so that I decided to drop MARKET PRICE because already represented by NEW PRICE.

## **Modelling**
First I defined X (features data) and Y (target data), with target data is SOLD PRICE. Then I split the data into Training set and Validation set with compotition 70-30.

Because of there are several features that have a very high values and there are several features that have a very small values, so that the values are on the same scale, then for the features that have a very high values will be 'scale' using method MinMaxScaler because of abnormal distribution.

To predict the price of used motorbike, I use several modelling method for further choose the best model. And before, I use Linear Regression model as a baseline model.
after run those models, I've got the best of the best model to predict price of used motorbike that is **Gradient Boosting Regressor**.

## Summary
### 1. Insight :
Based on analysis model from Gradient Boosting Regressor, I got an important feature to predict Sold Price :
- feature **NEW PRICE** become the first most impact feature to predict **SOLD PRICE**.
- feature **YEAR** become the second most impact feature to predict **SOLD PRICE**.
- feature **LOST PART, GROUP MODEL TYPE, CONDITION GRADE** still affect features to predict **SOLD PRICE** but it not too significant if compared with NEW PRICE and YEAR.
- at the same time feature **DOCUMENT** have very small impact to predict feature **SOLD PRICE**.
- the result of tuning hyperparameter with **Gradient Boosting Regressor** model have the result of **Mean Average Error** in the ammount of **709166.0635159286**. which means there are margin error as big as +- 709.166,06 point to the prediction result.
- while **R2 Score** value as big as **0.9159404231650905** which means SOLD PRICE predict using Gradient Boosting Regressor model can be predicted with accuracy up to 91,59%.

### 2 Recomendations :
Based on the insight above, this is the recommendation for the stakeholders :
- to predict **SOLD PRICE** of used motorbike, stakeholders must pay attention and must have a **New Price** reference from the model and type of motorbike for sale.
- after that, production year (**YEAR**) become the second parameters what to pay attention to when predicting **SOLD PRICE** of used motorbike.
- whereas the **CONDITION GRADE** and **model type** of motorbike only a supporting factors to predict **SOLD PRICE**.
