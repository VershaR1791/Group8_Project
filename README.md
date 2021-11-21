# Group8_Project

## Database Creation

- Find the data
- Add data to Pgadmin
- Split the database into bureaus
- Create different tables for different Tables
- Create an AWS, S3 and RDS Account
- Upload the data to AWS
- Connect AWS to Collab
- Clean Data In Collab
- Copy the clean Data from Collab to AWS
- Join Clean Tables (Sales & Address) into a new one (Sales_join_Address)

# Data Description

## Context

This dataset contains every property sale from 2003 - 2019 in every borough in New York City.

## Columns

- Borough: The name of the borough in which the property is located.
- Neighborhood: Department of Finance assessors determine the neighborhood name in the course of valuing properties. The common name of the neighborhood is generally the same as the name Finance designates. However, there may be slight differences in neighborhood boundary lines and some sub-neighborhoods may not be included.
- Building Class Category: This is a field that we are including so that users of the Rolling Sales Files can easily identify similar properties by broad usage (e.g. One Family Homes) without looking up individual Building Classes. Files are sorted by Borough, Neighborhood, Building Class Category, Block and Lot.
- Tax Class at Present: Every property in the city is assigned to one of four tax classes (Classes 1, 2, 3, and 4), based on the use of the property.
  Class 1: Includes most residential property of up to three units (such as one-, two-, and three-family homes and small stores or offices with one or two attached apartments), vacant land that is zoned for residential use, and most condominiums that are not more than three stories.
  Class 2: Includes all other property that is primarily residential, such as cooperatives and condominiums.
  Class 3: Includes property with equipment owned by a gas, telephone or electric company.
  Class 4: Includes all other properties not included in class 1,2, and 3, such as offices, factories, warehouses, garage buildings, etc. Glossary of Terms for Property Sales Files
- Block: A Tax Block is a sub-division of the borough on which real properties are located. The Department of Finance uses a Borough-Block-Lot classification to label all real property in the City. “Whereas” addresses describe the street location of a property, the block and lot distinguishes one unit of real property from another, such as the different condominiums in a single building. Also, block and lots are not subject to name changes based on which side of the parcel the building puts its entrance on.
- Lot: A Tax Lot is a subdivision of a Tax Block and represents the property unique location.
- Easement: An easement is a right, such as a right of way, which allows an entity to make limited use of another’s real property. For example: MTA railroad tracks that run across a portion of another property.
- Building Class at Present: The Building Classification is used to describe a property’s constructive use. The first position of the Building Class is a letter that is used to describe a general class of properties (for example “A” signifies one-family homes, “O” signifies office buildings. “R” signifies condominiums). The second position, a number, adds more specific information about the property’s use or construction style (using our previous examples “A0” is a Cape Cod style one family home, “O4” is a tower type office building and “R5” is a commercial condominium unit). The term Building Class used by the Department of Finance is interchangeable with the term Building Code used by the Department of Buildings. See NYC Building Classifications.
- Address: The street address of the property as listed on the Sales File. Coop sales include the apartment number in the address field.
- Zip Code: The property’s postal code
- Residential Units: The number of residential units at the listed property.
- Commercial Units: The number of commercial units at the listed property.
- Total Units: The total number of units at the listed property.
- Land Square Feet: The land area of the property listed in square feet.
- Gross Square Feet: The total area of all the floors of a building as measured from the exterior surfaces of the outside walls of the building, including the land area and space within any building or structure on the property.
- Year Built: Year the structure on the property was built.
- Building Class at Time of Sale: The Building Classification is used to describe a property’s constructive use. The first position of the Building Class is a letter that is used to describe a general class of properties (for example “A” signifies one-family homes, “O” signifies office buildings. “R” signifies condominiums). The second position, a number, adds more specific information about the property’s use or construction style (using our previous examples “A0” is a Cape Cod style one family home, “O4” is a tower type office building and “R5” is a commercial condominium unit). The term Building Class as used by the Department of Finance is interchangeable with the term Building Code as used by the Department of Buildings.
- Sales Price: Price paid for the property.
- Sale Date: Date the property sold.
  $0 Sales Price: A $0 sale indicates that there was a transfer of ownership without a cash consideration. There can be a number of reasons for a $0 sale including transfers of ownership from parents to children.
