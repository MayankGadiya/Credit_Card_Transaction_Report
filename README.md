# Credit Card Transaction Report

### Objective:
To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.


1. Developed an interactive dashboard using transaction and customer data from a csv file, to provide real-time insights.
2. Streamlined data processing & analysis to monitor key performance metrics and trends.
3. Shared actionable insights with stakeholders based on dashboard findings to support decision-making processes.

### DAX QUERIES:
IncomeGroup = SWITCH(
    TRUE(),
    customer[Income] < 35000 ,  "Low",
    customer[Income] >= 35000 && customer[Income] < 70000, "Med",
    customer[Income] > 70000 , "High",
    "Unkown"
)

	AgeGroup = SWITCH(
    TRUE(),
    customer[Customer_Age] < 30, "20-30",
    customer[Customer_Age] >= 30 && customer[Customer_Age] < 40 , "30-40",
    customer[Customer_Age] >= 40 && customer[Customer_Age] < 50 , "40-50",
    customer[Customer_Age] >=50 && customer[Customer_Age] < 60 , "50-60",
    customer[Customer_Age] >= 60, "60+"
   		 )
	Week_num2 = WEEKNUM(credit_card[Week_Start_Date])

	Current_Week_Revenue = CALCULATE(
    			sum(credit_card[Revenue]), 
    			FILTER(
         		ALL (credit_card),
         		credit_card[Week_num2] = MAX(credit_card[Week_num2])))

Previous_Week_Revenue = CALCULATE(
     				sum(credit_card[Revenue]), 
     				FILTER(
         			ALL (credit_card),
        			credit_card[Week_num2] = MAX(credit_card[Week_num2])-1))



### Project Insights
Overview YTD:
• Overall revenue is 57M
• Total interest is 8M
• Total transaction amount is 46M
• Male customers are contributing more in revenue 31M, female 26M.
• Blue & Silver credit card are contributing to 93% of overall transactions
• TX, NY & CA is contributing to 68%
• Overall Activation rate is 57.5%
• Overall Delinquent rate is 6.06%
