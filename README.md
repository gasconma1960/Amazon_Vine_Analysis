# Amazon_Vine_Analysis

![image](https://user-images.githubusercontent.com/112348240/216741112-8b3b8ff7-0ba2-4707-b83a-7547fe382c30.png)

# Background
Since I work with Jennifer on the SellBy project was so successful, I’ve been tasked with another, larger project: analyzing Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

In this project, I’ll have access to approximately 50 datasets. Each one contains reviews of a specific product, from clothing apparel to wireless products. I’ll need to pick one of these datasets and use PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Next, I’ll use PySpark, Pandas, or SQL to determine if there is any bias toward favorable reviews from Vine members in your dataset. Then, I’ll write a summary of the analysis for Jennifer to submit to the SellBy stakeholders.

# **Deliverable 1: Perform ETL on Amazon Product Reviews** 

Using my knowledge of the cloud ETL process, I’ll create an AWS RDS database with tables in pgAdmin, pick a dataset from the Amazon Review datasets Links to an external site., and extract the dataset into a DataFrame. I'll transform the DataFrame into four separate DataFrames that match the table schema in pgAdmin. Then, I'll upload the transformed data into the appropriate tables and run queries in pgAdmin to confirm that the data has been uploaded.

Follow the instructions below to complete Deliverable 1.

1. From the following Amazon Review datasets Links to an external site., pick a dataset that I would like to analyze. All the datasets have the same schemat.I picked this dataset: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Grocery_v1_00.tsv.gz
![image](https://user-images.githubusercontent.com/112348240/216742348-29ccedee-019d-4a02-a452-1794ffbabf77.png)


2. Create a new database with Amazon RDS just as you did in this module.

3. In pgAdmin, create a new database in my Amazon RDS server that I just create.

4. Download the `challenge_schema.sql` file to my computer.

5. In pgAdmin, run a new query to create the tables for your new database using the code from the `challenge_schema.sql` file.
    - After I run the query, I should have the following four tables in my database: `customers_table`, `products_table`, `review_id_table`, and `vine_table`.
6. Download the `Amazon_Reviews_ETL_starter_code.ipynb` file, then upload the file as a Google Colab Notebook, and rename it `Amazon_Reviews_ETL`.
7. First extract one of the review datasets, then create a new DataFrame.
8. Next, follow the steps below to transform the dataset into four DataFrames that will match the schema in the pgAdmin tables:


![image](https://user-images.githubusercontent.com/112348240/216742599-847396df-7dfe-4d4f-a340-f5f8f09efda2.png)

![image](https://user-images.githubusercontent.com/112348240/216742611-51fec4f8-e2a5-4902-987e-4928f7a760e7.png)

![image](https://user-images.githubusercontent.com/112348240/216742626-a8f47ec6-7a96-430b-a229-30b360c82254.png)

![image](https://user-images.githubusercontent.com/112348240/216742645-80b2a145-bcda-44b6-a162-6f917c8d0e03.png)

![image](https://user-images.githubusercontent.com/112348240/216742684-d7389ece-2c9c-4742-9948-b826e7820a98.png)

![image](https://user-images.githubusercontent.com/112348240/216742723-6fb6fec4-faa7-4f47-a598-8310a61abae9.png)

![image](https://user-images.githubusercontent.com/112348240/216742742-f449d48a-820e-434e-a466-a6c530554aef.png)

![image](https://user-images.githubusercontent.com/112348240/216742750-746555ff-1c4c-4b78-80d3-9daba47de399.png)

![image](https://user-images.githubusercontent.com/112348240/216742967-0d2c92e6-bbf6-4c9b-9ec9-9fd336f51a1f.png)

![image](https://user-images.githubusercontent.com/112348240/216743089-c5e1d558-b758-409f-bcd3-ab76b24d5ae4.png)

## The customers_table DataFrame
To create the `customers_table`, use the code in the `Amazon_Reviews_ETL_starter_code.ipynb` file and follow the steps below to aggregate the reviews by `customer_id`.

   - Use the `groupby()` function on the `customer_id` column of the DataFrame you created in Step 7.

   - Count all the customer ids using the `agg()` function by chaining it to the `groupby()` function. After you use this function, a new column will be created, `count(customer_id)`.

   - Rename the count(customer_id) column using the withColumnRenamed() function so it matches the schema for the customers_table in pgAdmin.

The final customers_table DataFrame should look like this:



# **SOURCES:**
https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Grocery_v1_00.tsv.gz

- AWS Console

- pgAdmin 4

- Google Colab

# **MODULE 17 Challenge**

by **Marisol Gascon Linarez**

**UCF Bootcamp Data Visualization and Analytics** 
