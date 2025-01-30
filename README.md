Part 1: Database and Jupyter Notebook 

1.Data Import:
Imported establishments.json into MongoDB using the mongoimport command, naming the database uk_food and the collection establishments.

2.Verify Database Setup:
Listed all databases to confirm uk_food exists.
Verified that the establishments collection was created successfully.
Displayed a sample document using find_one and pprint.
Assigned the establishments collection to a variable for further use.

Part 2: Updating the Database

1.Added a New Restaurant:
Inserted a document for a new halal restaurant, "Penang Flavours", with the provided details into the establishments collection.

2.Updated the BusinessTypeID:
Queried the BusinessTypeID for "Restaurant/Cafe/Canteen" using a filter.
Updated the new restaurant's record with the correct BusinessTypeID.

3.Removed Establishments in Dover:
Counted the number of establishments with the LocalAuthorityName "Dover."
Deleted all documents matching the LocalAuthorityName "Dover."
Verified that the deletion was successful.

4.Converted Data Types:
Used update_many to convert latitude and longitude in the geocode field from strings to decimals.
Converted RatingValue to integers, ensuring non-numeric values (e.g., "Pass") were coerced to null before conversion.

Part 3: Exploratory Analysis

1.Establishments with Hygiene Score Equal to 20:
Queried the database for establishments with scores.Hygiene: 20.
Counted matching documents and displayed the first result using pprint.
Converted the query results into a Pandas DataFrame and displayed the first 10 rows.

2.Establishments in London with RatingValue ≥ 4:
Queried establishments in London using a $regex filter on LocalAuthorityName and filtered for RatingValue >= 4.
Counted and displayed matching documents, then converted results into a Pandas DataFrame.

3.Top 5 Establishments with RatingValue of 5 Near "Penang Flavours":
Found the geocode of "Penang Flavours" and searched for nearby establishments (within ±0.01 degrees).
Filtered for RatingValue: 5 and sorted by scores.Hygiene (ascending).
Limited the results to the top 5 and converted them into a Pandas DataFrame for analysis.

4.Local Authorities with the Most Hygiene Scores of 0:
Used the MongoDB aggregation pipeline to group by LocalAuthorityName and count documents with scores.Hygiene: 0.
Sorted the results in descending order and displayed the top 10 local authorities.
Converted the aggregated results into a Pandas DataFrame.

Key Queries Answered:
1.Which establishments have a hygiene score of 20?
Found and displayed establishments with poor hygiene ratings.

2.Which establishments in London have a RatingValue ≥ 4?
Filtered establishments with good overall ratings in London.

3.What are the top 5 establishments near "Penang Flavours" with a RatingValue of 5?
Used geospatial proximity and hygiene scores to identify top-rated nearby establishments.

4.Which Local Authorities have the most hygiene scores of 0?
Aggregated data to identify areas with the highest number of poorly rated establishments.

Tools Used:
MongoDB: For data querying, filtering, updating, and aggregation.
PyMongo: Python library for MongoDB interactions.
Pandas: To convert query results into DataFrames for further analysis and visualization.