- Sale Date: Date the property sold.

# Code For Pgadmin

#Create Table
CREATE TABLE IF NOT EXISTS public."Bronx"
(
"Borough" integer NOT NULL,
"Neighborhood" character varying,
"Building 'Class' Category" character varying,
"Tax 'Class' 'At' Present" character varying,
"Block" integer,
"Lot" integer,
"Ease-Ment" character varying,
"Building 'Class' 'At' Present" character varying,
"Address" character varying,
"Apartment 'Number'" character varying,
"Zip Code" integer,
"Residential Units" integer,
"Commercial Units" integer,
"Total Units" integer,
"Land Square Feet" integer,
"Gross Square Feet" integer,
"Year Built" integer,
"Tax 'Class' 'At' Time 'Of' Sale" character varying,
"Building 'Class' 'At' Time `Of` Sale" character varying,
"Sale Price" integer,
"Sale Date" date
);
ALTER TABLE public."Bronx"
OWNER to postgres;

CREATE TABLE IF NOT EXISTS public."Brooklyn"
(
"Borough" integer NOT NULL,
"Neighborhood" character varying,
"Building 'Class' Category" character varying,
"Tax 'Class' 'At' Present" character varying,
"Block" integer,
"Lot" integer,
"Ease-Ment" character varying,
"Building 'Class' 'At' Present" character varying,
"Address" character varying,
"Apartment 'Number'" character varying,
"Zip Code" integer,
"Residential Units" integer,
"Commercial Units" integer,
"Total Units" integer,
"Land Square Feet" integer,
"Gross Square Feet" integer,
"Year Built" integer,
"Tax 'Class' 'At' Time 'Of' Sale" character varying,
"Building 'Class' 'At' Time `Of` Sale" character varying,
"Sale Price" integer,
"Sale Date" date
);
ALTER TABLE public."Brooklyn"
OWNER to postgres;
CREATE TABLE IF NOT EXISTS public."Manhattan"
(
"Borough" integer NOT NULL,
"Neighborhood" character varying,
"Building 'Class' Category" character varying,
"Tax 'Class' 'At' Present" character varying,
"Block" integer,
"Lot" integer,
"Ease-Ment" character varying,
"Building 'Class' 'At' Present" character varying,
"Address" character varying,
"Apartment 'Number'" character varying,
"Zip Code" integer,
"Residential Units" integer,
"Commercial Units" integer,
"Total Units" integer,
"Land Square Feet" integer,
"Gross Square Feet" integer,
"Year Built" integer,
"Tax 'Class' 'At' Time 'Of' Sale" character varying,
"Building 'Class' 'At' Time `Of` Sale" character varying,
"Sale Price" integer,
"Sale Date" date
);
ALTER TABLE public."Manhattan"
OWNER to postgres;

CREATE TABLE IF NOT EXISTS public."Queens"
(
"Borough" integer NOT NULL,
"Neighborhood" character varying,
"Building 'Class' Category" character varying,
"Tax 'Class' 'At' Present" character varying,
"Block" integer,
"Lot" integer,
"Ease-Ment" character varying,
"Building 'Class' 'At' Present" character varying,
"Address" character varying,
"Apartment 'Number'" character varying,
"Zip Code" integer,
"Residential Units" integer,
"Commercial Units" integer,
"Total Units" integer,
"Land Square Feet" integer,
"Gross Square Feet" integer,
"Year Built" integer,
"Tax 'Class' 'At' Time 'Of' Sale" character varying,
"Building 'Class' 'At' Time `Of` Sale" character varying,
"Sale Price" integer,
"Sale Date" date
);
ALTER TABLE public."Queens"
OWNER to postgres;

