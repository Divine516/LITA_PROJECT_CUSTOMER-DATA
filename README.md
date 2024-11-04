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


The first step is to create a database where all the data will be queried. ```SQL CREATE database Capstone_project_customer_data```
Then import the file to be used from excel to the SQL studio. Then ```SQL select* from [dbo].[customer data]``` to view the table.

![real sql](https://github.com/user-attachments/assets/69fb9907-4986-4ccc-9af6-80752aceb5cd)



In the table we have three empty columns which we neede to remove. Then the alter table function and the drop column function was used. ```SQL ALTER TABLE [dbo].[customer data] 
DROP COLUMN column10, column11, column12```

![real sql 2](https://github.com/user-attachments/assets/8250e84b-0f0b-482e-ad1d-964119beda46)


After removing the empty columns, we want to query the data set and :

1. Retrieve the total number of customers from each region : ```SQL select Region, count (CustomerID) as Region_Customers from [dbo].[customer data]
GROUP BY Region ```. 
The total number of customers from each region are:
- North 	8,433
- East	  8,488
- South 	8,446
- West	  8,420
  
![real sql 3](https://github.com/user-attachments/assets/5b1a838a-714c-47a9-88ef-623cda2d83ba)

2. Find the most popular subscription type by the number of customers: ```SQL select SubscriptionType, count (CustomerID) as customer_subscription from [dbo].[customer data]
Group by SubscriptionType
Order by customer_subscription desc```
The most popular subscription is the basic package with a total of 16,921

![real sql 4](https://github.com/user-attachments/assets/de9340d0-bfe1-4cf8-b149-c767779a1363)

3. Find customers who canceled their subscription within 6 months : ```SQL Select *
FROM [dbo].[customer data]
WHERE DATEDIFF( month, SubscriptionStart, SubscriptionEnd) <=6```
No customer canceled their subscription after 6 months.


4. Calculate the average subscription duration for all customers: ```SQL select AVG(DATEDIFF(year, subscriptionStart, SubscriptionEnd)) AS average_subscription
FROM [dbo].[customer data]```
The average subscription is equal to 1

![real sql 5](https://github.com/user-attachments/assets/e6369049-fcc9-4764-b91b-253ff442c15f)


5. Find customers with subscriptions longer than 12 months: ```SQL SELECT CustomerID, SubscriptionType, SubscriptionStart, SubscriptionEnd
FROM [dbo].[customer data]
WHERE DATEDIFF(month, SubscriptionStart, SubscriptionEnd) >12```
There was no customer that had subscription more than 12 months or a year.

6. Calculate total revenue by subscription type: ```SQL SELECT SubscriptionType, SUM(revenue) as total_revenue
FROM [dbo].[customer data]
GROUP BY SubscriptionType```. The total revenue by subscription type:
- Basic	33,776,735
- Premium	16,899,064
- Standard	16,864,376


  ![real sql 6](https://github.com/user-attachments/assets/59b0f7dd-47bb-4205-af36-27c649df986e)



7. Find the top 3 regions by subscription cancellations: ```SQL SELECT Region, count(*) AS canceled_subscription
FROM [customer data]
WHERE canceled = 1
GROUP BY Region
ORDER BY canceled_subscription DESC```. The top 3 regions according to those that canceled subscription in descending order:
- North	5,067
- South	5,064
- West	5,044

![real sql 7](https://github.com/user-attachments/assets/7c151cd8-c5a3-4ed2-9672-9d652e57812d)

![real sql 8](https://github.com/user-attachments/assets/391c9f64-9224-439e-848c-1f26ae4973a8)



8.Find the total number of active and canceled subscriptions: ```SQL SELECT canceled, COUNT(*) AS total_number_of_subscriptions
FROM [customer data]
GROUP BY Canceled```. The total number of active and canceled subscription is 
0 =	18,612
1 =	15,175
Where canceled subscription is 0 and active subscription is 1.

![real sql 9](https://github.com/user-attachments/assets/15e6ae44-f357-4678-a064-31b19f36cf72)




## POWER BI VISUALIZATION
The final stage of this analysis is to visualize our data set so that we can use the output to be able to make better decision regarding the business.





