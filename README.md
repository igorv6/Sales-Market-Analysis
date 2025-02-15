# Sales-Market-Analysis
Adventure Work Analysis using QlikView

## Business Overview
Adventure Works is a fictional company  created by Microsoft to provide a realistic business scenario for database and business intelligence (BI) applications. The company operates in the manufacturing and distribution sector, specializing in the production of bicycles and related accessories. It serves a global market, with a strong presence in North America, Europe, and Asia.

## Scope of Analysis
1. **Sales Perfomance Analysis**
- Revenue trends and product profitability
- Regional and market segment performance
- Customer purchasing behaviour and lifetime value
2. **Financial & Profitability Analysis**
- cost analysis and margin evaluation
3. **Human Resource & Employee Performance**
- Workforce productivity and retention

**Dataset**:
1 Fact Table containts details of sales and order date and 5 dimensions table ( Products, Regions, Resellers, SalesPersons, SalesPersonRegions)

### Data Loading and Preparation
Before loading the data from the Editor Script, I made some modification:
I formatted the Order date in Sales Table to use a properly formatting
```
Date(Date#(OrderDate,'dddd,MMMM DD, YYYY'), 'YYYY-MM-DD') as OrderDate,
```Sales:
LOAD SalesOrderNumber, 
     Date(Date#(OrderDate, 'DD/MM/YYYY'), 'YYYY-MM-DD') AS OrderDate,  
     Year(Date#(OrderDate, 'DD/MM/YYYY')) AS Year,
     Month(Date#(OrderDate, 'DD/MM/YYYY')) AS Month,
     Date(Date#(OrderDate, 'DD/MM/YYYY'), 'MMMM') AS MonthName,
     Date(Date#(OrderDate, 'DD/MM/YYYY'), 'MMM-YYYY') AS MonthYear,  
     ProductKey, 
     ResellerKey, 
     EmployeeKey as Sales_EmployeeKey, 
     SalesTerritoryKey, 
     Quantity, 
     [Unit Price], 
     Sales, 
     Cost
FROM
[C:\Users\Huawei\OneDrive\Desktop\Adventure work project Qlik View\Sales.csv]
(txt, codepage is 28591, embedded labels, delimiter is ';', msq)
WHERE OrderDate >= '2018-01-01' AND OrderDate <= '2019-12-31';
```
I changed the name of some columns in order to avoid the creation of synthetic key, here the model:

![image](https://github.com/user-attachments/assets/a6433bb7-1d54-4b64-bb98-e880a04cce20)

### Dashboards Overview
I created three distinct dashboards:


- **Sales Performance Analysis** – An overview of sales, costs, profits, and margins over the selected period..
- **Product Performance Analysis** – To explore Products performance.
- **Region & Team Performance** – To analyze

### Key Insights from the Sales Trend Dashboard

![image](https://github.com/user-attachments/assets/51f7401d-7345-4146-a228-06651653549f)

#### General Performance:
- Total Sales: $48.90M
- Total Costs: $48.18M
- Total Profit: $710.57K
- Total Margin: 1.45% (very low margin, indicating low profitability compared to costs)

The profit is relatively low compared to sales volume, suggesting a need to optimize costs or increase product margins.

#### Sales Trend Analysis:
- Sales in 2019 are higher than in 2018, showing steady growth with peaks in July and December.
- The trend follows seasonality, with a decline in the early months of the year and a strong recovery in Q3 and Q4.

The sales increase at the end of the year could be linked to seasonal promotions or holiday-related demand. It might be useful to analyze whether margins improve during peak months.

####  Profit Analysis (Total Profit):
- Monthly Profit is quite volatile
- Some months show losses ( es: June and October 2018)
- Higher sales months do not always correspond to high profits, suggesting possible high cost.

It's crucial to assess the relationship between costs and sales to optimize the commercial strategy.

#### Sales & Margin (%)
- The profit margin(%) tends to decrease in months when sales are higher.
- The negative correlation between sales and margin suggests that significant discounts may be applied during peak months.

If sales increase but margins decline, it may be necessary to review promotional strategies to avoid negatively impacting profitability.

#### Suggestion:
- Optimize costs: A 1.45% margin is very low. It's essential to investigate major cost factors and reduce inefficiencies.
- Analyze pricing: If sales peaks correspond to margin reductions, consider alternative strategies to maximize profit.
- Deep dive into seasonality: Identify the causes of low-sales months to stabilize annual performance.
- Focus on losses: Understand why profits are negative in certain months and correct any strategic issues.

### Key Insights from the Product Performance Dashboard

![image](https://github.com/user-attachments/assets/72eec305-a9a7-48d5-8f43-3573afbffe84)


#### General Performance:
- Total Sales: $48.90M
- Total Costs: $48.18M
- Total Profit: $710.57K
- Total Margin: 1.45% (very low margin, indicating low profitability compared to costs)

#### Distribution of Orders by Price Class:
- The main peaks are in the $100 - $200 and $600 - $700 ranges, suggesting these are the most popular price segments.

Offering more products within these high-demand price ranges could be a strategic move.

#### Top 5 Category, SubCategory and Product by  Sales and Quantity
- The Top Category for Sales is Bikes with 39M of value, is the core categoru of the company, the second is Components with 8M of sales. The last 2 are: Clothing 600k and Accessories 180k.
- The best Category in order of quantity sold are: Bikes (44.544 qty), Components (33.657 qty), Clothing (20.943 qty) and Accessories  (8.824 qty).
- The Top 5 SubCategory by Sales  are: Road Bikes ( 18,4M of Sales), Mountain Bikes (15,4M of Sales), Touring Bikes (5,8M of Sales), the last 2 belong to Category Components and are: Mountain Frames (3,5M of Sales) and Road Frames (2,8M of Sales).
- The top 5 products by Sales belong are Mountain Bikes: Mountain-200 Black, 39 ( 1,6M of Sales), Mountain-200 Black, 42 ( 1,4M of Sales), Mountain-200 Silver, 38 (1,2M of Sales), Mountain-200 Silver, 42 (1,17M of Sales) and Mountain-200 Silver, 46 (1,16M of Sales).

Bicycles dominate total sales. It makes sense to focus marketing efforts on these categories.

#### All Product Performance:
- In 2020 there is an increase of sales in almost all products.
- Despite the Sales almost 1/3 of all products show negative profits in both years. In particular for products that belong to Bike Category.
- In 2020 there is an increase of quantity sold in almost all products.

Negative Profits on Certain Products require an urgent control of costs who are effecting margins.

### Region & Team Performance Dashboard

![image](https://github.com/user-attachments/assets/503a4871-a163-41c3-a7de-796a12199cc1)

#### Total Sales by Region
- The Southwest (USA) and Canada (USA) regions appear to have the largest sales volume, while Australia and Germany have lower contributions.
  Southest (9,75M), Canada (8,26M), Northwest (7,8M), Southeast( 5,49M), Central (5,1M), Northeast (4,48M), UK (2,75M), France (2,6M), Germany (1,25M) and Australia (1,18M)

This suggests that sales strategies are highly successful in the U.S. regions, while international markets like Germany and Australia may need improvement or a different market approach.

#### Top 10 B2B Customers
- The largest B2B Customer are all from USA. The top 1 is Corner Bicycle Supply (Ontario), generating nearly $495K in sales. Other significant customers include Totes & Baskets Company (Texas) and Thorough Parts and Repair Services (Washington), both exceeding $450K in sales.

The sales gap between the top and bottom customers on this list suggests that customer segmentation and targeted strategies might be beneficial for lower-performing accounts.

#### Salesperson Performance
- Top Performer: Pamela Ansman-Wolfe (+414% sales growth, +116% customers) – Outstanding performance with a massive increase in revenue and customer base.
- Strong Growth: Michael Blythe & David Campbell – Significant sales growth despite a slight drop in customers. Likely secured higher-value deals.
- Worst Performer: Lynn Tsofilas (-22% sales, -36% customers) – Declining performance, losing both customers and sales. Needs urgent improvement.

Some representatives show exceptional growth, while others struggle with customer retention and sales consistency.

#### Suggestion:
- The company is expanding in terms of both customers and sales volume, but some sales reps are struggling, suggesting the need for focused interventions.
