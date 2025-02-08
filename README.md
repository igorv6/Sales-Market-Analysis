# Sales-Market-Analysis
Adventure Work Analysis using QlikView

## Business Overview
Adventure Works is a fictional company created by Microsoft to provide a realistic business scenario for database and business intelligence (BI) applications. The company operates in the manufacturing and distribution sector, specializing in the production of bicycles and related accessories. It serves a global market, with a strong presence in North America, Europe, and Asia.

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
1 Fact Table containts details of sales and order date and 6 dimensions table ( Products, Regions, Resellers, SalesPersons, 

### Data Loading and Preparation
Before loading the data from the Editor Script, I made some modification:
I formatted the Order date in Sales Table to use a properly formatting
```
Date(Date#(OrderDate,'dddd,MMMM DD, YYYY'), 'YYYY-MM-DD') as OrderDate,
```
