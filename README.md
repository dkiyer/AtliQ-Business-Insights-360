# AtliQ Business Insights 360

## Project Overview

AtliQ Hardware, experiencing significant growth in recent years, has made a pivotal decision to integrate data analytics using Power BI into its operations for the first time. This strategic move is aimed at outperforming competitors in the market and driving data-driven decision-making. The project is poised to provide comprehensive insights across finance, sales, marketing, and supply chain management domains, catering to the inquiries of stakeholders effectively.

_([CLICK TO VIEW INTERACTIVE DASHBOARD HERE](https://app.powerbi.com/view?r=eyJrIjoiMjdlYzExNzYtMTE2ZC00YzI5LWIxODctMzM3MjQ3M2Q1YzVjIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9))_


## Tech stacks

- SQL
- PowerBi Desktop
- Excel
- DAX language
- DAX studio (for optimizing the report)
- Project charter file


## Power BI Techniques Learnt

- What are all the questions to be asked before staring the project?
- Creating calculated columns
- Creating measures using DAX language
- Data Modeling
- Using Bookmarks to switch between two visuals
- Page Navigation with buttons
- Using divide function to prevent zero division errors
- Creating date table using M language
- Dynamic titles based on the applied filters
- Using KPI indicators
- Conditional formatting the values in visuals using icons or background color
- Data validation techniques
- Publishing reports to Power BI services and collaborating workspace 
- Setting up personal gateway to set up auto refresh for data

## Business related terms

- Gross Price
- Pre-invoice Discounts
- Post-Invoice Discounts
- Net Invoice Sales
- Net Sales
- COGS: Cost of Goods Sold 
- Gross Margin
- Net profit
- YTD - Year to Date
- YTG - Year to Go
- Direct
- Retailer
- Distributors
- Customer vs. Consumer

## Company’s background

AltiQ is an electronics hardware company which has grown vastly in the recent years, and opened business all over the globe. It sells computer hardware and accessories through three main mediums/channel:

- Retailers
- Direct
- Distributors

Recently, AltiQ faced an unexpected setback following the launch of a store in America, assessed through surveys, intuition, and rudimentary Excel analysis. In contrast, competitors leverage dedicated analytics teams for informed decision-making. Recognizing the necessity of adapting to industry demands, AltiQ Hardware must prioritize the establishment of its own analytics team. This strategic initiative will enable the company to gather comprehensive data-driven insights, make informed decisions, and enhance its competitive position in the market.

## Questions to ask before beginning to build a dashboard:

- What is the objective of building this dashboard?
- In what terms will the success of this project be measured?
- What will be the deadline of the project?
- Who are the stakeholders and what purpose will this dashbord serve for them?
- What are the stakeholder expectations from this project?
- Do they need a preview before the actual release?
- What are all the resources/data needed to build this dashboard?
- What missing/unavailable data needs to be factored into the building process?
- Are there any specific inputs from stakeholders in terms of design and views that need to be kept in mind?

## Understanding the Data

Understanding the data before jumping headlong into the analysis is important. First we need to identify our:  

- Dimension tables: They contain all the static data like details of customers, markets, products et al. 
- Fact tables : They contain all the data for day-to-day transactions.

In our model, we have the following Dimension Tables:

Using 2 databases: **gdb041** and **gdb056**:

1. **dim_customer:**
	- 27 distinct markets (eg. India, USA, Spain)
	- 75 distinct customers thoroughout the market
	- 2 types of platforms:
		- Brick & Mortor - Physical/offline store (eg. Croma, Sales India)
		- E-commerce - Online Store (eg. Amazon, Flipkart)
	- Three channels:
		- Retailer
		- Direct
		- Distributors

2. **dim_market:**
	- 27 distinct markets (eg. India, USA, Spain)
	- 7 sub-zones
	- 4 regions
		- APAC
		- EU
		- NA
		- LATAM

3. **dim_product:**
	- Divisions
		- P & A
			- Peripherals
			- Accessories
		- PC
			- Notebook
			- Desktop
		- N & S
			- Networking
			- Storage
	- Cagetories: 14 different kinds (eg. Internal HDD, Keyboard)
	- Variants: Different kinds available for the same product

And we have the following Fact Tables:

1. **fact_forecast_monthly:** This table is used to forecast customer needs in advance, enhancing customer satisfaction and reducing warehouse storage costs. Denormalized by the data engineering team for analytical purposes, it replaces all dates with their respective month start dates and includes all necessary column names, culminating in the forecasted customer quantity needs.

2. **fact_sales_monthly:** This table is essentially identical to the 'fact_forecast_monthly' table, except that the final column displays the quantity sold instead of the forecasted value.

3. **gross_price:** This table provides the details of gross prices with corresponding product codes. 

4. **Pre_invoice_deductions:** This table comprises the details of pre-invoice deduction percentages for each customer, segmented by year.

5. **Post_invoice_deductions:** This table encompasses the details of post-invoice deductions and other deduction categories.

6. **freight_cost:** This table provides detailed information on travel costs and other expenses associated with each market, organized by fiscal year.

7. **manufacturing_cost:** This table contains the manufacturing cost details associated with each product code, categorized by year.

Additional tables used are:

1. **facts_actuals_estimates:** Created by merging fact_sales_monthly and fact_forecast_monthly data together to get their quantities in one table.
   
2.  **operational_expense:** Contains data for ads and other operational expenses by fiscal year and market.
   
3. **NsGMTarget:** Net Sales, Gross Margin and Net Profit Targets for fiscal year 2022 by market.
 
4. **marketshare:** Total Market Sales data for fiscal year by manufacturer, category and sub zone. 

## Importing data into Power BI 

Given that the database for this project is in MySQL, it's essential to import the datasets into Power BI by providing the necessary database access credentials.

## Data Model

- Data modeling is crucial as it forms the foundation of reports, upon which all visuals are constructed. 
- Poor data modeling can significantly impact report performance. 
- In this project, we've adopted the Snowflake data modeling approach with 20+ tables (dimension and fact) altogether. 

<img width="828" alt="AtliQ Data Model" src="https://github.com/dkiyer/AtliQ-Business-Insights-360/assets/108228096/9aed446d-c0dd-4135-8fb3-3007888b43e6">

## Dashboard designing

Based on the mockups received from the project owner, we begin designing the visuals and generate DAX measure as needed. 

## Home View

In Home View, all the views button are available. User will land on specific view page by clicking each button.

- Finance View
- Sales View
- Marketing View
- Supply chain View
- Executive View

## Overall Report

![Home Page](https://github.com/dkiyer/AtliQ-Business-Insights-360/assets/108228096/a499fe27-b67e-4018-b29b-8c9dc4a605eb)

## Finance view

- **KPI Card Visuals:** Net Sales, Gross Margin %, Net Profit % (with comparison against Benchmarks).
- **Tables:** Profit & Loss Statement, Top/Bottom Products and Customers.
- **Area Chart:** Comparison of KPIs between Selected Year against Benchmarks.
- **Additional Feature:** Users can toggle between comparing current year figures with Last Year (vs LY) or Targets (vs Target).  

![Finance View](https://github.com/dkiyer/AtliQ-Business-Insights-360/assets/108228096/6fe6305a-2f31-40c6-93d6-5c056121d31e)

## Sales view

- Sales view is focused on customers so here we emphasize customer-oriented metrics.
- **Tables:** Customer Performance, Product Performance. Upon hovering over the table values, a line chart appears as a tooltip.
- **Scatter Plot:** Net Sales against Gross Margin % by market and region with a dynamic slicer to see customers below our GM % Target. Tooltip chart is also available upon hovering on the chart values. 
- **Donut Charts:** Displaying pre- and post-invoice discounts given to customers against Net Sales generated, facilitating comparison. Additionally, another donut chart illustrates the percentage of Net Sales allocated to Cost of Goods Sold (COGS) and Gross Margin, providing insight into unit economics which is important from a sales perspective.
- **Note:** For growth companies, tracking Gross Margin from a sales perspective is more crucial than Net Profit due to high operational costs incurred during market expansion. Therefore, this perspective prioritizes Gross Margin over Net Profit.

![Sales View](https://github.com/dkiyer/AtliQ-Business-Insights-360/assets/108228096/b0eda8b3-03de-4595-80bf-e53e8c8d1dba)

## Marketing View

- Marketing view is focused on products so here we emphasize product-oriented metrics
- **Tables:** Product Performance, Region/Market/Customer Performance 
- **Performance Matrix:** Displays a toggleable view presenting Net Sales plotted against Gross Margin % and Net Profit % using scatter chart.
- **Donut Chart:** Displays the breakdown of Cost of Goods Sold (COGS) and Gross Margin across various product segments.
- **Waterfall Chart:** Displays the Net Profit performance of products relative to their Gross Margin and operational expenses, which includes expenditures on ads and promotions.
- **Note:** The marketing team invests in ads to enhance brand engagement, making Net Profit a crucial criterion in their analysis. Excessive spending on ads can lead to increased operational expenses, emphasizing the importance of monitoring Net Profit in this view. 

![Marketing View](https://github.com/dkiyer/AtliQ-Business-Insights-360/assets/108228096/7e907768-b27d-480d-a324-5de12905a6e2)

## Supply Chain View

- **KPI Card Visuals:** Forecast Accuracy, Net Error, ABS Error with their corresponding previous year values for comparison. 
- **Tables:** Key Metrics by Customers and Products
- **Accuracy/Net Error Trend Chart:** A combined line and clustered column chart illustrates Forecast Accuracy % comparing the Current year to Last Year (LY), alongside Net Error to enhance visibility of discrepancies.

![Supply Chain View](https://github.com/dkiyer/AtliQ-Business-Insights-360/assets/108228096/a6ac8f27-52bc-4a0f-a9ce-cac4ffd7c683)

## Executive View

- **KPI Card Visuals:** Net Sales, Gross Margin %, Net Profit %, and Forecast Accuracy as compared against their corresponding benchmarks (Last Year or Targets, as chosen in the slicer).
- **Tables:** Key Insights by Sub Zones, Top 5 Customers and Top 5 Products by AtliQ's Revenue Contribution % (Market Share). 
- **Ribbon Chart:** Showcases PC Market Share Growth Trend comparing AtliQ's Market Share against similar competitors from 2018-2022. 
- **Donut Charts:** Displays Net Sales by Division and Channel. 
- **Yearly Trend Chart:** Shows Growth Trends for Gross Margin %, Net Profit %, PC Market Share % and Net Sales from 2018-2022. 

![Executive View](https://github.com/dkiyer/AtliQ-Business-Insights-360/assets/108228096/633a2803-885b-4fbb-901f-8f8f45bc33ea)

## Project Outcome

Utilizing this report enables data-driven decision-making across various departments and facilitates management with a comprehensive perspective on the organization's financial well-being.

_([CLICK TO VIEW INTERACTIVE DASHBOARD HERE](https://app.powerbi.com/view?r=eyJrIjoiMjdlYzExNzYtMTE2ZC00YzI5LWIxODctMzM3MjQ3M2Q1YzVjIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9))_


