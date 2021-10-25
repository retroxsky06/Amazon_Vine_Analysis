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
Using PySpark, the book dataset is extracted into four dataframes: customers_df, products_df, review_id_df, and vine_df. Once connected to the AWS RDS instance, the four dataframes were then written into their existing respective tables in pgAdmin. The ETL process can be found [here](https://github.com/retroxsky06/Amazon_Vine_Analysis/blob/main/Amazon_Reviews_ETL.ipynb). The password and url that were used to configure the settings for RDS have been removed for security.

## Data Analysis with Pandas
To determine if there is any bias toward favorable reviews from Vine members in the book dataset, Pandas is used to filter and create new dataframes.  This section of the analysis can be found [here](https://github.com/retroxsky06/Amazon_Vine_Analysis/blob/main/Vine_Review_Analysis.ipynb).  

For the initial filter (filter #1), the vine_df is filtered to retrieve all rows where the total votes is equal or greather than 20.

![fig1](https://github.com/retroxsky06/Amazon_Vine_Analysis/blob/main/images/filtered_df.png)

A second filter (filter #2) is then used on the initial filter (filter #1) to create a new dataframe that retrieves all rows where
the number of helpful votes divided by total votes is equal to or greater than 50%.

![fig2](https://github.com/retroxsky06/Amazon_Vine_Analysis/blob/main/images/fifty_percent_helpful_df.png)

## Results

- no vine paid
-  all that weere filtered were not paid
- This was a dataset that had 2 others.. need to examine the other 2 datasets to review if there were any other..
- a dataset of 3 million and became fitlered to 40oK that are helpful reviews
- 

## Summary



