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

## The customers_table DataFrame

To create the `customers_table`, use the code in the `Amazon_Reviews_ETL_starter_code.ipynb` file and follow the steps below to aggregate the reviews by `customer_id`.

   - Use the `groupby()` function on the `customer_id` column of the DataFrame I created in Step 7.

   - Count all the customer ids using the `agg()` function by chaining it to the `groupby()` function. After I use this function, a new column will be created, `count(customer_id)`.

   - Rename the `count(customer_id)` column using the` withColumnRenamed()` function so it matches the schema for the `customers_table` in pgAdmin.

   - The final customers_table DataFrame should look like this:

![image](https://user-images.githubusercontent.com/112348240/216742599-847396df-7dfe-4d4f-a340-f5f8f09efda2.png)

## The products_table DataFrame

To create the `products_table`, use the `select()` function to select the `product_id` and `product_title`, then drop duplicates with the `drop_duplicates()` function to retrieve only `unique product_ids`. Refer to the code snippet provided in the `Amazon_Reviews_ETL_starter_code.ipynb` file for assistance.

The final `products_table` DataFrame should look like this:

![image](https://user-images.githubusercontent.com/112348240/216742611-51fec4f8-e2a5-4902-987e-4928f7a760e7.png)

## The review_id_table DataFrame

To create the `review_id_table`, use the `select()` function to select the columns that are in the `review_id_table` in pgAdmin (as shown in the following image), and convert the `review_date` column to a date using the code snippet provided in the `Amazon_Reviews_ETL_starter_code.ipynb` file.

The final `review_id_table` DataFrame should look like this:

![image](https://user-images.githubusercontent.com/112348240/216742626-a8f47ec6-7a96-430b-a229-30b360c82254.png)

## The vine_table DataFrame
To create the `vine_table`, use the `select()` function to select only the columns that are in the `vine_table` in pgAdmin (as shown in the following image).

The final `vine_table` DataFrame should look like this:

![image](https://user-images.githubusercontent.com/112348240/216742645-80b2a145-bcda-44b6-a162-6f917c8d0e03.png)

**Screenshot for the code when Load the DataFrames that correspond to tables in pgAdmin**

![image](https://user-images.githubusercontent.com/112348240/216742684-d7389ece-2c9c-4742-9948-b826e7820a98.png)

# Deliverable 2: Determine Bias of Vine Reviews 

Using my knowledge of PySpark, Pandas, or SQL, I’ll determine if there is any bias towards reviews that were written as part of the Vine program. For this analysis, I'll determine if having a paid Vine review makes a difference in the percentage of 5-star reviews.

Using either PySpark, Pandas, or SQL, follow the instructions below to complete Deliverable 2.

1. Filter the data and create a new DataFrame or table to retrieve all the rows where the `total_votes` count is equal to or greater than 20 to pick reviews that are more likely to be helpful and to avoid having division by zero errors later on. 

![image](https://user-images.githubusercontent.com/112348240/216742723-6fb6fec4-faa7-4f47-a598-8310a61abae9.png)

![image](https://user-images.githubusercontent.com/112348240/216742742-f449d48a-820e-434e-a466-a6c530554aef.png)

2. Filter the new DataFrame or table created in Step 1 and create a new DataFrame or table to retrieve all the rows where the number of `helpful_votes` divided by `total_votes` is equal to or greater than 50%.
    - If I use the SQL option below, I’ll need to cast your columns as floats using `WHERE CAST(helpful_votes AS FLOAT)/CAST(total_votes AS FLOAT) >=0.5`.

![image](https://user-images.githubusercontent.com/112348240/216742750-746555ff-1c4c-4b78-80d3-9daba47de399.png)

3. Filter the DataFrame or table created in Step 2, and create a new DataFrame or table that retrieves all the rows where a review was written as part of the Vine program (paid), `vine == 'Y'`.

![image](https://user-images.githubusercontent.com/112348240/216742967-0d2c92e6-bbf6-4c9b-9ec9-9fd336f51a1f.png)

4. Repeat Step 3, but this time retrieve all the rows where the review was not part of the Vine program (unpaid), `vine == 'N'`.

![image](https://user-images.githubusercontent.com/112348240/216743089-c5e1d558-b758-409f-bcd3-ab76b24d5ae4.png)
  
5. Determine the total number of reviews, the number of 5-star reviews, and the percentage of 5-star reviews for the two types of review (paid vs unpaid).

**Total number of reviews**

![image](https://user-images.githubusercontent.com/112348240/216845394-7513f395-0d59-449b-902f-2a7307677598.png)

**Total helpul vine reviews Vine == 'Y'**

![image](https://user-images.githubusercontent.com/112348240/216845583-02cca5ef-84e0-4539-aaec-c7bb9a4e60a5.png)

**Total helpul vine reviews Vine == 'N'**

![image](https://user-images.githubusercontent.com/112348240/216845730-0b715a2f-e85c-4eeb-9bcd-223ea241a107.png)

**Total helpul vine reviews Vine == 'Y' on 5-Stars reviews**
![image](https://user-images.githubusercontent.com/112348240/216845791-57deffb3-3bd7-4090-a369-5fbce36c34fb.png)

**Total helpul vine reviews Vine == 'N' on 5-Stars reviews**
![image](https://user-images.githubusercontent.com/112348240/216845768-db9053ff-eb61-4f71-b5c5-4e9527283347.png)

**Percentage of Vine reviews were 5 stars**
![image](https://user-images.githubusercontent.com/112348240/216845813-466fe467-0567-4153-bc7c-66a9b1e7f914.png)

**Percentage of non-Vine reviews were 5 stars**
![image](https://user-images.githubusercontent.com/112348240/216845850-782e5658-694b-4ad2-8159-b6aca73801f6.png)

## Using PySpark
1. Create a new Google Colab Notebook, and name it `Vine_Review_Analysis`
2. Extract the dataset you used in Deliverable 1.
3. Recreate the `vine_table`, and perform my analysis using the steps above.
4. Export my `Vine_Review_Analysis` Google Colab Notebook as an `ipynb` file, and save it to your Amazon_Vine_Analysis GitHub repository.

# Deliverable 3: A Written Report on the Analysis

# **Overview of the analysis**:

> Analyzing Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

# **Results**: 
    - How many Vine reviews and non-Vine reviews were there? 
      We have a 61 total Vine Reviews and non-Vine reviews are 28278
       
    - How many Vine reviews were 5 stars?
      We have 20
      
    - How many non-Vine reviews were 5 stars?
      We have 15686
      
    - What percentage of Vine reviews were 5 stars? 
      The Percentage Vine reviews is 32.78688524590164
      
    - What percentage of non-Vine reviews were 5 stars?
      The Percentage non-Vine reviews is 55.470683923898434
      
# **Summary**: 
   Based on the results is a positivity bias since for reviews in the Vine program. So, this is reflected on the higher percentage (32.79%) of 5-star Vine reviews compared to the non-Vine reviews (55.47%).  
   One additional analysis that could be done to support this statement is to compare the average rating of Vine reviews and non-Vine reviews. With this extra analysis will give a much clear understanding of the overall difference in the quality of the reviews between the two groups.
















# **SOURCES:**
https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Grocery_v1_00.tsv.gz

- AWS Console

- pgAdmin 4

- Google Colab

# **MODULE 17 Challenge**

My link github page: https://gasconma1960.github.io/Amazon_Vine_Analysis/

by **Marisol Gascon Linarez**

**UCF Bootcamp Data Visualization and Analytics** 
