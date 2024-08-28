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
*Six tables:

    * One table for listings information from the listings.csv file
    * One table with hosts information from the listings.csv file
    * One table with listings reviews from the reviews.csv file
    * One table with rooms type information from the listings.csv file
    * One table with properties types information from the listings.csv file
    * A table with dates was created using the CALENDAR function.
    
* Tables are linked together:
  
    * Listings and hosts tables linked together by host_id
    * Hosts table and date table linked together by host_since
    * Hosts table and reviews table linked together by review_date
    * Listings and rooms type tables linked together by room_id
    * Listings and properties type tables linked together by property_id
    * Listings and reviews table linked together by listing_id
      










  