CREATE TABLE IF NOT EXISTS public."StatenIsland"
(
"Borough" integer NOT NULL,
"Neighborhood" character varying,
"Building 'Class' Category" character varying,
"Tax 'Class' 'At' Present" character varying,
"Block" integer,
"Lot" integer,
"Ease-Ment" character varying,
"Building 'Class' 'At' Present" character varying,
"Address" character varying,
"Apartment 'Number'" character varying,
"Zip Code" integer,
"Residential Units" integer,
"Commercial Units" integer,
"Total Units" integer,
"Land Square Feet" integer,
"Gross Square Feet" integer,
"Year Built" integer,
"Tax 'Class' 'At' Time 'Of' Sale" character varying,
"Building 'Class' 'At' Time `Of` Sale" character varying,
"Sale Price" integer,
"Sale Date" date
);
ALTER TABLE public."StatenIsland"
OWNER to postgres;

#Import Data
COPY “Bronx”
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/03_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/04_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/05_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/06_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/2007_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/2008_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/2009_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/2010_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/2011_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/2012_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/2013_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/2014_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/2015_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/2016_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/2017_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/2018_Bronx.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Bronx/2019_Bronx.csv'
DELIMITER ','
CSV HEADER;

COPY “Brooklyn”
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/03_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/04_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/05_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/06_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/2007_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/2008_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/2009_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/2010_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/2011_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/2012_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/2013_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/2014_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/2015_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/2016_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/2017_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/2018_Brooklyn.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Brooklyn/2019_Brooklyn.csv'
DELIMITER ','
CSV HEADER;

COPY “Manhattan”
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/03_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/04_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/05_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/06_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/2007_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/2008_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/2009_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/2010_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/2011_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/2012_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/2013_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/2014_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/2015_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/2016_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/2017_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/2018_Manhattan.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Manhattan/2019_Manhattan.csv'
DELIMITER ','
CSV HEADER;

COPY “Queens”
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/03_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/04_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/05_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/06_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/2007_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/2008_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/2009_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/2010_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/2011_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/2012_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/2013_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/2014_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/2015_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/2016_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/2017_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/2018_Queens.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/Queens/2019_Queens.csv'
DELIMITER ','
CSV HEADER;

COPY “StatenIsland”
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/03_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/04_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/05_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/06_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/2007_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/2008_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/2009_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/2010_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/2011_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/2012_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/2013_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/2014_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/2015_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/2016_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/2017_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/2018_StatenIsland.csv'
FROM '/Users/aitorgoyenechea/Downloads/Nyc/StatenIsland/2019_StatenIsland.csv'
DELIMITER ','
CSV HEADER;

Rename Tables  
ALTER TABLE public."Bronx"
RENAME "Building 'Class' Category" TO "Building_Class_Category";
ALTER TABLE public."Bronx"
RENAME "Tax 'Class' 'At' Present" TO "Tax_Class_At_Present";
ALTER TABLE public."Bronx"
RENAME "Building 'Class' 'At' Present" TO "Building_Class_At_Present";
ALTER TABLE public."Bronx"
RENAME "Apartment 'Number'" TO "Apartment_Number";
ALTER TABLE public."Bronx"
RENAME "Zip Code" TO "Zip_Code";
ALTER TABLE public."Bronx"
RENAME "Residential Units" TO "Residential_Units";
ALTER TABLE public."Bronx"
RENAME "Commercial Units" TO "Commercial_Units";
ALTER TABLE public."Bronx"
RENAME "Total Units" TO "Total_Units";
ALTER TABLE public."Bronx"
RENAME "Land Square Feet" TO "Land_Square_Feet";
ALTER TABLE public."Bronx"
RENAME "Gross Square Feet" TO "Gross_Square_Feet";
ALTER TABLE public."Bronx"
RENAME "Year Built" TO "Year_Built";
ALTER TABLE public."Bronx"
RENAME "Tax 'Class' 'At' Time 'Of' Sale" TO "Tax_Class_At_Time_Of_Sale";
ALTER TABLE public."Bronx"
RENAME "Building 'Class' 'At' Time `Of` Sale" TO "Building_Class_At_Time_Of_Sale";
ALTER TABLE public."Bronx"
RENAME "Sale Price" TO "Sale_Price";
ALTER TABLE public."Bronx"
RENAME "Sale Date" TO "Sale_Date";

