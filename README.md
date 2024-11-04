# CAPSTONE DATA ANALYSIS PROJECT 
## TITLE: CUSTOMER DATA
### Project Overview 
The Data Analysis project aims to explore and use customer data to idetify trends, patterns, and insights that can drive better business decisions. The analysis covers various aspects such as sales performance, customer behaviour, product trends and geographic distribution. The goal is to help businesses make data-driven desicions by providing a comprehensive understanding of their sales data.

### Data Sources 
The primary data sources used is excel worksheet, which is an open-source data.

### Tools Used
- Excel spreadsheet for data cleaning and analysis
- Structured Query Language(SQL) for querying the data
- Power Business Intelligence(Power BI) for visualizing the data set


### CONTENT OF THE CUSTOMER DATA EXCEL SPREADSHEET
- CustomerID
- Customer Name
- Region
- Subscription Type
- Subscription Start
- Subscription End
- Canceled
- Revenue
- Subscription Duration

We have been tasked with analyzing the customer of a retail store. Let the retail store be known as Melewis Boutique. 
The sales performance includes:
- Analyze customer data using pivot tables to find subscription patterns.
- Calculate the average subscription duration and identify the most popular subscription types.
- Create any other interesting reports.

We will also be using pivot tables and pie chart to summarize the total sales by product, region, and month. Furthermore, after analyzing this data set on excel worksheet, we will be importing into Structured Query Language(SQL) to run queries on the data and then proceed to Power Business Intelligence(Power BI) for visualization of the data set.
This data set  has a total of 75,001 rows and 8 columns to be worked on and this data set is unclean.

The first step is to clean the data by removing the duplicate in the data set. After cleaning the data set, we are left with 33,788 rows to work with. Then we move on to find the subscription duration for each customer. To find the subscription duration, you subtract the subscription start from the subscription end.


![customer data](https://github.com/user-attachments/assets/421f2ec2-be3a-46da-a39f-7d3621ae1642)


Then find the average subscription duration using the "AVG" function. The average subscription duration is **365.35**

 
 Most popular subscription type was also analyzed using the "sumif" function. The most popular subscription type is the Basic subscription package with the following breakdown:

- Basic    33,776,735 
- Premium	 16,899,064 
- Standard 16,864,376 


![average customer data](https://github.com/user-attachments/assets/d4717078-47b8-4457-ba41-4f5f1c56cc2d)


We also made use of pivot table to find subscription patterns.

![customer pivot](https://github.com/user-attachments/assets/35411438-0252-4f70-b7cb-e6096585a421)

We moved further to find the total revenue made from sales of all subscription package using the "sum" function and the total revenue is  67,540,175 


![revenue customer](https://github.com/user-attachments/assets/7e0b4a07-efa3-4e30-8c38-ac643317991c)


For a much clearer and well defined analysis we analyzed the pivot table in a bar chart with a slicer. 

![customer bar chart](https://github.com/user-attachments/assets/efbd5171-6976-498a-9216-ad4767139977)



## STRUCTURED QUERY LANGUAGE(SQL)
We want to query the customer data set we have been given to analyze. We want to:

- retrieve the total number of customers from each region.
- find the most popular subscription type by the number of customers.
- find customers who canceled their subscription within 6 months.
- calculate the average subscription duration for all customers.
- find customers with subscriptions longer than 12 months.
- calculate total revenue by subscription type.
- find the top 3 regions by subscription cancellations.
- find the total number of active and canceled subscriptions.


The first step is to create a database where all the data will be queried. 

