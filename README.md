# Amazon Vine Analysis
Module 16 Challenge

## Project Overview
The purpose of this project is to analyze Amazon customer reviews of the paid Amazon Vine program, which is a service that allows manufacturers and publishers to receive reviews for their products. Utilizing PySpark, the ETL process will extract the dataset, transform the data and connect to an AWS RDS instance.  The transformed data will then be loaded into pgAdmin.  Lastly, Pandas is used to determine if there is any bias towards favorable reviews from Vine members in the dataset.  

### Technical Analysis Deliverables
- Deliverable 1: Perform ETL on Amazon Product Reviews
- Deliverable 2: Determine Bias of Vine Reviews

### Software & Resources
-	PySpark
-	PostgreSQL
-	AWS RDS
-	Pandas
-	Dataset: The dataset derived from 
[Amazon Review Dataset](https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt) list. The chosen dataset for this analysis is the [Book dataset](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Books_v1_02.tsv.gz!) (1 of 3).

## Extract, Transform, Load (ETL)
Using PySpark, the book dataset is extracted into four dataframes: customers_df, 

Data Schema
```
CREATE TABLE review_id_table (
  review_id TEXT PRIMARY KEY NOT NULL,
  customer_id INTEGER,
  product_id TEXT,
  product_parent INTEGER,
  review_date DATE -- this should be in the formate yyyy-mm-dd
);

-- This table will contain only unique values
CREATE TABLE products_table (
  product_id TEXT PRIMARY KEY NOT NULL UNIQUE,
  product_title TEXT
);

-- Customer table for first data set
CREATE TABLE customers_table (
  customer_id INT PRIMARY KEY NOT NULL UNIQUE,
  customer_count INT
);

-- vine table
CREATE TABLE vine_table (
  review_id TEXT PRIMARY KEY,
  star_rating INTEGER,
  helpful_votes INTEGER,
  total_votes INTEGER,
  vine TEXT,
  verified_purchase TEXT
);
```


## Results

- no vine paid
-  all that weere filtered were not paid
- This was a dataset that had 2 others.. need to examine the other 2 datasets to review if there were any other..
- a dataset of 3 million and became fitlered to 40oK that are helpful reviews
- 

## Summary



