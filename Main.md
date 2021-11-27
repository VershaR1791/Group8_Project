# Group8_Final Project: Investing in Residential Properties in New York City

## Presentation

[Click Here](https://github.com/VershaR1791/Group8_Project/blob/5f155207961f6af6b981ca64e2ff38a7baa353bd/Project%20Group%208_Segment%202.pptx)

## Communication Protocols

The team has agreed to the following: 
- Slack shall be used for exchanging updates, checking on team members, and planning team meetings.
- GoogleMeets will be used for team meetings.
  - Tuesday & Thursday will be our working meeting during class hours which will be used for brainstorming and dividing responsibilities related to project deliverables.
  - Saturday will be our standing team meeting at 12 PM ET for 1 hour. The objective of this meeting is to align on the work done by individual team members and decide on final deliverables. Meeting will be extended as required.
  - Sunday meeting will be called for as required to confirm final deliverables and which documents/code will be pushed to GitHub for final submission.
Create Branch


## Machine Learning Model

### Choosing A Machine Learning Model

**Supervised Machine Learning**

For our project, we want to be able to predict unit selling price for residential properties in New York City. We have 15 years of sales data for the five boroughs in NYC.  
We will be using the first 10 years of sales data to train our model and the subsequent five years to test our machine learning model. As supervised learning deals with 
labeled data this will be the primary model we will use.  

We will be using a regression model as the target output are continuous variables (sale price). The classification model would not be an appropriate choice as it can only be used to predict discrete outcomes. Logistic regression would also not be appropriate as its outcomes are binary. Support Vector Machine (SVM) would also not be able to generate the desired output for our project as it too produces a binary output.  

![image](https://user-images.githubusercontent.com/84694664/142769927-900f46a4-4693-4a58-a449-3d6afe41a8d4.png)

In order to confirm that the linear regression model is most accurate in predicting the target outcome, we will build a linear regression model, multiple 
linear regression model and a neural network to compare results.  Although we have determined that a Linear Regression model will be most appropriate, our testing will include 
a variety of models in order to confirm our the soundness of our machine learning model.

### Cleaning Data for Model

Most data preprocessing was completed in **SQL using PgAdmin** including dropping NaN values, removing commercial properties and outliers.  Property sales with a price of under $1,000 also were removed as these are typically transfer of property between related parties and do not represent a true property sale.

Label Encoder was used to encode **"Address", "Building Class Category"** and **"Neighborhood"** in order to use in the machine learning model.

### Building ML Model
To confirm which machine learning model provides the greatest degree of predictive accuracy we tested the following models:

- Linear Regression 
- Robust Regression 
- Ridge Regression 
- Lasso Regression 
- Elastic Net Regression 
- Polynomail Regression 
- Stochastic Gradient Descent 
- Artficial Neural Network 
- Random Forest Regressor 
- SVM Regressor

In order to proceed with building our machine learning model we will complete the following steps:
#### Creating the model:
To create the model we will be using **Scikit-learn** linear regression module in **Pandas**: from sklearn.linear_model import LinearRegression
      
#### Train the model:
We will define the target variable (Sale_Price) and independent variable(s).  We will split the dataset into X and y components, with X being the input data and y the output.

#### Create the predictions:
Using y_pred = model.predict(X) we will generate predictions for the y data and plot the best fit line
     
### Accuracy of ML Model
Our initial Linear regression model yielded an R2 value of **0.676**.  The R2 value increased significantly weh the Polynomial Regression model was used.
This result was expected as sns.pairplot was used to visualize the relationship between various factors and Sale Price.  The visualizations showed that the relationship was
not a straight linear relationship.  

![image](https://user-images.githubusercontent.com/84694664/142787714-dead4c43-f23d-4e7e-a68e-45551e193282.png)

We are continuing to test the last four models and results will be added once available, however we do not expect to see a model with a higher R2 score than the Polynomial Regression model.

## Dashboard
The final dashboard will be a website created through **Flask** using different **routes**. The website will have 2 sections.

**Section 1** will be user self serve information that will include:

- Sales price trends in different NYC boroughs visualized through simple line graphs built in **python**.
- Sales price trends in different building types visualized through trend lines built in **python**.
- A NYC map will be built using **JavaScript** and **GoogleMaps API**. Using **d3.JSON** the map will include circleMarkers to indicate sales price which will have
  - a different color based on the sales price range and
  - different radii based on the sales price amount
- The map will be interactive that will display information such as _"Sales Price", "Address", "Postal Code"_ & _"Property Type"_ while hovering over the CircleMarker 

![Slide1](https://user-images.githubusercontent.com/84694664/142731205-b9d670c2-44ae-4220-87de-bc9e5303cb17.PNG)

**Section 2** will be the interactve section where users will provide inputs of:
- Property Type
- Budget Range
- Borough
through a dropdown menu option built using Flask.

The output will provide:  
- top 3 choices to the user of properties(address) that they could invest in, 
- the 3 addresses will also be displayed on a map built through **JavaScript** & **GoogleMaps API** and 
- a **Machine Learning** output which displays how the sales price of the 3 properties provided through the output will grow through the next 5 years.

![Slide2](https://user-images.githubusercontent.com/84694664/142731218-c7283fbd-29c0-4872-998d-228e651ae668.PNG)
