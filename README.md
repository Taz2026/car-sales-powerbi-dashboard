# Car Sales Power BI Dashboard

## 📌 Project Overview
This project presents a sales analytics dashboard built for a vehicle dealership network. It ingests sales data from Dealers, Models, and Sales tables (in Excel/SQL) and answers key business questions: 
(1) revenue by country (South Africa vs Botswana), 
(2) identifying the top 3 best-selling car models, 
(3) comparing profit versus units sold across car segments, and 
(4) visualizing revenue by city. 
* The goal is to provide clear metrics and visual insights for decision-makers.

## 🛠 Tools Used
* Power BI Desktop: For data modeling, DAX measures, and interactive visualizations.
* SQL / Excel: Data storage and queries (joins, aggregations) on the underlying tables.
* DAX (Data Analysis Expressions): For calculated measures (e.g., total revenue, profit, rankings).
* GitHub: Repository for project files, documentation, and version control.

## 🗂 Database Schema
The data model consists of three main tables:

* Dealers: Contains DealerID, DealerName, City, and Country. 
Each dealer record represents a sales outlet in ZA or BW.
* Models: Contains ModelID, Brand, ModelName, Segment (e.g., SUV, Sedan), EngineSize, FuelType, Price, and Profit per unit. 
This is a dimension table of car models.
* Sales: Contains SaleID, Date, DealerID (foreign key to Dealers), ModelID (foreign key to Models), Quantity, TotalPrice, and TotalProfit. 
This is the fact table of transactions.
* Key relationships: Dealers.DealerID → Sales.DealerID (one-to-many) and Models.ModelID → Sales.ModelID. 

* These links enable slicing sales by dealer location or car attributes.

## ❓ Business Questions
The analysis addresses the following questions:

* Revenue by Country: How does total sales revenue compare between South Africa (ZA) and Botswana (BW)?
* Top 3 Cars Sold: Which three car models have the highest units sold, and what are their sales figures?
* Profit vs Segment: For each car segment, how do total profit and sales quantity compare? (Which segments deliver the most profit per unit sold?)
* Revenue by City: Which cities generate the most sales revenue across all dealers?

* Each question is explored with appropriate visuals (bar charts, pie charts, or scatter charts) and backed by SQL/DAX calculations.

## 🧠 Key SQL Techniques Used
* JOINs: Combine the Dealers, Models, and Sales tables on their key columns to aggregate data.
* GROUP BY & Aggregations: Compute sums and counts (e.g., SUM(Quantity), SUM(TotalPrice)) to get total sales and revenue by category.
* Window Functions / RANK(): Identify top-N items. For example, use RANK() OVER (ORDER BY SUM(Quantity) DESC) or a TOP 3 clause to find the three best-selling models.
* Filtering: SQL WHERE clauses and DAX filters restrict data (e.g., to ZA and BW countries or to specific date ranges).
* Calculated Columns/Measures: Use DAX or SQL to create fields like Profit per Unit and TotalRevenue.

* (Note: All source data in the Excel was treated as if in a SQL database, but Power BI’s “Get Data” and DAX were used for the analysis.)

## 📊 Key Insights from the Analysis
* Country Revenue: The dashboard reveals that Botswana accounts for the majority (67.42%) of total revenue, with South Africa contributing the remainder. 
This highlights BW’s larger market share.
* Top 3 Models: The top-selling models were Model 3 Series (Brand BMW), Model Qashqai (Brand Nissan), and Model Polo & Rio (Brand Volkswagen & Kia) with 33, 32, and 29 units sold respectively. 
Their sales significantly outperform those of other models, indicating strong demand in popular segments.
* Segment Profitability: Sedans and Hatchbacks lead in total units sold, but Sedan vehicles show the highest profit margin per unit. The Dual-axis bar chart helped identify segments that sell more versus those that are more profitable.
* City Performance: Cities like Gaborone, Cape Town, and Molepolole stand out with the highest revenues. 
This informs regional targeting for sales efforts.

* These insights can guide strategy, such as focusing marketing on high-profit segments or allocating inventory to top-performing cities.

## 📈 Supply Chain KPIs Calculated
* Total Revenue: Sum of all sales (SUM(TotalPrice)), key top-line metric.
* Total Profit: Sum of all profits from sales (SUM(TotalProfit)), indicating overall margin.
* Units Sold: Total quantity of vehicles sold (SUM(Quantity)), reflecting volume.
* Number of Dealers/Models: Distinct counts of dealers and models sold, showing network and product diversity.
* Profit per Unit: Average profit by dividing total profit by units sold, highlighting margin efficiency per sale.

## 📁 Project Structure

```
/sales-dashboard-project
│
├─ data/
│    └─ TopCars_Africa.xlsx   # Source data tables (Dealers, Models, Sales)
│
├─ reports/
│    └─ SalesDashboard.pbix   # Power BI report file with data model and visuals
│
├─ sql/
│    └─ queries.sql           # Key SQL queries used for analysis (joins, top3 queries, etc.)
│
├─ screenshots/
│    └─ Dashboard_Example.png # Example final dashboard image
│
└─ README.md                 # Project documentation (this file)

* The data folder contains the raw dataset.
* Reports hold the Power BI report with all measures and visuals.
* SQL includes example SQL query snippets (e.g., top-3 ranking, segment aggregation).
* Screenshots have images of the dashboard for preview.
* The top-level README.md (this file) summarizes the project, tools, and findings.
