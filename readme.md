# learning mongodb

- no sql database

- Querying from database

  - Adhoc queries. Explore your MongoDB data with mongosh, Compass , VSCode or a MongoDB driver.

  - Data transformations. Use aggregation pipelines to reshape your data and perform calculations.

  - Document join support Use $lookup and $unionWith to combine data from different collections.

  - Graph and geospatial queries. Use operators such as $geoWithin and $geoNear to analyze geospatial data and $graphLookup for graph data.

  - Full-text search. Use the $search stage to perform efficient text search on your data.

  - Semantic search. Use the $vectorSearch stage to perform semantic search on your data.

  - Indexing. Improve your MongoDB query performance by using the correct index type for your data architecture.

  - On-demand materialized views. Use $out and $merge to create materialized views on common queries.

  - Time series analysis. Query and aggregate your time-stamped data with time series collections.

## Getting started

- to get more info about the mongodb database, just visit `https://www.mongodb.com/docs/manual/tutorial/getting-started/`

- CLI tool : mongosh

  - installation : `https://www.mongodb.com/docs/mongodb-shell/install/`

- GUI tool : use mongo atlas or compass

- for dataset, go to kaggle and import whatever you want and start to play with the database

  ```
  import the dataset

  mongo_db % mongoimport --uri="mongodb://localhost:27017" \
  --db=<db_name> \
  --collection=rating \
  --type=csv \
  --headerline \
  --file=<path_to_file>
  ```

## Basics

- **Database commands :**

  - Create db mydb

    ```
    > use mydb
    switched to db mydb
    ```

  - list all databases

    ```
    > show dbs
    ```

  - delete database

    ```
    > db.dropDatabase("test");
    ```

- **Collection commands :**

  - Create a collection mycollection

    ```
    > db.createCollection("mycollection")
    { "ok" : 1 }
    ```

  - view collections

    ```
    > use <db_name> // to change the database
    > db.getCollectionNames() // to get it as array

    -----  or  ------

    > show collections
    ```

  - rename collection

    ```
    > db.<old_collection_name>.renameCollection("new_collection_name");
    ```

  - drop collection

    ```
    > use <db_name>
    > db.<collection_name>.drop()
    ```

  - to get the stats about the collection

    ```
    db.<collection_name>.stats()
    ```

- the bulk write

  ```
  try {
  db.<collection_name>.bulkWrite([
  {
  insertOne: {
  document: <document_1>
  }
  },
  {
  insertOne: {
  document: <document_2>
  }
  },
  {
  insertOne: {
  document: <document_3>
  }
  },
  {
  updateOne: {
  filter: <filter>,
  update: { $set: <new_value> }
  }
  }
  ], { ordered: true });
  } catch (err) {
  print(err);
  }
  ```

- Project only the required fields
  ```
  >db.<collection_name>.find(<filter>).projection(<projection list>); // eg: projection({item:1}) => only item and _id will be added to the final results
  ```
- Import dataset into mongodb

  ```
  mongo_db % mongoimport --uri="mongodb://localhost:27017" \
  --db=movies \
  --collection=rating \
  --type=csv \
  --headerline \
  --file=./archive/ratings.csv
  ```
