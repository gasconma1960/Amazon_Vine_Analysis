# Amazon_Vine_Analysis

![image](https://user-images.githubusercontent.com/112348240/216741112-8b3b8ff7-0ba2-4707-b83a-7547fe382c30.png)

# Background
Since I work with Jennifer on the SellBy project was so successful, I’ve been tasked with another, larger project: analyzing Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

In this project, I’ll have access to approximately 50 datasets. Each one contains reviews of a specific product, from clothing apparel to wireless products. I’ll need to pick one of these datasets and use PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Next, I’ll use PySpark, Pandas, or SQL to determine if there is any bias toward favorable reviews from Vine members in your dataset. Then, I’ll write a summary of the analysis for Jennifer to submit to the SellBy stakeholders.

# **Deliverable 1: Perform ETL on Amazon Product Reviews** 

Using my knowledge of the cloud ETL process, I’ll create an AWS RDS database with tables in pgAdmin, pick a dataset from the Amazon Review datasets Links to an external site., and extract the dataset into a DataFrame. I'll transform the DataFrame into four separate DataFrames that match the table schema in pgAdmin. Then, I'll upload the transformed data into the appropriate tables and run queries in pgAdmin to confirm that the data has been uploaded.

Follow the instructions below to complete Deliverable 1.

1. From the following Amazon Review datasets Links to an external site., pick a dataset that I would like to analyze. All the datasets have the same schemata, as shown in this image:


  I picked this dataset: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Grocery_v1_00.tsv.gz
  
