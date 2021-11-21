# Group8_Project

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

## Machine Learning Overview
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

## Database Integration
### Data Cleaning 

#### Selected columns

**Original columns: **
  * Borough, Neighborhood, Building Class Category, Tax Class As Of Final Roll 18/1, Block, Lot, Ease-Ment, Building            Class As Of Final Roll 18/1, Address, Apartment Number, Zip Code, Residential Units, Commercial Units, Total Units, Land Square Feet, Gross Square Feet, Year Built, Tax Class At Time of Sale, Building Class At Time Of Sale, Sale Price, Sale Date

**Retained columns: **
  *  Borough, Neighborhood, Building Class Category, Address, Zip Code, Gross Square Feet, Sale_Price, Sale_Date
 
**Added columns:**
   * $sqf, Year, Month

#### Filtering for residential units
  * Identified residential Building Class Categories and filtered commercial rows based on category
  * Attempted to use Residential Units column to filter out rows with < 0 residential units; this column did not exclude non-Residential units effectviely and was dropped
 
#### Filtering incomplete values
   * Dropped rows where square feet or price were 0

#### Price Filtering 
  * Although $0 properties were dropped, it was still necessary to identify price outliers which were very low or high for reasons irrelevant to out analysis (i.e. deed transfers, features not available in our dataset i.e. lakefront, renovations)
  * $sqf column was created to compare prices per property; since prices increased over the years and by Borough, quantiles were calculated by Borough and Year; top and bottom 5% were dropped for each group

#### Pre and Post Price Processing Summary 
Quartiles were not significantly effected by the removal of the top and bottom 5th percentiles; means decreased, standard deviation decreased significantly. 

![Pre-processing summary](https://github.com/VershaR1791/Group8_Project/blob/8fa30e0728e57e3f200255e60bfe09b5543f3bff/post_processing_$.png)

![Post-Processing summary](https://github.com/VershaR1791/Group8_Project/blob/8fa30e0728e57e3f200255e60bfe09b5543f3bff/post_processing_$.png)

#### Primary Key
![ERD](https://user-images.githubusercontent.com/84694664/142769288-2ba8d7ae-6b1d-48f4-923e-b94794e682a5.png)

  * Attempted to use address and apartment number as composite primary key (addresses were duplicated often for multi-unit buildings); Populated apartment number columns were insufficient to uniquely identify duplicated addresses
  * numeric index column was created instead

#### Final Tables
  * Table was placed in two tables with common index: 
     *  Address (columns: Address, Building Class Category, Borough, Neighborhood, Zip Code)
     *  Sale (columns: Gross Square Feet, Sale Price, Sale Date, Year, Month)

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
