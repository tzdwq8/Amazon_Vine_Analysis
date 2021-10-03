# Amazon Vine Analysis

## Overview
The purpose of this project is to analyze Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products.  For this analysis, we used sports products sold on Amazon.  The dataset can be found at:
  
[Sports Product Reviews](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Sports_v1_00.tsv.gz)

PySpark was used to extract, and then transform, the data to determine if there is any bias toward favorable reviews from Vine members.  This includes determining if having a paid Vine review makes a difference in the percentage of 5-star reviews.

## Results
To perform this analysis, we transformed the dataset by first creating a table with the pertinent columns.  Next, filtered the data to retrieve all the rows where the total votes count is equal to or greater than 20.  This is to pick reviews that are more likely to be helpful and to avoid having division by zero errors later on.  To further refine the data, filtered all the rows where the number of helpful votes divided by total votes is equal to or greater than 50%.  From this data, two DataFrames were created:

### Reviews written as part of the Vine program (paid)

![Paid Reviews](https://user-images.githubusercontent.com/85590155/135738879-9064f9d9-6fec-412b-be42-cb5cca0255b2.PNG)

### Reviews written not a part of the Vine program (unpaid)

![Unpaid Reviews](https://user-images.githubusercontent.com/85590155/135738902-4b00465e-1a0b-4a00-a013-8399c3e89f5d.PNG)

### Analysis
- From the transformed dataset, there were **334** reviews from the Vine program.  Of these, **139** were 5 star reviews which equates to **41.62%**.
- From the transformed dataset, there were **61614** reviews from the unpaid reviewers.  Of these, **32665** were 5 star reviews which equates to **53.02%**.

## Summary
Based upon the data, there does not appear to be any positivity bias for reviews in the Vine program concerning sports products.  This can be concluded due to the percentage of 5 star reviews in the Vine program (41.62%) being less than the percentage of 5 star reviews outside the program (53.02%)  Since the sample data is much smaller for the Vine program, we could analyze additional data to support this statement.  4 star reviews are also positive reviews.  So we can include 4 stars in this analysis to determine if there is any change in the positivity bias for both datasets. 
