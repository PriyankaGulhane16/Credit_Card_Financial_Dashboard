📊 Credit Card Transaction & Customer Analytics Dashboard

📝 Overview

This project demonstrates an end-to-end Data Analytics workflow — from raw data processing in SQL to interactive dashboard development in Power BI.

The objective was to analyze credit card transactions and customer data to generate actionable business insights such as revenue trends, customer segmentation, and week-on-week performance metrics


🛠 Tools & Technologies

SQL Server – Data storage & initial loading

PostgreSQL – Data querying & analysis

Power BI – Data modeling & dashboard creation

DAX (Data Analysis Expressions) – Business calculations



📂 Dataset

The dataset includes two primary tables:

1️⃣ Credit Card Details

Client Number

Card Category

Annual Fees

Total Transaction Amount

Total Transaction Count

Interest Earned

Week Start Date

2️⃣ Customer Details

Client Number

Customer Age

Gender

Income

State

Activation Status

Delinquency Status

The data simulates real-world banking transaction and customer records.





🔄 Project Steps

1️⃣ Data Loading (SQL Server)

Created database and tables

Imported UTF-8 CSV files

Verified schema and data types

2️⃣ Data Cleaning

Removed duplicate records

Handled NULL values

Corrected inconsistent formats

Validated numeric and date fields

3️⃣ SQL Analysis (PostgreSQL)

Performed joins between customer and transaction tables

Calculated aggregated metrics (SUM, COUNT, AVG)

Extracted weekly and state-level insights

Validated business KPIs before dashboard modeling

4️⃣ Data Modeling in Power BI

Imported SQL data

Created relationships using Client_Num

Built calculated columns and measures using DAX


📐 DAX Calculations

🔹 Revenue Measure
Revenue =
SUM('Credit Card Details'[Total_Trans_Amt]) +
SUM('Credit Card Details'[Annual_Fees]) +
SUM('Credit Card Details'[Interest_Earned])

🔹 Age Group (Calculated Column)
Age_Group =
SWITCH(
    TRUE(),
    'Customer Details'[Customer_Age] < 30, "20-30",
    'Customer Details'[Customer_Age] >= 30 && 'Customer Details'[Customer_Age] < 40, "30-40",
    'Customer Details'[Customer_Age] >= 40 && 'Customer Details'[Customer_Age] < 50, "40-50",
    'Customer Details'[Customer_Age] >= 50 && 'Customer Details'[Customer_Age] < 60, "50-60",
    'Customer Details'[Customer_Age] >= 60, "60+",
    "Unknown"
)

🔹 Income Group (Calculated Column)
IncomeGroup =
SWITCH(
    TRUE(),
    'Customer Details'[Income] < 35000, "Low",
    'Customer Details'[Income] >= 35000 && 'Customer Details'[Income] < 70000, "Medium",
    'Customer Details'[Income] >= 70000, "High",
    "Unknown"
)

🔹 Week Number
WeekNum = WEEKNUM('Credit Card Details'[Week_Start_Date])

🔹 Current Week Revenue
Current_week_revenue =
CALCULATE(
    [Revenue],
    FILTER(
        ALL('Credit Card Details'),
        'Credit Card Details'[WeekNum] =
        MAX('Credit Card Details'[WeekNum])
    )
)

🔹 Previous Week Revenue
Previous_week_revenue =
CALCULATE(
    [Revenue],
    FILTER(
        ALL('Credit Card Details'),
        'Credit Card Details'[WeekNum] =
        MAX('Credit Card Details'[WeekNum]) - 1
    )
)

🔹 Week-on-Week Revenue %
WeekOnWeek_revenue =
DIVIDE(
    [Current_week_revenue] - [Previous_week_revenue],
    [Previous_week_revenue]
)

📊 Dashboard

The Power BI dashboard includes:

KPI Cards (Revenue, Interest, Transactions, Customer Count)

Weekly Revenue Trend (Line Chart)

Revenue by Gender (Bar Chart)

Revenue by State (Map Visualization)

Card Category Contribution (Donut Chart)

Age & Income Segmentation (Stacked Charts)

Week-on-Week Growth Indicator

The dashboard is fully interactive with slicers for:

Week

Card Category

Gender

State


📈 Results & Insights

Identified revenue contribution by demographic groups

Analyzed weekly revenue growth trends

Measured activation and delinquency rates

Found key revenue-contributing states

Evaluated high-performing card categories

The analysis enables stakeholders to monitor operational KPIs and make data-driven decisions.



🎯 Key Skills Demonstrated

SQL (Data Cleaning & Querying)

PostgreSQL

Data Modeling

DAX Calculations

Business KPI Development

Dashboard Design

Data Storytelling



📊 Project Insights

🔹  Project Insights for Week 53 (31st Dec)
Week-on-Week Change

Revenue increased by 28.8% compared to the previous week

Total Transaction Amount increased by XX%

Total Transaction Count increased by XX%

Customer Count increased by XX%

This indicates strong year-end spending behavior and higher customer engagement during the final week of the year.


🔹  Overview – Year-to-Date (YTD)

Overall Revenue: 57M

Total Interest Earned: 8M

Total Transaction Amount: 46M

👥 Revenue by Gender

Male customers contributed 31M

Female customers contributed 26M

💳 Card Category Contribution

Blue & Silver credit cards account for 93% of overall transactions

🌎 State-wise Contribution

TX, NY & CA contribute 68% of total revenue

📌 Portfolio Health Metrics

Overall Activation Rate: 57.5%

Overall Delinquent Rate: 6.06%

<img width="1999" height="1545" alt="image" src="https://github.com/user-attachments/assets/fd2f0dfd-5a34-4332-b304-a1af58cecbe7" />











    
