# Web Traffic Analysis Dashboard

## Project Overview
The [Sales Performance Dashboard](https://public.tableau.com/app/profile/fang.wen.hsiao/viz/SupersotreSales_17111190533460/SuperstoreSalesPerformance) aims to provide actionable insights into the company's sales performance, focusing on key metrics such as Total Profit, Total Sales, Total Quantity, Profit by Subcategory, Sales by Segment, Order Distribution by Shipping Mode, and Order Distribution by Category. By leveraging these metrics, we aim to enhance our understanding of sales trends, identify areas of improvement, and drive strategic decision-making to optimize revenue and profitability.
![Superstore Sales Performance](https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/824c6010-480a-4933-8a10-2e67e523c235)


## Dashboard Metrics
1. **Total Profit with % Difference from Previous Year**
- What do I want to know:
  - I want to understand the overall profitability of our sales operations.
- Why do I want to know:
  - To check the financial health of our business and track changes in profitability over time.
- So what?
  - Analyze factors contributing to changes in profit.
  - Identify areas for cost reduction or revenue enhancement.

2. **Total Sales with % Difference from Previous Year**
- What do I want to know:
  - I want to assess the overall sales performance.
- Why do I want to know:
  - To track revenue growth or decline and evaluate the effectiveness of sales strategies.
- So what?
  - Investigate reasons behind fluctuations in sales.
  - Develop strategies to boost sales in underperforming areas.
 
3. **Total Quantity with % Difference from Previous Year**
- What do I want to know:
  - I want to understand the volume of products sold.
- Why do I want to know:
  - To evaluate demand trends and inventory management efficiency.
- So what? 
  - Adjust inventory levels based on demand fluctuations.
  - Explore opportunities for bundling or cross-selling products.

4. **Profit by Subcategory**
- What do I want to know:
  - I want to analyze profitability across different product categories.
- Why do I want to know:
  - To identify high-performing product categories and prioritize resource allocation.
- So what?
  - Allocate marketing resources to high-profit subcategories.
  - Consider expanding product lines in profitable categories.

5. **Sales by Segment**
- What do I want to know:
  - I want to understand sales performance across different customer segments.
- Why do I want to know:
  - To tailor marketing strategies and services to specific customer segments.
- So what?
  - Customize marketing campaigns to target specific segments.
  - Enhance customer experience based on segment preferences.

6. **Order Distribution by Shipping Mode**
- What do I want to know:
  - I want to analyze the distribution of orders by shipping method.
- Why do I want to know:
  - To optimize shipping logistics and improve delivery efficiency.
- So what?
  - Evaluate shipping costs and delivery times for each method.
  - Optimize shipping routes and carrier partnerships.

7. **Order Distribution by Category**
- What do I want to know:
  - I want to understand the distribution of orders across different product categories.
- Why do I want to know:
  - To identify popular product categories and adjust inventory management strategies.
- So what?
  - Ensure adequate inventory levels for high-demand categories.
  - Monitor sales trends to anticipate shifts in category popularity.

## Business Objectives
- Improve overall profitability by optimizing sales strategies and resource allocation.
- Increase revenue through targeted marketing efforts and product innovation.
- Enhance customer satisfaction by tailoring services to specific segments and improving delivery experiences.
- Optimize inventory management to meet demand and minimize stockouts.
- Drive growth by capitalizing on opportunities in high-profit product categories and customer segments.

## Data Source
The Sample Data is from [Tableau Superstore Sales](https://public.tableau.com/app/learn/sample-data): Contains information about products, sales, and profits that you can use to identify key areas of improvement within this fictitious company.

## Data Exploration

### YoY Percentage Increase in Total Sales, Total Profit and Total Quantity Sold
Prior to developing visualizations for these distinct aspects, it was essential to generate several calculated fields to filter the sales data from four years down to only two years, encompassing the current year and the preceding year.
To do this, I first created Calculated Fields for the following main KPIs: Total Profit, Total Sales, and Total Quantity Sold:
- Sales Current Year: IF YEAR ( [Order Date] ) = {MAX ( YEAR ( [Order Date] ))} THEN [Sales] END
- Sales Previous Year: IF YEAR ( [Order Date] ) = {MAX ( YEAR ( [Order Date] ))} - 1 THEN [Sales] END
- Sales % Differences: ( SUM ( [Sales Current Year] ) - SUM ( [Sales Previous Year] )) / SUM ( [Sales Previous Year] )
- Sales YoY%(+): IF [Sales % Differences] >= 0 then [Sales % Differences] END
- Sales YoY%(-): IF [Sales % Differences] < 0 then [Sales % Differences] END

![Sales Current Year](https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/9940ab14-d836-42f4-8b27-5c374a7071fa)

![Sales Previouse Year](https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/7ec2f5ee-4cd4-450a-8f09-d5b9f264c23a)

![Sales % Difference](https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/94289f72-75c5-4ad2-a8e7-d9ac58e99438)

![Sales YoY% (+)](https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/286b8982-b40c-4c86-82b3-4d8b6d13f4b2)

![Sales YoY% (-)](https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/39745e2a-5cce-4ecf-81b4-de857ce030c1)


Which allowed me to create this visual:

![Total Sales](https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/4f9caac6-a105-491d-bfd4-24dbcddb0c41)



I then duplicated those calculated fields to create the same for Profits and Quantity:

![Total Profit](https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/ef1e5500-5965-422d-9c2b-58fb27c10a2e)
![Total Quantity](https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/fd69cc22-fbd2-43bd-bd4e-acaade78bd20)


This provides a quick and easy snapshot to see how sales, profit, and quantity sold are doing compared to the previous year.

### Profit by Subcategory
I created a bar chart to understand the profitability of different product subcategories. By visualizing Profit by Subcategory, we can identify which subcategories contribute the most to overall profit and which ones may be underperforming. This insight helps in strategic decision-making, such as allocating resources towards high-profit subcategories, optimizing marketing strategies, or addressing issues in less profitable areas.

- Use tooltip to highlight detailed information
<img width="349" alt="Profit by subcategory" src="https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/ae3ed945-862e-4599-8482-813720d28acf">


### Sales by Segment
Creating side-by-side area charts for monthly sales by segment assists sales managers in promptly identifying the top-performing segments and their performance trends relative to others. By highlighting the maximum point for each segment and comparing it to the average values throughout the current year, managers can effectively gauge whether order sizes align with established averages. This aids in assessing deal sizes in the pipeline and ensures that order sizes are trending in line with existing averages, providing valuable insights for decision-making.

- Use tooltip to highlight detailed information


![Sales by Segment](https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/e01b916d-6ead-41a2-9a37-9ceee9c77adb)

### Order Distribution by Shipping Mode
This bar chart provides valuable insights into how orders are distributed across different shipping modes, allowing us to understand which shipping methods are most commonly used by customers. By analyzing this distribution, we can optimize our shipping logistics, improve delivery efficiency, and ensure customer satisfaction by offering preferred shipping options.

- Use tooltip to highlight detailed information


![Order Distribution by Shipping Mode](https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/8c718cbf-eec3-42c5-9baa-36ef6bbdf8e7)


### Order Distribution by Category
This bar chart is valuable for understanding how orders are distributed across different product categories. By analyzing this distribution, we can identify popular product categories and adjust inventory management strategies accordingly. Additionally, it helps us anticipate shifts in category popularity and tailor marketing efforts to promote products in less popular categories, ultimately driving sales and maximizing revenue.

- Use tooltip to highlight detailed information


![Order Distribution by Category](https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/bb1e859a-076d-484d-87c5-01daf703633c)


### Filter
We use the Country and State filter in this dashboard to provide users with the ability to analyze sales performance and trends at different geographic levels. By filtering data based on country and state, users can narrow down their focus to specific regions of interest. This enables them to gain insights into regional sales patterns, identify areas of high or low performance, and tailor strategies to specific geographic markets. 


![Filter](https://github.com/fangoaish/Tableau__Superstore_Sales_Performance/assets/51399519/d56a784f-06ac-4a1e-8e91-defaa655708a)


## Exploratory Data Analysis
1. **Total Profit, Sales, and Quantity:**
    - Insight: Our sales dashboard provides a comprehensive view of Total Profit, Sales, and Quantity, allowing us to monitor financial health and performance trends over time.
    - Recommendation: Analyze factors driving changes in profit, sales, and quantity. Identify areas for cost reduction or revenue enhancement to improve profitability.

2. **Profit by Subcategory:**
    - Insight: The Profit by Subcategory chart reveals which product categories contribute the most to overall profit.
    - Recommendation: Allocate resources to high-profit subcategories, optimize marketing strategies, and address underperforming areas to maximize profitability.

3. **Sales by Segment:**
    - Insight: Side-by-side area charts for monthly sales by segment highlight top-performing segments and their performance trends.
    - Recommendation: Compare order sizes with established averages to assess deal sizes in the pipeline and ensure alignment with expectations.

4. **Order Distribution by Shipping Mode and Category:**
    - Insight: These charts offer insights into order distribution across shipping modes and product categories.
    - Recommendation: Optimize shipping logistics, improve delivery efficiency, and tailor marketing efforts based on popular product categories to drive sales and maximize revenue.

5. **Geographic Filter:**
    - Insight: The Country and State filter enables analysis of sales performance at different geographic levels.
    - Recommendation: Tailor strategies to specific geographic markets, identify regional sales patterns, and focus on areas of high performance for targeted growth initiatives.

## Conclusion 
The Sales Performance Dashboard provides valuable insights into the company's sales performance across various metrics and geographic regions. By leveraging these insights, we can make informed decisions to optimize revenue, enhance profitability, and improve customer satisfaction. 
