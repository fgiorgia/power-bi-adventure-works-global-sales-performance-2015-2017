# Global Sales Performance 2015–2017

A comprehensive business intelligence solution analyzing sales performance, customer demographics, and product portfolio metrics for AdventureWorks (2015-2017). Built as the final project for ReDI School's AI & Data Analytics Course 2025.

## Initial Setup
To use this project, you need to enable the [PBIR preview feature in Power BI Desktop](https://powerbi.microsoft.com/en-us/blog/power-bi-enhanced-report-format-pbir-in-power-bi-desktop-developer-mode-preview/). Go to `File > Options and settings > Options > Preview features`, and check the box next to "_Store reports using enhanced metadata format (PBIR)._" This will allow you to use the new PBIR format.

## Preview

<video src="https://github.com/user-attachments/assets/59edbe03-3cb8-4d2d-80c8-0de7ff476459" controls="controls" muted="muted" style="max-width: 700px;">
</video>


### Desktop
<img width="1200" max-width="80vw" alt="Report overview dashboard" src="https://github.com/user-attachments/assets/f9257780-64eb-49f5-a397-bec641a678f0" />

### Mobile
<img width="350" max-width="80vw" alt="Report overview dashboard" src="https://github.com/user-attachments/assets/64cb5d5b-f79d-41f4-b041-da7e0c0ffe92" />

## Project Overview
This Power BI report provides executive-level insights into a fictional retail company's performance across multiple dimensions:
- Financial Performance: Revenue trends, profit margins, and growth metrics
- Product Analytics: Pareto analysis identifying top revenue drivers
- Customer Segmentation: Demographics, purchasing behavior, and lifetime value
- Geographic Analysis: Multi-region performance comparison
- Operational Metrics: Return rates and quality indicators

### Key Metrics Tracked
| Metric               | Value      | Insight                         |
|----------------------|------------|---------------------------------|
| Total Revenue        | $24.91M    | Strong growth trajectory        |
| Net Profit           | $10.46M    | ~42% net margin                 |
| Return Rate          | 2.17%      | Industry-leading quality        |
| Revenue Per Customer | ~$3,000    | High customer lifetime value    |
| Top 20 Products      | 59.61%     | Pareto principle validated      |

### Key Features
#### Data Architecture
- Star Schema Design: Optimized for query performance
- 2 Fact Tables: Sales and Returns transactions
- 6 Dimension Tables: Customers, Products, Calendar, Territories, Categories, Subcategories
- Relationships: 9 active, 1 inactive (for time intelligence scenarios)

<img width="1200" max-width="80vw" alt="Star Schema Design" src="https://github.com/user-attachments/assets/457e842b-ea6c-42c7-a424-5186871cce89" />

| From Table[Column]                                | To Table[Column]                                      | Type         |
|---------------------------------------------------|-------------------------------------------------------|--------------|
| Fact_Sales [ProductKey]                           | Dim_Products [ProductKey]                             | Many-to-One  |
| Fact_Sales [CustomerKey]                          | Dim_Customers [CustomerKey]                           | Many-to-One  |
| Fact_Sales [TerritoryKey]                         | Dim_Territories [SalesTerritoryKey]                   | Many-to-One  |
| Fact_Sales [OrderDate]                            | Dim_Calendar [Date]                                   | Many-to-One  |
| Fact_Returns [ProductKey]                         | Dim_Products [ProductKey]                             | Many-to-One  |
| Fact_Returns [TerritoryKey]                       | Dim_Territories [SalesTerritoryKey]                   | Many-to-One  |
| Fact_Returns [ReturnDate]                         | Dim_Calendar [Date]                                   | Many-to-One  |
| Dim_Products [ProductSubcategoryKey]              | Dim_Product_Subcategories [ProductSubcategoryKey]     | Many-to-One  |
| Dim_Product_Subcategories [ProductCategoryKey]    | Dim_Product_Categories [ProductCategoryKey]           | Many-to-One  |

**Inactive Relationships**
- `Fact_Sales[StockDate] → Dim_Calendar[Date]` (Used for specific stock-based measures via `USERELATIONSHIP`).

#### Advanced Analytics
- Pareto Analysis: Identifies 80/20 revenue distribution
- Time Intelligence: Month-over-month comparisons, trend analysis
- Customer Segmentation: Age groups, income brackets, occupation analysis
- Calculated Columns: Dynamic customer age at purchase, age grouping
- DAX Measures: Including cumulative calculations and ranking functions

#### Visualization Highlights
- Interactive geographical maps
- Pareto charts with dual-axis design
- Time-series revenue trends
- Demographic breakdowns
- KPI cards with conditional formatting

#### Enhanced User Experience
- Natural Language Q&A: Extensive synonym library for intuitive queries
- Custom HTML Documentation: HTML built-in technical reference
- Executive Summary: HTML built-in business-focused report

<video src="https://github.com/user-attachments/assets/2e80a06e-30c1-488b-81d4-ed068652e436" controls="controls" muted="muted" style="max-width: 700px;">
</video>

### Technical Stack
#### Primary Tools:
- Power BI Desktop
- Power Query (M Language)
- DAX (Data Analysis Expressions)

#### Data Source:
- CSV files ([Google Drive folder](https://drive.google.com/drive/folders/1J7RGXF7GGRJqO8gEyi7UzWXAWyLU4KpE))
- 10 source files including Sales (2015-2017), Customers, Products, Returns, Territories, Calendar

## Getting Started
#### Prerequisites
- Power BI Desktop (latest version recommended)
- Basic understanding of data modeling and DAX

#### Installation & Setup
1. Clone the repository: `git clone https://github.com/fgiorgia/power-bi-adventure-works-global-sales-performance-2015-2017.git
   cd power-bi-adventure-works-global-sales-performance-2015-2017`
2. Download the data source
    - Data is hosted on Google Drive: [AdventureWorks Data](https://drive.google.com/drive/folders/1J7RGXF7GGRJqO8gEyi7UzWXAWyLU4KpE)
    - Save all CSV files to a local folder
3. Configure data source path
    - Open Power BI Desktop
    - Import the PBIX file
    - Go to Transform Data → Data Source Settings
    - Update the folder path to your local directory
    - Apply changes and refresh
4. Explore the dashboard
    - Navigate through report pages using tabs
    - Try Q&A feature with natural language queries
    - Use slicers and filters for interactive analysis

## Key Insights & Findings
#### Financial Performance
- Consistent revenue growth from 2015-2017
- Recent month: +3.31% revenue despite -0.88% order volume (increasing AOV)
- 42% net profit margin indicates healthy operations
#### Product Strategy
- Pareto Validation: Top 20 products = 59.61% of revenue
- Star Products: Mountain-200 series (Black/Silver) each exceed $1.2M
- Volume Leaders: Tires and Tubes drive order frequency
- Opportunity: Use accessories as entry point, upsell to bikes
#### Customer Profile (ICP)
- Age: 40-49 age group dominates ($8.9M revenue)
- Income: $40k-$70k annual income sweet spot
- Education: Bachelor's degree holders contribute $8.4M
- Occupation: Professionals lead at $8.5M revenue
#### Geographic Distribution
- Top Markets: United States, Australia
- Consistency: 59-63% revenue concentration across all regions
- Insight: Australia shows higher revenue per customer than US
#### Operational Excellence
- 2.17% return rate (excellent for retail)
- Concern areas: Shorts category, specific helmet SKUs (>3.3% returns)
## Notable DAX Measures
#### Time Intelligence Example:
```
Previous Month Revenue = 
CALCULATE(
    [Total Revenue],
    DATEADD(Dim_Calendar[Date], -1, MONTH)
)
```
#### Pareto Analysis:
```
Cumulative Revenue % = 
VAR CurrentSumSalesAmount = [Total Revenue]
VAR TotalSalesAmount = 
    CALCULATE(
        [Total Revenue],
        ALLSELECTED(Dim_Products[ProductName])
    )
VAR IncrementalSalesAmount = 
    SUMX(
        FILTER(
            ALLSELECTED(Dim_Products[ProductName]),
            [Total Revenue] >= CurrentSumSalesAmount
        ),
        [Total Revenue]
    )
RETURN 
    DIVIDE(IncrementalSalesAmount, TotalSalesAmount)
```
#### Dynamic Age Calculation:
```
CustomerAge = 
YEAR(Fact_Sales[OrderDate]) 
    - YEAR(RELATED(Dim_Customers[BirthDate]))
    + IF(
        DATE(2000, MONTH(Fact_Sales[OrderDate]), DAY(Fact_Sales[OrderDate])) 
        < DATE(2000, MONTH(RELATED(Dim_Customers[BirthDate])), 
               DAY(RELATED(Dim_Customers[BirthDate]))),
        -1,
        0
    )
```
## Documentation
The project includes embedded HTML documentation accessible within the Power BI report:
- Technical Documentation: Complete data model architecture, ETL transformations, and measure definitions
- Executive Summary: Business-focused insights and recommendations
- Linguistic Schema: Q&A synonyms and natural language query optimization

## Learning Outcomes
This project demonstrates proficiency in:
- - [x] Data modeling (Star Schema design)
- - [x] ETL processes using Power Query (M language)
- - [x] Advanced DAX calculations (time intelligence, ranking, Pareto)
- - [x] Data visualization best practices
- - [x] Business intelligence storytelling
- - [x] Report optimization and user experience design
- - [x] Mobile-optimized report layout

## Future Enhancements
- - [ ] Parameterize data source connections for deployment
- - [ ] Implement DAX-generated calendar table for dynamic dates
- - [ ] Add forecasting models using Power BI's AI features
- - [ ] Integrate real-time data refresh (if production data available)
- - [ ] Add what-if parameters for scenario planning
- - [ ] Implement row-level security for multi-user deployment

## License
This project is licensed under the MIT License - see the LICENSE file for details.
