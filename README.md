# Customer-Data

# Introduction Overview 

This project involves analyzing customer data for a subscription service to identify 
segments and trends. The goal was to understand customer behavior, track subscription types, 
and identify key trends in cancellations and renewals. The final deliverable was a Power BI 
dashboard that presented my analysis.

# Tools Used 

# MS Excel

- Duplicates were found in the data and deleted.

- Customer data was analyzed using pivot tables to find subscription patterns.
  
- The average subscription duration was calculated using pivot tables and the most popular 
subscription types was identified.

# SQL 

I executed queries to retrieve:

- Retrieve the total number of customers from each region.
  
- Find the most popular subscription type by the number of customers.
- Find customers who canceled their subscription within 6 months.
- Calculate the average subscription duration for all customers.
- Find customers with subscriptions longer than 12 months.
- Calculate total revenue by subscription type.
- Find the top 3 regions by subscription cancellations.
- Find the total number of active and canceled subscriptions.

  # Power BI

  Power BI dashboard was created that visualizes key customer segments, 
cancellations, and subscription trends. Slicers were included for interactive analysis.

# Discussion/Result 

The total number of customers was 34K. The total revenue generated was 68M. The most popular subscription type was Basic, with a total of 16,921 customers. The Eastern region had the highest number of customers with a total of 8,488. No customer canceled their subscription within 6 months neither was there any customer whose suscription was longer than 12 months. 
The revenue generated from Basic subscription was 33,776,735. The total number of active and canceled subscriptions are, 18,612 and 15,175. 

# MS Excel 

![CUSTOMER DATA](https://github.com/Abasianam/Customer-Data/blob/main/CUSTOMER%20DATA%20.jpg)

# SQL

The following queries were executed to extract key insights

- Retrieve the total number of customers from each region
  
Select region, count (customerID) as Total_No_of_Customers
from [dbo].[CAPSTONE DATA2]
group by region
order by Total_No_of_Customers DESC

- Find the most popular subscription type by the number of customers
  
select Top 1 subscriptiontype, count (customerid) as Total_No_of_Customers
from [dbo].[CAPSTONE DATA2]
group by subscriptiontype
order by Total_No_of_Customers desc

- Find customers who canceled their subscription within 6 months
  
select customerid, customername, subscriptionstart, subscriptionend
from [dbo].[CAPSTONE DATA2]
where canceled =  1
AND DATEDIFF (month, subscriptionstart, subscriptionend) <= 6;

- Calculate the average subscription duration for all customers
  
select AVG (DATEDIFF(month, subscriptionstart, subscriptionend))
as AVG_Duration
from [dbo].[CAPSTONE DATA2]

- Find customers with subscriptions longer than 12 months
  
select customerid, customername, subscriptionstart, subscriptionend
from [dbo].[CAPSTONE DATA2]
where datediff (month, subscriptionstart, subscriptionend) > 12;

- Calculate total revenue by subscription type
  
select subscriptiontype, sum (revenue) as Total_Revenue
from  [dbo].[CAPSTONE DATA2]
group by subscriptiontype
order by Total_Revenue desc

- Find the top 3 regions by subscription cancellations
  
select top 3 region, count (customerid) as Cancellation_Count
from [dbo].[CAPSTONE DATA2]
where canceled = 1
group by region 
order by Cancellation_Count

- Find the total number of active and canceled subscriptions
  
select sum(case when canceled= 1 then 1 else 0 end) as CanceledSubscriptions,
sum (case when canceled = 0 then 1 else 0 end) as ActiveSubscriptions
from [dbo].[CAPSTONE DATA2];

# Power BI

Below are pictorial representations of the customer data:


![POWER BI VISUALISATION 2](https://github.com/Abasianam/Customer-Data/blob/main/POWER20%BI20%VISUALISATION20%220%.jpg)



![Basic subscription Type](https://github.com/Abasianam/Customer-Data/blob/main/Basic20%subscription20%type.jpg)



![Eastern region](https://github.com/Abasianam/Customer-Data/blob/main/Eastern20%region20%.jpg)
