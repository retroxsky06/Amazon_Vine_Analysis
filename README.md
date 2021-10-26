# Amazon Vine Analysis

## Project Overview
The purpose of this project is to analyze Amazon customer reviews of the paid Amazon Vine program, which is a service that allows manufacturers and publishers to receive reviews for their products. Utilizing PySpark, the ETL process will extract the dataset, transform the data and connect to an AWS RDS instance.  The transformed data will then be loaded into pgAdmin.  Lastly, Pandas is used to determine if there is any bias towards favorable reviews from Vine members in the dataset.  

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

For the final stages of the analysis, the dataset was filtered to create two additional dataframes which would yield the following metrics for Amazon vine (paid) and non-vine (unpaid) reviews:
- total number of reviews
- total number of 5-star reviews
- percentage of reviews that were 5-stars

![fig3](https://github.com/retroxsky06/Amazon_Vine_Analysis/blob/main/images/totals_reviews.png)

## Results
The Book dataset provided the following results:
- There are 0 Vine reviews.
- There are 403,807 non-Vine reviews.
  - 242,889 non-Vine reviews gave 5-stars.
  - 60% of non-Vine reviews were 5-stars.


## Summary
Based on this analysis, there seems to be little to no positvity bias as there is 0 Vine (paid customers) reviews, while 60% of non-Vine (unpaid customers) reviews rated various books with 5-stars. It is surprising to discover that there were 0 Vine reviews in a dataset that initially began with approximately 3.1 million reviews; however, to ensure that the dataset was not solely holding non-Vine reviews, an additional dataframe was created on the vine_df.  It was discovered that there were 2 vine reviews; however, due to the filters during the analysis process, they were not displayed.  

#### Dataframe with no filters
![fig4](https://github.com/retroxsky06/Amazon_Vine_Analysis/blob/main/images/vine_df_paid.png)

## Recommendations for further analysis
From the Amazon Review Dataset, there were three book datasets while the majority  had one of its kind. As the dataset for this analysis did not have significant vine reviews, it may be helpful for future analysis to combine all three book datasets to better determine if there is any indication of positivity bias.
