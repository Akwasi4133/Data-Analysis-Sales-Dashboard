
# Maven Toys Store Data Analysis (Interactive Dashboard created using Power BI)

## Table of Content
 - [Project Overview](#project-Overview)
 - [Data Used](#data-used)
 - [Tools Used](#tools-used)
 - [Methodology](#methodology)
 - [Recommended Analysis](#recommended-analysis)
 - [Key Insights](#key-insights)
 - [Strategic Recommendation](#strategic-recommendation)
   
## Project Overview

This recent Power BI-driven analysis has provided actionable insights into revenue trends, product performance across various regions, and the strengths of specific store locations. This analysis offers a foundation for strategic decisions that can drive profitability and optimize operations. Here’s a summary of the main insights:

## Data Used 
<a href =“https://www.kaggle.com/datasets/tanvir25/maven-toys?select=MavenToys”>Dataset<a/>

## Tools Used
- Power BI

## Methodology
#### Data Cleaning/Preparation 
- This Power BI analysis workflow started with:
  - Removing Duplicates: Identifying and deleting duplicate entries to preserve the accuracy and uniqueness of the data.
  - Filtering Rows: Applying filters to remove any rows that don’t meet specified criteria, such as rows with null values or zeros, to focus only on relevant  data.
  - Splitting Columns: Separating data in a single column into multiple columns using delimiters.
  - Merging Columns: Combining data from multiple columns into a single column when necessary, such as combining first and last names to create a full name field.
  - Handling Null Values: Managing missing data by replacing and deleting nulls to avoid errors in calculations and maintain report accuracy.

#### Data Modeling
- Define Relationships: Relevant relationships between tables based on key fields (primary and foreign keys) were created to ensure accurate joins.

#### DAX (Data Analysis Expressions)
-  DAX calculations are created to define essential metrics like revenue and profit.

    - Key Codes
       - YOY Trend Icon Profit = 
VAR PositiveIcon = UNICHAR(9650)
VAR NegativeIcon = UNICHAR(9660)
VAR Choice = IF('Profit Measures'[YOY Growth Profit] > 0, PositiveIcon, NegativeIcon)
VAR Display = Choice & " " & FORMAT([YOY Growth Profit],"0.00%")
RETURN Display

      - Rank Category By Profit = 
    VAR topcategorybyprofit = IF(ISINSCOPE(Products[Product_Category]),(RANKX(ALL(Products[Product_Category]),'Profit Measures'[Profit],,ASC)))
    VAR bottomcategorybyprofit = IF(ISINSCOPE(Products[Product_Category]),(RANKX(ALL(Products[Product_Category]),'Profit Measures'[Profit],,DESC)))
    VAR Ranking = IF(SELECTEDVALUE(TopBottom[Value]) = "Top", topcategorybyprofit, bottomcategorybyprofit)
    RETURN IF(Ranking <= 'Top N Parameter'[Top N Parameter Value], 'Profit Measures'[Profit])

      - YOY Growth Revenue = DIVIDE('Revenue Measures'[Revenue] - 'Revenue Measures'[Revenue SPLY], 'Revenue Measures'[Revenue SPLY])
        
#### Data Visualization 
-  Visuals, such as bar charts and line graphs, along with dynamic filters, are added to explore trends by product category, region, and time period. Finally, the report is published in Power BI Service, allowing stakeholders to interact with insights and make informed strategic decisions


## Recommended Analysis
- Identifying profit-driving product categories across store locations.
- Which stores are the most profitable, and how can this guide store expansion decisions?
- Unveiling seasonal trends or patterns in sales data.
- Investigating sales impact due to out-of-stock products.
- Evaluating inventory investment and duration. 


## Key Insights:
- Top-Performing Location: The Downtown area stands out as the leading revenue generator, contributing $8.22M in sales and $2.25M in profit across 29 stores, highlighting the value of prime locations.

- Category Performance: Toys have proven to be a major driver, accounting for 36% of total sales ($5.1M) and 27% of profit ($1.1M). This underscores the effectiveness of targeted product strategies.

- Highest-Profit Store: The Ciudad de Mexico 2 store has the highest profitability, bringing in $170K in profit, which suggests that localized store strategies can greatly impact revenue.

- Inventory Insights: Our analysis revealed no direct correlation between stock levels and profit, indicating that optimal inventory management can be achieved without surplus stock.

- Seasonal Sales Patterns: December emerged as the top month for revenue, with $877K in sales, demonstrating a strong opportunity for targeted seasonal promotions and inventory planning.

- Stock on Hand vs Profit: This had zero correlation as having high or low stock does not correlate with high or low profit.


## Strategic Recommendations:
To support continued revenue growth, Maven should focus on ensuring optimal inventory levels for high-demand product categories at key locations, especially during peak sales periods. Prioritizing seasonal promotions and aligning inventory with expected demand can further enhance sales impact. Applying these insights will allow Maven to expand its reach effectively while optimizing profitability.

## Dashboard Static Preview 
### Landing Page
![Landing Page](https://github.com/user-attachments/assets/33572d23-b64f-42dc-bf5d-71b032a7bc3d)
### Overview Page
![Overview Page](https://github.com/user-attachments/assets/31542f92-f5c6-4933-b88b-72b772349a1a)
### Product Performance Page
![Product Performance](https://github.com/user-attachments/assets/6274d53e-9b6a-4dfd-9ce1-c18c75b13cb1)
### Store Performance Page
![Store Performance](https://github.com/user-attachments/assets/92b4fc64-1cd8-4fe3-b367-a0df5cc40787)

## Dashboard Dynamic Preview 
<a href=”https://app.powerbi.com/view?r=eyJrIjoiYWEwNjRhZTMtNDNjYi00ZmVjLWExM2YtNDA0ZmI2NjNlMzRkIiwidCI6IjNlOTQzNDlkLWUyYTgtNGY2YS05MGExLWE2NGJjOGUwYTc4ZCJ9”> View Dashboard </a>
