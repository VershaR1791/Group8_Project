# Choosing A Machine Learning Model

## Supervised Machine Learning

###
For our project, we want to be able to predict unit selling price for residential properties in New York City.  We have 15 years of sales data for the five boroughs in NYC.  
We will be using the first 80% of sales data to train our model and the subsequent 20% to test our machine learning model.  As supervised learning deals with 
labeled data this will be the primary model we will use.  

We will be using a regression model as the target output are continuous variables (sale price).  The classification model would not be an appropriate choice as it can only be used
to predict discrete outcomes.  Logistic regression would also not be appropriate as its outcomes are binary.  Support Vector Machine (SVM) would also not be able to generate the 
desired output for our project as it too produces a binary output.  

In order to confirm that the linear regression model is most accurate in predicting the target outcome, we testing the following models:

  1) Linear Regression 
  2) Robust Regression 
  3) Ridge Regression 
  4) Lasso Regression 
  5) Elastic Net Regression 
  6) Polynomail Regression 
 
###
Our initial Linear regression model yielded an R2 value of 0.676.  The R2 value increased significantly weh the Polynomial Regression model was used.
This result was expected as sns.pairplot was used to visualize the relationship between various factors and Sale Price.  The visualizations showed that the relationship was
not a straight linear relationship.  

  Model	                           MAE	          MSE	          RMSE	      R2 Square	Cross Validation
1	Linear Regression	           475892.700245	  1.129445e+13	3.360721e+06	0.676345	-0.421112
2	Robust Regression	           406618.850768	  2.097093e+13	4.579403e+06	0.399054	 0.584584
3	Ridge Regression	           475814.956204	  1.129592e+13	3.360941e+06	0.676302	-0.421112
4	Lasso Regression	           482076.172022	  1.131200e+13	3.363332e+06	0.675842	-0.421112
5	Elastic Net Regression       473787.534290	  1.133768e+13	3.367147e+06	0.675106  -0.419317
6	Polynomail Regression	       402190.509575	  8.751292e+12	2.958258e+06	0.749222	 0.000000
7	SGD Regressor                476411.676965	  1.128039e+13	3.358628e+06	0.676748	 0.000000


### Cleaning Data for Model
Most data preprocessing was completed in SQL using PgAdmin including dropping NaN values, removing commercial properties and outliers.  Property sales with a price of under $1,000 
also removed as these are typically transfer of property between related parties and do not represent a true property sale.  

Due to the size of the data, we decided to focus our results on residential units so we dropping commericial units, sales that had no square footage listed and null/NaN values 
as there was still sufficient data to complete our analysis.

Label Encoder and OneHotEncoder were were used to encode "Address", "Building Class Category" and "Neighborhood" in order to use in the machine learning model.

In order to proceed with building our machine learning model we will complete the following steps:
  1. Creating the model:
      To create the model we will be using Scikit-learn linear regression module in Pandas: from sklearn.linear_model import LinearRegression
  2. Train the model:
      We will define the target variable (Sale_Price) and independent variable(s).  We will split the dataset into X and y components, with X being the input data and y the output.
  3. Create the predictions:
      Using y_pred = model.predict(X) we will generate predictions for the y data and plot the best fit line


![image](https://user-images.githubusercontent.com/84694664/142769927-900f46a4-4693-4a58-a449-3d6afe41a8d4.png)

![image](https://user-images.githubusercontent.com/84694664/142787714-dead4c43-f23d-4e7e-a68e-45551e193282.png)

