# Credit_Card_Financial_Dashboard
Credit Card Transaction and Customer Dashboard using Power BI

1. Project Objective:- 
To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.


3. Import data to SQL database:-
Prepare csv file into UTF-8 format
Create database / tables in SQL
Import UTF-8 file into SQL


3. Imported SQL data into Power BI to perform DAX Queries:
DAX:
Revenue = SUM('Credit Card Details'|Total_Trans_Amt]) + SUM('Credit Card Details'[Annual _Fees]) + SUM('Credit Card
Details'[Interest_Earned])

3.1 DAX:
Age_Group =
SWITCH
TRUE(),
'Customer Details'[Customer_Age) < 30, '20-30",
'Customer Details'|Customer_Age) >= 30 && 'Customer Details'[Customer _Age) < 40, "30-40",
'Customer Details'[Customer _Age] >= 40 && 'Customer Details'[Customer_Age] < 50, "40-50",
'Customer Details'(Customer_Age] >= 50 && 'Customer Details'[Customer _Age] « 60, "50-60",
'Customer Details'[Customer_Age] ≥= 60, "60+",
"Unknown")

3.2 DAX:
IncomeGroup = 
SWITCH(TRUE(), 
     'public cust_detail'[income] < 3500, "Low", 
     'public cust_detail'[income] >= 3500 && 'public cust_detail'[income] < 70000, "Medium",       
     'public cust_detail'[income] >= 70000, "High", "Unknown")

3.3 DAX:
WeekNum = WEEKNUM('public cc_detail'[week_start_date])

3.4 DAX:
Current_week_revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        All('public cc_detail'),'public cc_detail'[WeekNum] = MAX('public cc_detail'[WeekNum])))


3.5 DAX:
previous_week_revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
   FILTER(
        ALL('public cc_detail'), 'public cc_detail'[WeekNum] = MAX('public cc_detail'[WeekNum]) -1))

3.6 DAX:
WeekOnweek_revenue = DIVIDE(
    ([Current_week_revenue] - [previous_week_revenue]), [previous_week_revenue])



4. Project Insights for Week 53 (31st Dec):-
4.1 Week On Week change
-Revenue increased by 28.8%,
-Total Transaction Amt & Count increased by xx% & xx%
-Customer count increased by xx%

4.2 Overview YTD:
-Overall revenue is 57M
-Total interest is 8M
-Total transaction amount is 46M
-Male customers are contributing more in revenue 31M, female 26M
-Blue & Silver credit card are contributing to 93% of overall transactions
-TX, NY & CA is contributing to 68% Overall Activation rate is 57.5% Overall Delinquent rate is 6.06%



    
