# Data Analysis using NoSQL ( MongoDB)

## Instructions
The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating.
You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

**Database Management (NoSQL/MongoDB):**
- Created, managed, and queried databases using MongoDB.**
- Imported JSON data into MongoDB collections using mongoimport.
 ![image](https://github.com/user-attachments/assets/39efc549-2f46-4bc3-9163-2a050e093623)
- Demonstrated proficiency with database setup, updating, and querying.

  
**Data Cleaning and Preprocessing:**

- Converted data types (e.g., strings to decimal numbers and integers) to ensure data consistency.
  ![image](https://github.com/user-attachments/assets/e90817af-c1ac-4139-9dbd-fbee4989ceea)

- Used update_many for bulk data updates to clean and standardize datasets.
![image](https://github.com/user-attachments/assets/a5aaf560-972e-4ec9-9af7-71e69d9ec9c5)

**Data Manipulation:**

- Updated and modified datasets using MongoDB queries (e.g., adding new records, updating fields, and removing unnecessary records).
- Performed aggregation queries to group and sort data for insights.

**Exploratory Data Analysis (EDA):**

- Used MongoDB and Pandas to analyze datasets, identifying patterns and trends.
- Built and applied queries to filter data by specific conditions (e.g., hygiene score, RatingValue).
- Aggregated data to summarize insights (e.g., top establishments by hygiene score).

**Geospatial Data Analysis:**

- Leveraged geolocation fields (latitude and longitude) to find nearby establishments.
- Utilized geospatial queries to compare locations and identify top-rated establishments near a specific point.

**Visualization and Reporting:**

- Converted query results to Pandas DataFrames for further analysis and reporting.
- Presented results in a structured format using DataFrames, enhancing interpretability.

**Python Libraries and Tools:**

- sed PyMongo for MongoDB queries.
- Applied Pretty Print (pprint) for enhanced readability of database records.
- Leveraged Pandas for data analysis and transformation.


![image](https://github.com/user-attachments/assets/21a25d8d-f3c4-4c0b-a583-95dc71e7986b)

**Addressed the Business Questions**

**1. Which establishments have a hygiene score equal to 20?**

Total 41 establishments have a hygiene score equal to 20
Establishment names are:

1. The Chase Rest Home
2. Brenalwood
3. Melrose Hotel
4. Seaford Pizza
5. Golden Palace
6. Ashby's Butchers
7. South Sea Express Cuisine
8. The Tulip Tree
9. F & S
10. Longhouse
11. Westview Playgroup Based At Downsview Comm Primary
12. Whatever The Weather Coffee
13. Kings Restaurant (Oriental)
14. Xich Lo
15. Asian Supermarket Ltd: T/A Best Food Wine Ltd
16. Londis
17. Costcutter
18. La Simon Ltd
19. Caribiscus Ltd
20. Kennedy Fried Chicken
21. Gah Shing
22. A1 News & Wine
23. Cakes & Bakes
24. Sahajanand Catering Limited
25. Sisko Cafe
26. Magazin Romanesc Diana
27. Bali Maamalas
28. Angels Bakery
29. Nikkis Place Restaurant
30. Chicago 30
31. Samui Thai Restaurant
33. Pakhtoonkhwa Restaurant
34. New Happy Garden
35. Mummy Yum
36. Gospodina
37. Leo's Bar & Grill
38. Royal Ribs
39. Great Hallingbury Manor Hotel
40. The Dog And Duck
41. Oriental Cottage

**2. Which establishments in London have a RatingValue greater than or equal to 4?**

Hint: The London Local Authority has a longer name than "London" so you will need to use $regex as part of your search.

Total 33 establishments in London have a RatingValue greater than or equal to 4
Establishment names are:

1. Charlie's
2. Mv City Cruises Erasmus
3. Benfleet Motor Yacht Club
4. Coombs Catering t/a The Lock and Key
5. Tilbury Seafarers Centre
6. Mv Valulla
7. Tereza Joanne
8. Brick Lane Brews
9. The Nuance Group (UK) Limited
10. WH Smith
11. City Bar & Grill
12. Caffè Nero
13. Jet Centre
14. Mv Sunborn Yacht Hotel
15. Good Hotel London
16. La Nonna lina
17. Wake Up Docklands Limited
18. MV Venus Clipper
19. MV Typhoon clipper
20. MV Moon clipper
21. MV Jupiter clipper
22. MV Monsoon clipper
23. MV Meteor clipper
24. MV Mercury clipper
25. MV Tornado clipper
26. MV Cyclone clipper
27. MV Hurricane clipper
28. MV Neptune clipper
29. MV Galaxy clipper
30. MV Sun clipper
31. Mv Storm Clipper
32. Canary Wharf 1V
33. MV Aurora clipper

**3. What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?**

Hint: You will need to compare the geocode to find the nearest locations. Search within 0.01 degree on either side of the latitude and longitude.

Top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to Penang Flavours are

1. Volunteer
2. Plumstead Manor Nursery
3. Atlantic Fish Bar
4. Iceland
5. Howe and Co Fish and Chips - Van 17
   
**4. How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.**
Hint: You will need to use the aggregation method to answer this.

Total number of establishments in each Local Authority area with hygiene score of 0 :  55
Top 10 Local Authority area are:

1. 'Thanet', 'count': 1130
2. 'Greenwich', 'count': 882
3. 'Maidstone', 'count': 713
4.  'Newham', 'count': 711
5. 'Swale', 'count': 686
6. 'Chelmsford', 'count': 680
7. 'Medway', 'count': 672
8. 'Bexley', 'count': 607
9. 'Southend-On-Sea', 'count': 586
10. 'Tendring', 'count': 542

##### References
- UK Food Standards AgencyLinks to an external site. (2022). UK food hygiene rating data API. https://ratings.food.gov.uk/open-data/en-GBLinks to an external site.. Contains public sector information licensed under the Open Government Licence v3.0Links to an external site.
Accessed Sept 9, 2022 and Sept 12, 2022 with the establishment settings as follows: longitude=51.5072, latitude=-0.1276, maxdistancelimit=4567, pagesize=10000, sortoptionkey=distance, pagenumber=(1,2,3,4,5,6,7,8).
