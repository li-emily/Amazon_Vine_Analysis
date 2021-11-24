# Amazon_Vine_Analysis

## Overview
### Purpose
>We have tasked with another, larger project: analyzing Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

- Become familiar working with PySpark in Google Colab Notebook.
- Perform the ETL process to extract and transform a dataset.
- Practice using Amazon Web Services, particularly RDS and S3. 
- Connect to an AWS RDS instance, and load the transformed data into pgAdmin.
- Use PySpark to determine if there is any bias in dataset.


### Resources
* Languages and Packages: PySpark (Apache Spark in Python), Java, Postgres, SQL
* Interfaces: Google Colab Notebook, pgAdmin 4, PostgreSQL, Amazon Web Services (RDS)
* Data Source: [Amazon US Reviews (wireless products)](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Wireless_v1_00.tsv.gz)

## Results
### Deliverable 1: Perform ETL on Amazon Product Reviews

Extraction of Amazon wireless products reviews on the US site from AWS S3 bucket to PySpark. Creation of tables from the dataframe through transformations. Finally, connect to pgAdmin4 using AWS RDS and load data. 

Customer table             |  Loading into pgAdmin 4
:-------------------------:|:-------------------------:
![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d1_customers.png) |  ![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d1_customers_load.png)


---

Product table             |  Loading into pgAdmin 4
:-------------------------:|:-------------------------:
![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d1_products.png) | ![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d1_products_load.png)

---

Reviews table             |  Loading into pgAdmin 4
:-------------------------:|:-------------------------:
![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d1_review.png) | ![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d1_review_id_load.png)

---

Vine program table             |  Loading into pgAdmin 4
:-------------------------:|:-------------------------:
![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d1_vine.png) | ![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d1_vine_load.png)

### Deliverable 2: Determine Bias of Vine Reviews

Filter vine dataframe to create tables that grab rows with 20 or more votes, 50%+ helpful votes, part of the Vine program (paid), and not part of the Vine program (unpaid), respectively.

![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d2_vine_votes_df.png)

![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d2_helpful_df.png)

![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d2_paid_df.png)

![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d2_unpaid_df.png)

### Looking Deeper:

All of the dataframes counted only reviews that had at least 20 or more votes, with 50% or more of those votes marked as helpful. There was a total of 30,765 5* reviews given.

![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d2_5_reviews.png)

![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d2_5_paid.png)

![image](https://raw.githubusercontent.com/li-emily/Amazon_Vine_Analysis/main/Resources/Images/d2_5_unpaid.png)

Vine (paid) Reviews:

- 613 paid reviews overall
- 222 5* reviews
- 36.2% of paid reviews were 5* ratings

Non-vine (unpaid) reviews:

- 64,968 unpaid reviews overall
- 30,543 5* reviews
- 47% of unpaid reviews were 5* ratings

## Summary

Overall, it does not seem like there is an obvious positivity bias looking at these reviews in the Vine program. In fact, unpaid reviews actually had a higher 5* rating percentage, 36.2% for paid versus 47% for unpaid.

If we wished to delve deeper into this, we could take other statistics such as mean, median, mode, as well as graph distribution to have a better idea. For instance, perhaps paid reviews would give more 4* ratings. Additionally, we could also test the data with a lighter 'helpful rating' parameter, or remove that altogether. This does runs the risk of low-effort reviews being taken into account, but the 'verified purchase' column could help filter these out.
