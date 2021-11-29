# Group8_Project_Final Project: Investing in Residential Properties in New York City

## Dashboard
The final dashboard will be a website created through **JavaScript**. The website will have 2 sections.

**Section 1** will be user self serve information that will include:

- Sales price trends in different NYC boroughs visualized through simple line graphs built in **Tableau**.
- Sales price trends in different building types visualized through trend lines built in **Tableau**.
- A NYC map will be built using **JavaScript** and **GoogleMaps API**. Using **d3.JSON** the map will include Markers to indicate:
  - Sales Price
  - Neighborhood
  - Address
  - Property Type
  - Zip Code
  - Square Feet
- The map will be interactive that will display information such as _"Sales Price", "Address", "Zip Code"_ & _"Property Type"_ while hovering over the Marker 

![Slide1](https://user-images.githubusercontent.com/84694664/142731205-b9d670c2-44ae-4220-87de-bc9e5303cb17.PNG)

**Section 2** will be the interactve section where users will provide inputs of:
- Square Feet
- Budget Range
- Borough (Optional)
through a dropdown menu option built using **JavaScript**.

The output will provide:  
- top 3 choices to the user of properties(address) that they could invest in, 
- the 3 addresses will also be displayed on a map built through **JavaScript** & **GoogleMaps API** and 
- a **Machine Learning** output which displays how the sales price of the 3 properties provided through the output will grow through the next 5 years.

![Slide2](https://user-images.githubusercontent.com/84694664/142731218-c7283fbd-29c0-4872-998d-228e651ae668.PNG)

## Map visualization
- The map was built using **JavaScript** and **GeoMaps API**. 
- The Sale_join_Address database was filtered using **Python (CoLab)** to only incude **0.04%** of database. Including 400K+ data would make the map on JavaScript difficult to visualize and load.
- API call was made to pull in **Latitude** and **Longitude** for each line of address.
![image](https://user-images.githubusercontent.com/84694664/143798666-35c94236-4d6e-4019-b737-e9fb9218b501.png)

- The dataframe was then converted to **.json** format.
![image](https://user-images.githubusercontent.com/84694664/143798767-74a812d6-9157-449e-a975-2082f16a614e.png)

- The visualization has an interactive element where we can switch between _'Street', 'Satellite'_ and _'Dark'_ view
![image](https://user-images.githubusercontent.com/84694664/143799120-83949522-2e0a-49d2-a6db-081e575c00d4.png)

- The markers provide details of _Address, Neighborhood, Property type, Sales Price_ and _Gross Square feet_.
![image](https://user-images.githubusercontent.com/84694664/143798318-8bf42e9f-c969-4b75-aa3a-181436137baa.png)

