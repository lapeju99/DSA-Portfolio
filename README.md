# DSA-Portfolio

This is where I started my portfolio building while taking Data Analysis class.

I learnt quite a lot from Excel to SQL to Power BI and now portfolio building

This Project is on Kultra Mega Stores and Palmorial Company

## Project Topic: Kultra Mega Stores Inventory
## Project Overview
This Data Analysis project ais to generate insights into sales performance of KMS over 3 years. By analysing various parameters in the data received we seek to gather enough insights to make reasonable desicions which then enables us to tell compelling stories around our data from the insight gotten and to know the best performance from our data

### Data Source
[KMS Sql Case Study.csv](https://github.com/user-attachments/files/21321932/KMS.Sql.Case.Study.csv)
[Order_Status.csv](https://github.com/user-attachments/files/21321937/Order_Status.csv)



## 💻 Tools & Technologies

- **SQL Server Management Studio (SSMS)** (Data querying, transformation and Analysis)
- **GitHub** (project hosting)



  ## 📁 Files Included

| File Name                              | Description                             |
|----------------------------------------|-----------------------------------------|
[KMS Sql Case Study.csv](https://github.com/user-attachments/files/21323353/KMS.Sql.Case.Study.csv) |Data for KMS including sales|
[Order_Status.csv](https://github.com/user-attachments/files/21323358/Order_Status.csv) | Order status for items|



## Questions

## 1. Top Product Category by Sales
Product Category with the Highest Sales:
Based on total sales aggregated from Row_ID, the Technology category generated the highest revenue.


## SQL Insight:

SELECT Product_Category, SUM(DISTINCT Row_ID) AS TotalSales
FROM [dbo].[KMS Sql Case Study]
GROUP BY Product_Category
ORDER BY TotalSales DESC;


## Question 2  Top & Bottom 3 Regions by Sales

### Top 3 Regions by Sales:
West, Ontario, and Prairie led in total revenue.

### Bottom 3 Regions by Sales:
Nunavut, NorthWest Territories, and Yukon recorded the lowest sales.


SELECT TOP 3 Region, SUM(DISTINCT Sales) AS TotalSales
FROM [dbo].[KMS Sql Case Study]
GROUP BY Region
ORDER BY TotalSales DESC;


SELECT TOP 3 Region, SUM(DISTINCT Sales) AS TotalSales
FROM [dbo].[KMS Sql Case Study]
GROUP BY Region
ORDER BY TotalSales ASC;


## Question 3
 Appliance Sales in Ontario
Ontario saw significant sales in the Appliances sub-category within the Technology category.
### Total sales was 202346.84

SELECT Region, Product_Sub_Category, SUM(Sales) AS TotalSales
FROM [dbo].[KMS Sql Case Study]
WHERE Region = 'Ontario' AND Product_Sub_Category = 'Appliances'
GROUP BY Region, Product_Sub_Category
ORDER BY TotalSales DESC;



## Question 4 
Advise the management of KMS on what to do to increase the revenue from the bottom
10 customers

### Answer: 
1. They should buy in large quantities to make more profits
2. The Shipping cost is high for thee customers and should therefore use cheaper shipping options
3. They should avoid high discounts on low- quality orders.

Select top 10 Customer_Name, SUM(Sales) AS TotalSales
from [dbo].[KMS Sql Case Study]
group by Customer_Name
order by TotalSales asc;




## Question 5

KMS incurred the most shipping cost using which shipping method?

Most Expensive Shipping Method
### Delivery Truck incurred the highest shipping cost overall at $51,972. 

SELECT TOP 5 Ship_Mode, SUM(Shipping_Cost) AS TotalShipping_Cost
FROM [dbo].[KMS Sql Case Study]
GROUP BY Ship_Mode
ORDER BY TotalShipping_Cost DESC;

## Question 6:
Who are the most valuable customers, and what products or services do they typically 
purchase? 
Top customers are those with the highest cumulative spend.
### They are Emily Phan, Deborah Brumfield, Dennis Kane

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


## Question 7

Which small business customer had the highest sales?

### Dennis Kane made the highest sales among small business customers

SELECT TOP 1 Customer_Segment, Customer_Name, SUM(Sales) AS TotalSales
FROM [dbo].[KMS Sql Case Study]
WHERE Customer_Segment = 'Small Business'
GROUP BY Customer_Segment, Customer_Name
ORDER BY TotalSales desc


## Question 8:

Which Corporate Customer placed the most number of orders in 2009 – 2012?

### Adam Hart placed the most orders between 2009-2012.

SELECT TOP 1 Customer_Name, COUNT(DISTINCT Order_ID) AS Number_of_Orders
FROM [dbo].[KMS Sql Case Study]
WHERE customer_Segment = 'Corporate'
AND Order_Date BETWEEN '2009-01-01' AND '2012-12-31'
GROUP BY Customer_Name
ORDER BY Number_of_Orders DESC;


## Question 9:
Which consumer customer was the most profitable one?

### Emily Phan was the most profitable customer.

SELECT TOP 1
[Customer_Name], SUM(Profit) AS Total_Profit
FROM [dbo].[KMS Sql Case Study]
WHERE [Customer_Segment] = 'Consumer'
GROUP BY [Customer_Name]
ORDER BY Total_Profit DESC;

## Question 10:
Which customer returned items, and what segment do they belong to?

### Customers returned items in all segments but most especially in corporate and small business

SELECT DISTINCT TOP 10 o.[Order_ID], o.[Customer_Name], o.[Customer_Segment]
FROM [dbo].[KMS Sql Case Study] o
JOIN [dbo].[OrderStatus] r 
ON o.[Order_ID] = r.[Order_ID]
WHERE r.Status = 'Returned';

## Question 11:
If the delivery truck is the most economical but the slowest shipping method and 
Express Air is the fastest but the most expensive one, do you think the company 
appropriately spent shipping costs based on the Order Priority? Explain your answer

SELECT [Order_Priority], [Ship_Mode],
COUNT([Order_ID]) AS OrderCount,
ROUND(SUM(Sales - Profit), 2) AS EstimatedShippingCost,
AVG(DATEDIFF(day, [Order_Date], [Ship_Date])) AS AvgShipDays
FROM [dbo].[KMS Sql Case Study]
GROUP BY [Order_Priority], [Ship_Mode]
ORDER BY [Order_Priority], [Ship_Mode] DESC;

### I don't think the company spent apprioipriately because customers take proirity very important and could impact their next buy.










# 🧠 Palmoria Group HR Analytics Report

This Power BI project explores HR data from Palmoria Group — a Nigerian manufacturing company — with the goal of uncovering insights related to gender representation, salary compliance, performance ratings, and bonus allocation. The analysis leverages real organizational data to support strategic decision-making in Human Resources.


## 📌 Project Objectives

- Identify and address gender disparities in employment distribution.
- Evaluate compliance with minimum salary regulations.
- Analyze bonus distribution using performance ratings and department-level rules.
- Calculate average ratings by gender and department.
- Determine the total financial commitment to employees, including bonuses.


## 📊 Key Analysis Areas

### 1. **Gender Distribution by Region & Department**
- Visual breakdown of employees by gender across regions and departments.
- Highlighted departments with gender imbalance.

### 2. **Performance Ratings Analysis**
- Comparison of average ratings between male, female, and non-disclosed genders.
- Performance trends across departments and gender categories.

### 3. **Salary Compliance**
- Identified employees below the ₦90,000 minimum salary threshold.
- Summary by department and region for salary violation analysis.

### 4. **Bonus Allocation Model**
- Bonus calculated using department-based percentages tied to performance ratings.
- DAX measures used to compute accurate bonuses per employee.
- Separate visuals show bonus trends by gender and department.

### 5. **Total Compensation Report**
- A complete view of employee compensation (Salary + Bonus).
- Aggregate views:
  - Per employee
  - Per region
  - Company-wide
 

## 💻 Tools & Technologies

- **Microsoft Power BI** (Data Modeling, DAX, Visualizations)
- **Power Query** (Data Cleaning and Transformation)
- **DAX Measures** for custom calculations
- **GitHub** (project hosting)


  ## 📁 Files Included

| File Name                              | Description                             |
|----------------------------------------|-----------------------------------------|
|[Palmoria Visualization.pdf](https://github.com/user-attachments/files/21321718/Palmoria.Visualization.pdf)             | Power BI report                         |
|[Palmoria Group emp-data (1).csv](https://github.com/user-attachments/files/21321643/Palmoria.Group.emp-data.1.csv)         | Employee details including salary       |
|[Palmoria Group Bonus Rules.xlsx](https://github.com/user-attachments/files/21321649/Palmoria.Group.Bonus.Rules.xlsx)    | Bonus rules per department & rating     |
| `README.md`                            | Project documentation                   |


## 📸  Visualizations
[Palmoria Visualization.pdf](https://github.com/user-attachments/files/21321711/Palmoria.Visualization.pdf)


[Palmoria Visualization.pdf](https://github.com/user-attachments/files/21321589/Palmoria.Visualization.pdf)


## Insights

### 1. Gender Distribution
Insight:
The organization shows a gender imbalance, with male employees significantly outnumbering female employees across all regions.

Region A had the highest gender skew, with over 70% male representation.

Female employees were most concentrated in departments like Admin and Customer Service, while departments like Engineering and Production were male-dominated.

A small percentage of employees did not disclose their gender. These were categorized as “Undisclosed” for analysis consistency.

Recommendation:
Targeted recruitment drives focused on increasing female participation, especially in technical departments.


###  2. Ratings by Gender
Insight:

Male employees were more frequently rated as "Good" and "Very Good", while female employees received a higher proportion of "Average" and "Poor" ratings.

The data suggests possible unconscious bias or unequal access to performance-improving opportunities.

Recommendation:
Audit the performance appraisal system and training access. Introduce anonymous peer reviews and manager calibration sessions.


###  3. Gender Pay Gap Analysis
Insight:

A gender pay gap exists across multiple departments and regions.

Male employees earn higher average salaries than female counterparts in Engineering, Production, and Operations.

The gap is smallest in Admin and Customer Service, where female representation is higher.

Recommendation:
Conduct structured pay reviews and develop an equitable salary band system by job role, not gender. Transparency in promotion and pay decisions should be improved.


### 4. Salary Compliance & Pay Distribution
Insight:
The company is non-compliant with the new minimum wage regulation of $90,000:

34% of employees earn below the regulatory minimum, most of whom are in Region C and Support departments.

The salary distribution shows a concentration in the $60,000 – $80,000 range, with fewer employees in the top band.

Recommendation:
Immediate salary reviews for affected employees. Adjust salary structures to meet compliance, especially in vulnerable departments.

Bonus Insight:

Salary band distribution visualization revealed potential compression issues, where high-performing staff were stuck in mid-tier salary bands.


### 5. Bonus Allocation Based on Performance
Insight:

Annual bonus allocations were computed using department-specific bonus percentages based on employee performance ratings.

The total bonus paid across the company was approximately $68.04bn.

Employees rated as "Very Good" in departments like Sales and Engineering received the highest bonuses.

Top 3 Departments by Total Bonus Paid:

Engineering

Sales

Operations

Recommendation:
Use bonus allocation as a motivation strategy but monitor fairness. Ensure managers are not skewing ratings to manipulate bonus distribution.

### Total Compensation Analysis
Insight:

By combining base salary and bonus, a new view of Total Compensation was created.

Some employees who earned modest salaries benefited significantly from performance bonuses.

Region A had the highest average total compensation, while Region C lagged behind.

Recommendation:
Use Total Compensation as a retention metric and benchmark future compensation strategies.



## Author
Olapeju Folajin
Data Analyst


