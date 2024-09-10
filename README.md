# ANALYSIS-OF-GREEK-AIRBNB-LISTINGS-IN-POWERBI

## ABOUT THE DATASET
In this challenge, I had the opportunity to analyze Airbnb data for 12,960 listings across 44 cities. The dataset included details about hosts, pricing, location, and room types, along with over 500,000 reviews. The prices were provided in the local currency.
### Data Files
* First file is the listings.csv file that contains information about Airbnb listings and hosts
* Second file is the reviews.csv file that contains information about the reviews a property has received
### Resources 
The data are from the official site of Airbnb and they are licensed under a Creative Commons Attribution 4.0 International License.
http://creativecommons.org/licenses/by/4.0/

### Concept for a Relational Database Design

*Seven tables:

    * One table for listings information from the listings.csv file
    * One table with hosts information from the listings.csv file
    * One table with listings reviews from the reviews.csv file
    * One table with rooms type information from the listings.csv file
    * One table with properties types information from the listings.csv file
    * A table with dates was created using the CALENDAR function linked with the DimHostTable.
    * A table with dates was created using the CALENDAR function linked with the FactReviewsTable.
    

### Data Cleaning 
The first step in the data cleaning process was correcting data types. 
Latitude, longitude, and review score columns were converted to float for accurate calculations, while beds and bedrooms were changed to integer to reflect counts. 
Additionally, host-related columns like host_response_rate and host_acceptance_time were converted to float, while host_response_time, host_has_profile_pic, and host_identity_verified were changed to text. 

The second step in the data cleaning process was to replace null values. In the Dimhost table, null values in the host_name and host_location columns were replaced with "Unknown". In the host_response_time column, null values were replaced with "N/A". For the columns host_is_superhost, host_identity_verified, and host_has_profile_pic in the Dimhost table and for the column instant_bookable in the FactListings table, null values were handled by mapping false to 0 and true to 1.

Final step in the data cleaning process was to extract the bathrooms column from the original bathrooms_text column. This was done by extracting the text before the space character, which served as the delimiter.

### Data Transformations
Using PowerQuery, we created our first DAX measure called NumberofHosts, which helps us determine the number of accommodations included in the project. For illustration, we used the COUNTROWS function as follows:
COUNTROWS(DimHost).

Secondly, we created a DAX Measure called Pricing_Listing where we calculated the overall pricing of accommodations where hosts are located in Κουκάκι-Μακρυγιάννη, one of the most popular neighborhoods in Athens.Dax Syntax : CALCULATE(SUM(FactListings[price]),FactListings[city_location]="Κουκακι-Μακρυγιαννη"))

To complete the transformations in PowerQuery, we created two conditional columns for more detailed analysis. The first column, called is_shared, was created to determine if the majority of bathrooms were shared.  The column was set up using the Add Column feature in PowerQuery View, with the following syntax: if bathrooms_text contains shared then 1 else 0. 

To conclude, we created a second conditional column called Price Category, which categorizes prices based on their value. The column was set up with the following syntax:  if [price] < 100 then "cheap" else if [price] = 200 then "mid-range" else "expensive".

### Data Modelling 
At the start of the data modeling process, we verified in the model view that all data types were correct and ensured that countable measures had the appropriate symbols. We then checked that the host_response_rate and host_acceptance_rate columns were formatted as percentages. Additionally, we added data categories to columns such as latitude, longitude, and city_location (with the data category city), and host_location (with the data category place). For columns like latitude, longitude, host_acceptance_rate, host_response_rate, maximum_nights, and minimum_nights, we also included further descriptions.

Further along in the modeling process, we defined key columns for the tables as follows:
* In the Dimhost table, the primary key is the host_id column.
* In the DimPropertyType table, the primary key is the property_id column.
* In the DimRoomType table, the primary key is the room_id column.
* In the Factlistings table, the primary key is the listing_id column.

Continuing, we reviewed the relationships and cardinality of the schema to ensure proper data connections and integrity.
Tables are linked together:

* FactListings and Dimhost table linked together by host_id (cardinality: many to one)
* Dimhost table and DateHost table linked together by host_since (cardinality: many to one)
* FactListings and FactReviews table linked together by listing_id (cardinality: many to one)
* FactReviews and DateReviews table linked together by review_date (cardinality: many to one)
* FactListings and DimRoomType table linked together by room_id (cardinality: many to one)
* FactListings and DimPropertyType table linked together by property_id (cardinality: many to one)

### Purpose of this project
The purpose of this project is to create a DashBoard from 2 CSV files related with Airbnb listings and reviews. The data process required us to use Microsoft PowerBI. By creating the Data model that follows a Star Schema, it was decided to answer to some business questions. Below you can find a detailed description of those:

### Key Questions
* What’s the average price of accommodations on Airbnb’s site and how the price differs.
* Which neighborhood is the most popular in Greece and what makes her stand out among the others.
* Is it true that the number of reviews contributes to a higher number of visitors.
* Features that can help an Airbnb listing become more popular.
* SuperHosts Insights

### Conclusion

To sum up the findings of this project:

* The Average price per night for an Airbnb listing is 110€.

* The ideal month for the app to increase prices is September due to the rise of the listings.

* After Airbnb’s official launch in 2008, 2011,2018,2021 seem to be the  years that the average price of an Airbnb increased.

* Εμπορικό Τρίγωνο-Πλάκα seems to have the highest numbers of listings and a price only 30 € more than the average price of an Airbnb.

* Ρηγίλλης might be the city with the highest average price - The average price of an Airbnb listing in Ρηγίλλης is 368€- , but at the same time it ranks as the top reviewed for location.

* Κουκάκι-Μακρυγιάννη is the city with the highest average score among the top 10 cities in reviews for listings. The check-in process, communication, cleanliness and accuracy seem to work well in listings for 
  this area.

* The highest number of total reviews by city belongs to Εμπορικό Τρίγωνο-Πλάκα with 9,704 reviews. 
  
* We noticed that the highest number of reviews is on May. On July we had the lowest number of reviews.

* Entire apartments undoubtly have more listings on the app, since they combine comfort and lower prices.

* Superhosts have 60% more listings on the app than those who haven’t earned the qualification. Airbnb seems to reward superhosts since their average response rate reaches at 100%.


 








    
  
    
  
















































      










  
