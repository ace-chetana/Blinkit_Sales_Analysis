# Blinkit Sales Analysis

**Interactive Power BI dashboard** analyzing Blinkit’s sales, customer satisfaction, and inventory distribution to surface actionable insights for operations and merchandising. Core KPIs: **Total Sales**, **Average Sales**, **Number of Items**, and **Average Rating**. :contentReference[oaicite:0]{index=0}

---

## Features
- Total sales breakdown by **Item Fat Content**, **Item Type**, and **Outlet Establishment Year**. :contentReference[oaicite:1]{index=1}  
- Comparative outlet analysis: **Sales by Outlet Size**, **Sales by Outlet Location**, and **All KPIs by Outlet Type**. :contentReference[oaicite:2]{index=2}  
- Uses raw dataset (JSON/CSV) for analysis and supplied SQL queries for aggregation & sampling. Example dataset preview: `blinkit.json`. :contentReference[oaicite:3]{index=3}

---

## Data
Files included:
- `BlinkIT_data.csv` — raw dataset (CSV)  
- `Blinkit_data.sql` — example SQL queries used for aggregation and KPI checks. 
- `Blinkit Analysis.pptx` — project requirements and visualization specs. 

---

## SQL snippets 
```sql
-- Total sales (millions) for outlets established in 2022
select cast(sum(Total_Sales)/1000000 as decimal(10,2)) as Total_Sales_Millions
from blinkit_data
where Outlet_Est_Year = 2022;

-- Top 5 item types by total sales
select Item_Type,
       cast(sum(Total_Sales) as decimal(10,2)) as Total_Sales,
       cast(avg(Total_Sales) as decimal(10,1)) as Avg_Sale,
       Count(*) As No_of_Item,
       cast(avg(Rating) As decimal(10,2)) As Avg_Rating
from blinkit_data
group by Item_Type
order by Total_Sales desc
limit 5;
