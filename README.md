# Group8_Project

## Segment 1 Deliverables: 
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
![image](https://user-images.githubusercontent.com/84694664/140664353-96ad9934-abb5-4d54-a8d2-6700ea56f954.png)

The ERD does not show any primary keys because none of the values are completely unique to each item (addresses can be shared between multiple apartments since they do not include apartment numbers). Foreign key relationships are also excluded since values do not correspond to other tables.