#Rename Tables  
ALTER TABLE public."StatenIsland"
RENAME "Building 'Class' Category" TO "Building_Class_Category";
ALTER TABLE public."StatenIsland"
RENAME "Tax 'Class' 'At' Present" TO "Tax_Class_At_Present";
ALTER TABLE public."StatenIsland"
RENAME "Building 'Class' 'At' Present" TO "Building_Class_At_Present";
ALTER TABLE public."StatenIsland"
RENAME "Apartment 'Number'" TO "Apartment_Number";
ALTER TABLE public."StatenIsland"
RENAME "Zip Code" TO "Zip_Code";
ALTER TABLE public."StatenIsland"
RENAME "Residential Units" TO "Residential_Units";
ALTER TABLE public."StatenIsland"
RENAME "Commercial Units" TO "Commercial_Units";
ALTER TABLE public."StatenIsland"
RENAME "Total Units" TO "Total_Units";
ALTER TABLE public."StatenIsland"
RENAME "Land Square Feet" TO "Land_Square_Feet";
ALTER TABLE public."StatenIsland"
RENAME "Gross Square Feet" TO "Gross_Square_Feet";
ALTER TABLE public."StatenIsland"
RENAME "Year Built" TO "Year_Built";
ALTER TABLE public."StatenIsland"
RENAME "Tax 'Class' 'At' Time 'Of' Sale" TO "Tax_Class_At_Time_Of_Sale";
ALTER TABLE public."StatenIsland"
RENAME "Building 'Class' 'At' Time `Of` Sale" TO "Building_Class_At_Time_Of_Sale";
ALTER TABLE public."StatenIsland"
RENAME "Sale Price" TO "Sale_Price";
ALTER TABLE public."StatenIsland"
RENAME "Sale Date" TO "Sale_Date";

#Rename Tables  
ALTER TABLE public."Brooklyn"
RENAME "Building 'Class' Category" TO "Building_Class_Category";
ALTER TABLE public."Brooklyn"
RENAME "Tax 'Class' 'At' Present" TO "Tax_Class_At_Present";
ALTER TABLE public."Brooklyn"
RENAME "Building 'Class' 'At' Present" TO "Building_Class_At_Present";
ALTER TABLE public."Brooklyn"
RENAME "Apartment 'Number'" TO "Apartment_Number";
ALTER TABLE public."Brooklyn"
RENAME "Zip Code" TO "Zip_Code";
ALTER TABLE public."Brooklyn"
RENAME "Residential Units" TO "Residential_Units";
ALTER TABLE public."Brooklyn"
RENAME "Commercial Units" TO "Commercial_Units";
ALTER TABLE public."Brooklyn"
RENAME "Total Units" TO "Total_Units";
ALTER TABLE public."Brooklyn"
RENAME "Land Square Feet" TO "Land_Square_Feet";
ALTER TABLE public."Brooklyn"
RENAME "Gross Square Feet" TO "Gross_Square_Feet";
ALTER TABLE public."Brooklyn"
RENAME "Year Built" TO "Year_Built";
ALTER TABLE public."Brooklyn"
RENAME "Tax 'Class' 'At' Time 'Of' Sale" TO "Tax_Class_At_Time_Of_Sale";
ALTER TABLE public."Brooklyn"
RENAME "Building 'Class' 'At' Time `Of` Sale" TO "Building_Class_At_Time_Of_Sale";
ALTER TABLE public."Brooklyn"
RENAME "Sale Price" TO "Sale_Price";
ALTER TABLE public."Brooklyn"
RENAME "Sale Date" TO "Sale_Date";

