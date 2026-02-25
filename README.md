# Credit_Card_Financial_Dashboard
Credit Card Transaction and Customer Dashboard using Power BI

1. Project Objective:- 
To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.


3. Import data to SQL database 
1. Prepare csv file into UTF-8 format
2. Create database / tables in SQL
3. import UTF-8 file into SQL


3. Imported data into Power BI to perform DAX Queries:
DAX:
Revenue = SUM('Credit Card Details'|Total_Trans_Amt]) + SUM('Credit Card Details'[Annual _Fees]) + SUM('Credit Card
Details'[Interest_Earned])

DAX:
Age_Group =
SWITCH
TRUE(),
'Customer Details'[Customer_Age) < 30, '20-30",
'Customer Details'|Customer_Age) >= 30 && 'Customer Details'[Customer _Age) < 40, "30-40",
'Customer Details'[Customer _Age] >= 40 && 'Customer Details'[Customer_Age] < 50, "40-50",
'Customer Details'(Customer_Age] >= 50 && 'Customer Details'[Customer _Age] « 60, "50-60",
'Customer Details'[Customer_Age] ≥= 60, "60+",
"Unknown")

DAX:
IncomeGroup = 
SWITCH(TRUE(), 
     'public cust_detail'[income] < 3500, "Low", 
     'public cust_detail'[income] >= 3500 && 'public cust_detail'[income] < 70000, "Medium",       
     'public cust_detail'[income] >= 70000, "High", "Unknown")

DAX:
WeekNum = WEEKNUM('public cc_detail'[week_start_date])

DAX:
Current_week_revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        All('public cc_detail'),'public cc_detail'[WeekNum] = MAX('public cc_detail'[WeekNum])))


DAX:
previous_week_revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
   FILTER(
        ALL('public cc_detail'), 'public cc_detail'[WeekNum] = MAX('public cc_detail'[WeekNum]) -1))

DAX:
WeekOnweek_revenue = DIVIDE(
    ([Current_week_revenue] - [previous_week_revenue]), [previous_week_revenue])



Project Insights for Week 53 (31st Dec):-
Week On Week change:
Revenue increased by 28.8%,
Total Transaction Amt & Count increased by xx% & xx%
* Customer count increased by xx%
Overview YTD:
* Overall revenue is 57M
Total interest is 8M
* Total transaction amount is 46M
Male customers are contributing more in revenue 31M, female 26M
Blue & Silver credit card are contributing to 93% of overall transactions
TX, NY & CA is contributing to 68% Overall Activation rate is 57.5% Overall Delinquent rate is 6.06%



    
