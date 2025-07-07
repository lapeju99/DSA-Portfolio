# DSA-Portfolio

This is where I started my portfolio building while taking Data Analysis class.

I learnt quite a lot from Excel to SQL to Power BI and now portfolio building

## Project Topic: Kultra Mega Stores Inventory
## Project Overview
This Data Analysis project ais to generate insights into sales performance of KMS over 3 years. By analysing various parameters in the data received we seek to gather enough insights to make reasonable desicions which then enables us to tell compelling stories around our data from the insight gotten and to know the best performance from our data

### Data Source


## Questions

1 Which product category had the highest sales? 


Select * from [dbo].[KMS Sql Case Study]

Select Product_Category, SUM(distinct Row_ID) as TotalSales
from [dbo].[KMS Sql Case Study]
group by Product_category
order by TotalSales desc

Question 2


Select top 3 Region, SUM(Distinct Sales) AS TotalSales
from [dbo].[KMS Sql Case Study]
group by Region
order by TotalSales desc


Select top 3  Region, SUM(Distinct Sales) AS TotalSales
from [dbo].[KMS Sql Case Study]
group by Region
order by TotalSales asc

Question 3

SELECT Region,  Product_Sub_Category, SUM(Sales) AS TotalSales
FROM [dbo].[KMS Sql Case Study]
WHERE Region = 'Ontario'
AND Product_Sub_Category = 'Appliances' 
GROUP BY Region,  Product_Sub_Category
ORDER BY TotalSales desc

Question 4 
Select top 10 Customer_Name, SUM(Sales) AS TotalSales
from [dbo].[KMS Sql Case Study]
group by Customer_Name
order by TotalSales asc


 Question 5

KMS incurred the most shipping cost using which shipping method?

Select top 5 Ship_Mode, SUM(Shipping_Cost) AS TotalShipping_Cost
from [dbo].[KMS Sql Case Study]
group by Ship_Mode
order by TotalShipping_Cost desc

Delivery Truck incurred the most shipping cost.

question 6:
6. Who are the most valuable customers, and what products or services do they typically 
purchase? 

6a

SELECT top 5 Row_ID, Customer_Name, SUM(Sales) AS TotalSpent
FROM [dbo].[KMS Sql Case Study]
GROUP BY Row_ID, Customer_Name
ORDER BY TotalSpent DESC

6b

SELECT TOP 5 [Customer_Name], [Product_Name],
SUM(Sales) AS Total_Sales
FROM [dbo].[KMS Sql Case Study]
GROUP BY [Customer_Name], [Product_Name]
ORDER BY Total_Sales DESC;


Question 7

Which small business customer had the highest sales?

SELECT TOP 1 Customer_Segment, Customer_Name, SUM(Sales) AS TotalSales
FROM [dbo].[KMS Sql Case Study]
WHERE Customer_Segment = 'Small Business'
GROUP BY Customer_Segment, Customer_Name
ORDER BY TotalSales desc


Question 8:

Which Corporate Customer placed the most number of orders in 2009 – 2012?

SELECT TOP 1 Customer_Name, COUNT(DISTINCT Order_ID) AS Number_of_Orders
FROM [dbo].[KMS Sql Case Study]
WHERE customer_Segment = 'Corporate'
AND Order_Date BETWEEN '2009-01-01' AND '2012-12-31'
GROUP BY Customer_Name
ORDER BY Number_of_Orders DESC;

Question 9:
Which consumer customer was the most profitable one?

SELECT TOP 1
[Customer_Name], SUM(Profit) AS Total_Profit
FROM [dbo].[KMS Sql Case Study]
WHERE [Customer_Segment] = 'Consumer'
GROUP BY [Customer_Name]
ORDER BY Total_Profit DESC;

Question 10:Which customer returned items, and what segment do they belong to?

SELECT DISTINCT TOP 10 o.[Order_ID], o.[Customer_Name], o.[Customer_Segment]
FROM [dbo].[KMS Sql Case Study] o
JOIN [dbo].[OrderStatus] r 
ON o.[Order_ID] = r.[Order_ID]
WHERE r.Status = 'Returned';

11. If the delivery truck is the most economical but the slowest shipping method and 
Express Air is the fastest but the most expensive one, do you think the company 
appropriately spent shipping costs based on the Order Priority? Explain your answer

SELECT [Order_Priority], [Ship_Mode],
COUNT([Order_ID]) AS OrderCount,
ROUND(SUM(Sales - Profit), 2) AS EstimatedShippingCost,
AVG(DATEDIFF(day, [Order_Date], [Ship_Date])) AS AvgShipDays
FROM [dbo].[KMS Sql Case Study]
GROUP BY [Order_Priority], [Ship_Mode]
ORDER BY [Order_Priority], [Ship_Mode] DESC;

Idon't think the company spent apprioipriately because customers take proirity very important and could impact their next buy.
