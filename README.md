# Group8_Final Project: Investing in Residential Properties in New York City

## Presentation

Included

## Communication Protocols

The team has agreed to the following: 
- Slack shall be used for exchanging updates, checking on team members, and planning team meetings.
- GoogleMeets will be used for team meetings.
  - Tuesday & Thursday will be our working meeting during class hours which will be used for brainstorming and dividing responsibilities related to project deliverables.
  - Saturday will be our standing team meeting at 12 PM ET for 1 hour. The objective of this meeting is to align on the work done by individual team members and decide on final deliverables. Meeting will be extended as required.
  - Sunday meeting will be called for as required to confirm final deliverables and which documents/code will be pushed to GitHub for final submission.
Create Branch

## Database Integration

### Database Storage & Integration:

- Database was found on **Kaggle** for [NYC Sales Prices](https://www.kaggle.com/johnshuford/new-york-city-property-sales) for 5 different boroughs for the last 15 years (2003-2018).

- Database was uploaded to **AWS** using **RDS & S3**.

- Tables were created for each borough in **PgAdmin**.

  ![image](https://user-images.githubusercontent.com/84694664/142786450-8155dbf6-7bf0-4c7c-a9a0-1411bc729a98.png)

- **AWS** was connected to **PgAdmin**.

- Data was read from **AWS** into **PgAdmin** tables using **SQLAlchemy** in **CoLab**. 

![image](https://user-images.githubusercontent.com/84694664/142786494-070bec8d-d7c5-4bec-82b8-1010a45878bd.png)

- Data was cleaned as discussed below in _Database Cleaning_ section.

- 2 new tables called _"Sales"_ & _"Address"_ were created in **PgAdmin**

- The cleaned data was pushed into the 2 new tables in **PgAdmin**
![image](https://user-images.githubusercontent.com/84694664/142786759-28f092b7-f095-4236-8063-6f4b7456c556.png)

- The cleaned data in the 2 new tables were joined to create a new table Sales_join_Address
 ![image](https://user-images.githubusercontent.com/84694664/142786855-89a0ff5b-44ac-403b-81d0-42ec8469df3b.png)

### Database Cleaning: 

### A. Selected columns

**Original columns:**
  * Borough, Neighborhood, Building Class Category, Tax Class As Of Final Roll 18/1, Block, Lot, Ease-Ment, Building Class As Of Final Roll 18/1, Address, Apartment Number, Zip Code, Residential Units, Commercial Units, Total Units, Land Square Feet, Gross Square Feet, Year Built, Tax Class At Time of Sale, Building Class At Time Of Sale, Sale Price, Sale Date

**Retained columns:**
  * Borough, Neighborhood, Building Class Category, Address, Zip Code, Gross Square Feet, Sale_Price, Sale_Date
 
**Added columns:**
   * $sqf, Year, Month

### B. Filtering for residential units
  * Identified residential Building Class Categories and filtered commercial rows based on category
  * Attempted to use Residential Units column to filter out rows with < 0 residential units; this column did not exclude non-Residential units effectviely and was dropped
 
### C. Filtering incomplete values
   * Dropped rows where square feet or price were 0

### D. Price Filtering 
  * Although $0 properties were dropped, it was still necessary to identify price outliers which were very low or high for reasons irrelevant to our analysis (i.e. deed transfers, features not available in our dataset i.e. lakefront, renovations)
  * $sqf column was created to compare prices per property; since prices increased over the years and by Borough, quantiles were calculated by Borough and Year; top and bottom 5% were dropped for each group

### E. Pre and Post Price Processing Summary 
Quantiles were not significantly effected by the removal of the top and bottom 5th percentiles; Mean decreased, Standard Deviation decreased significantly. 

![Pre-processing summary](https://github.com/VershaR1791/Group8_Project/blob/8fa30e0728e57e3f200255e60bfe09b5543f3bff/post_processing_$.png)

![Post-Processing summary](https://github.com/VershaR1791/Group8_Project/blob/8fa30e0728e57e3f200255e60bfe09b5543f3bff/post_processing_$.png)

### F. Primary Key
![ERD](https://user-images.githubusercontent.com/84694664/142769288-2ba8d7ae-6b1d-48f4-923e-b94794e682a5.png)

  * Attempted to use address and apartment number as composite primary key (addresses were duplicated often for multi-unit buildings); Populated apartment number columns were insufficient to uniquely identify duplicated addresses
  * Numeric index column was created instead to be primary key

### G. Final Tables
  * Table was placed in two tables with common index: 
     *  Address (columns: Address, Building Class Category, Borough, Neighborhood, Zip Code)
     *  Sale (columns: Gross Square Feet, Sale Price, Sale Date, Year, Month)

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