#Rename Tables  
ALTER TABLE public."Manhattan"
RENAME "Building 'Class' Category" TO "Building_Class_Category";
ALTER TABLE public."Manhattan"
RENAME "Tax 'Class' 'At' Present" TO "Tax_Class_At_Present";
ALTER TABLE public."Manhattan"
RENAME "Building 'Class' 'At' Present" TO "Building_Class_At_Present";
ALTER TABLE public."Manhattan"
RENAME "Apartment 'Number'" TO "Apartment_Number";
ALTER TABLE public."Manhattan"
RENAME "Zip Code" TO "Zip_Code";
ALTER TABLE public."Manhattan"
RENAME "Residential Units" TO "Residential_Units";
ALTER TABLE public."Manhattan"
RENAME "Commercial Units" TO "Commercial_Units";
ALTER TABLE public."Manhattan"
RENAME "Total Units" TO "Total_Units";
ALTER TABLE public."Manhattan"
RENAME "Land Square Feet" TO "Land_Square_Feet";
ALTER TABLE public."Manhattan"
RENAME "Gross Square Feet" TO "Gross_Square_Feet";
ALTER TABLE public."Manhattan"
RENAME "Year Built" TO "Year_Built";
ALTER TABLE public."Manhattan"
RENAME "Tax 'Class' 'At' Time 'Of' Sale" TO "Tax_Class_At_Time_Of_Sale";
ALTER TABLE public."Manhattan"
RENAME "Building 'Class' 'At' Time `Of` Sale" TO "Building_Class_At_Time_Of_Sale";
ALTER TABLE public."Manhattan"
RENAME "Sale Price" TO "Sale_Price";
ALTER TABLE public."Manhattan"
RENAME "Sale Date" TO "Sale_Date";

#Rename Tables  
ALTER TABLE public."Queens"
RENAME "Building 'Class' Category" TO "Building_Class_Category";
ALTER TABLE public."Queens"
RENAME "Tax 'Class' 'At' Present" TO "Tax_Class_At_Present";
ALTER TABLE public."Queens"
RENAME "Building 'Class' 'At' Present" TO "Building_Class_At_Present";
ALTER TABLE public."Queens"
RENAME "Apartment 'Number'" TO "Apartment_Number";
ALTER TABLE public."Queens"
RENAME "Zip Code" TO "Zip_Code";
ALTER TABLE public."Queens"
RENAME "Residential Units" TO "Residential_Units";
ALTER TABLE public."Queens"
RENAME "Commercial Units" TO "Commercial_Units";
ALTER TABLE public."Queens"
RENAME "Total Units" TO "Total_Units";
ALTER TABLE public."Queens"
RENAME "Land Square Feet" TO "Land_Square_Feet";
ALTER TABLE public."Queens"
RENAME "Gross Square Feet" TO "Gross_Square_Feet";
ALTER TABLE public."Queens"
RENAME "Year Built" TO "Year_Built";
ALTER TABLE public."Queens"
RENAME "Tax 'Class' 'At' Time 'Of' Sale" TO "Tax_Class_At_Time_Of_Sale";
ALTER TABLE public."Queens"
RENAME "Building 'Class' 'At' Time `Of` Sale" TO "Building_Class_At_Time_Of_Sale";
ALTER TABLE public."Queens"
RENAME "Sale Price" TO "Sale_Price";
ALTER TABLE public."Queens"
RENAME "Sale Date" TO "Sale_Date";

#Join Tables
SELECT "Sales".index, "Gross_Square_Feet", "Sale_Price", "Sale_Date", "Year"
INTO "Sales_join_Address"
FROM public."Sales"
JOIN public."Address" on "Sales".index = "Address".index
