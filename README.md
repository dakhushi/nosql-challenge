# Data Analysis using NoSQL ( MongoDB)

## Instructions
The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating.
You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

### Part 1: Database and Jupyter Notebook Set Up
- Import the data provided in the establishments.json file from your Terminal. 
- Name the database uk_food and the collection establishments. Copy the text you used to import your data from your Terminal to a markdown cell in your notebook.
- Within your notebook, import the libraries you need: PyMongo and Pretty Print (pprint).
- Create an instance of the Mongo Client.
- Confirm that you created the database and loaded the data properly:
- List the databases you have in MongoDB. Confirm that uk_food is listed.
- List the collection(s) in the database to ensure that establishments is there.
- Find and display one document in the establishments collection using find_one and display with pprint.
- Assign the establishments collection to a variable to prepare the collection for use.

### Part 2: Update the Database
The magazine editors have some requested modifications for the database before you can perform any queries or analysis for them. Make the following changes to the establishments collection:
- An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked you to include it in your analysis. Add the following information to the database:

```
{
    "BusinessName":"Penang Flavours",
    "BusinessType":"Restaurant/Cafe/Canteen",
    "BusinessTypeID":"",
    "AddressLine1":"Penang Flavours",
    "AddressLine2":"146A Plumstead Rd",
    "AddressLine3":"London",
    "AddressLine4":"",
    "PostCode":"SE18 7DY",
    "Phone":"",
    "LocalAuthorityCode":"511",
    "LocalAuthorityName":"Greenwich",
    "LocalAuthorityWebSite":"http://www.royalgreenwich.gov.uk",
    "LocalAuthorityEmailAddress":"health@royalgreenwich.gov.uk",
    "scores":{
        "Hygiene":"",
        "Structural":"",
        "ConfidenceInManagement":""
    },
    "SchemeType":"FHRS",
    "geocode":{
        "longitude":"0.08384000",
        "latitude":"51.49014200"
    },
    "RightToReply":"",
    "Distance":4623.9723280747176,
    "NewRatingPending":True
}
```
- Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the BusinessTypeID and BusinessType fields.
- Update the new restaurant with the BusinessTypeID you found.
- The magazine is not interested in any establishments in Dover, so check how many documents contain the Dover Local Authority. Then, remove any establishments within the Dover Local Authority from the database, and check the number of documents to ensure they were deleted.
- Some of the number values are stored as strings, when they should be stored as numbers.
- Use update_many to convert latitude and longitude to decimal numbers.
- Use update_many to convert RatingValue to integer numbers.

### Part 3: Exploratory Analysis
Eat Safe, Love has specific questions they want you to answer, which will help them find the locations they wish to visit and avoid.
Some notes to be aware of while you are exploring the dataset:
RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.

Note: This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating. We will coerce non-numeric values to nulls during the database setup before converting ratings to integers.
The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. This means, the higher the value, the worse the establishment is in these areas.

Use the following questions to explore the database, and find the answers, so you can provide them to the magazine editors.
Unless otherwise stated, for each question:
Use count_documents to display the number of documents contained in the result.
Display the first document in the results using pprint.
Convert the result to a Pandas DataFrame, print the number of rows in the DataFrame, and display the first 10 rows.



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
