# Group8_Project

### Presentation

Included

### Communication Protocols

The team has agreed to the following: 
- Slack shall be used for exchanging updates, checking on team members, and planning team meetings.
- GoogleMeets will be used for team meetings.
  - Tuesday & Thursday will be our working meeting during class hours which will be used for brainstorming and dividing responsibilities related to project deliverables.
  - Saturday will be our standing team meeting at 12 PM ET for 1 hour. The objective of this meeting is to align on the work done by individual team members and decide on final deliverables. Meeting will be extended as required.
  - Sunday meeting will be called for as required to confirm final deliverables and which documents/code will be pushed to GitHub for final submission.
Create Branch

### Machine Learning Overview
As the desired output of our machine learning model is a predication of the percentage increase in property value we will be looking at the following data:

- 10 years of property sales data by borough in NYC for the training set, additional 5 years of property sales will be used to test our model
- Input features from our database will be the following:
  - Building Class Category
  - Neighborhood
  - Address
  - Zip Code
  - Gross Square Feet
  - Sale Price
  - Year
  - Sales Date
  - Residential
- The target output will be "Sale Price". As the target output is continuous data we will be using a supervised machine learning model and testing with both linear and multiple linear regression models.

![image](https://user-images.githubusercontent.com/84694664/140664113-e60db76c-3df3-4227-afb8-2e85d5b0a612.png)

### Database
# Data Cleaning 

## Selected columns

Original columns: 

  * Borough, Neighborhood, Building Class Category, Tax Class As Of Final Roll 18/1, Block, Lot, Ease-Ment, Building            Class As Of Final Roll 18/1, Address, Apartment Number, Zip Code, Residential Units, Commercial Units, Total Units, Land Square Feet, Gross Square Feet, Year Built, Tax Class At Time of Sale, Building Class At Time Of Sale, Sale Price, Sale Date

Retained columns: 

  *  Borough, Neighborhood, Building Class Category, Address, Zip Code, Gross Square Feet, Sale_Price, Sale_Date
 
 Added columns:
 
  * $sqf, Year, Month

## Filtering for residential units

  * Identified residential Building Class Categories and filtered commercial rows based on category
  * Attempted to use Residential Units column to filter out rows with < 0 residential units; this column did not exclude non-Residential units effectviely and was dropped
 
 ## Filtering incomplete values
 
  * Dropped rows where square feet or price were 0

## Price Filtering 

  * Although $0 properties were dropped, it was still necessary to identify price outliers which were very low or high for reasons irrelevant to out analysis (i.e. deed transfers, features not available in our dataset i.e. lakefront, renovations)
  * $sqf column was created to compare prices per property; since prices increased over the years and by Borough, quantiles were calculated by Borough and Year; top and bottom 5% were dropped for each group

### Pre and Post Price Processing Summary 

Quartiles were not significantly effected by the removal of the top and bottom 5th percentiles; means decreased, standard deviation decreased significantly. 

![Pre-processing summary](https://github.com/VershaR1791/Group8_Project/blob/8fa30e0728e57e3f200255e60bfe09b5543f3bff/post_processing_$.png)

![Post-Processing summary](https://github.com/VershaR1791/Group8_Project/blob/8fa30e0728e57e3f200255e60bfe09b5543f3bff/post_processing_$.png)

## Primary Key

  * Attempted to use address and apartment number as composite primary key (addresses were duplicated often for multi-unit buildings); Populated apartment number columns were insufficient to uniquely identify duplicated addresses
  * numeric index column was created instead

## Final Tables

  * Table was placed in two tables with common index: 
     *  Address (columns: Address, Building Class Category, Borough, Neighborhood, Zip Code)
     *  Sale (columns: Gross Square Feet, Sale Price, Sale Date, Year, Month)
