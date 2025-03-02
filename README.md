# Telecom-Dashboard
Power BI dashboard analyzing the effects of 5G plans in India.  

Problem Statement:
Why is there a decline in active users and revenue growth post-5G launch?

Step 1) 
Run basic queries in SQL to understand the dataset 

Step 2)
Clean data & create relationships between tables in Power BI 

Step 3) 
Build Dashboard

> Page 1 called "Before and after 5G (users/revenue)"

This page showcases the difference in values between active users and unsubscribed users, the average revenue per user (ARPU), and the overall revenue. 

This includes a calculation of an attribute like:

Active Users Before 5G = CALCULATE( SUM(fact_atliqo_metrics[active_users_lakhs]), FILTER( dim_date, dim_date[before/after_5g] = "Before 5G" ) )

Active Users After 5G = CALCULATE( SUM(fact_atliqo_metrics[active_users_lakhs]), FILTER( dim_date, dim_date[before/after_5g] = "After 5G" ) )

Then, using those attributes to calculate the percent change: 

% Change in Active Users = 
VAR ActiveUsersBefore5G = CALCULATE([Active Users Before 5G], ALLSELECTED('dim_date'))
VAR ActiveUsersAfter5G = CALCULATE([Active Users After 5G], ALLSELECTED('dim_date'))
RETURN DIVIDE(
    ActiveUsersAfter5G - ActiveUsersBefore5G,
    ActiveUsersBefore5G,
    0
) * 100

The same was done for all other attributes, including ARPU, User data, Market share, and type of plans. 

> Page 2: "Before and after 5G (plan/market)" 

This page showcases the differences between market share % changes and the changes in revenue as per different plans. 

> Page 3: "Overview of plan revenue and market share" 
Provides a visualization of the market share % of each company and the revenue per plan

Step 4) Analyze in Python

Outcome: Utilizing both paired t-test and ANOVA testing, it was found that the only attribute with a significant change before and after introducing 5G was ARPU (Average Revenue Per User), which showed a positive change. Enhanced network performance, for instance, could drive increased data usage, and lower latency might improve the overall customer experience. Consequently, understanding the causes of increased ARPU and developing innovative solutions—such as offering bundled packages, attractive deals, or strategic pricing to offset costs—would be the next logical step.

However, given that the paired t-test results showed a decline in active users and an increase in unsubscribed users, the initial focus should be further research into ARPU (Average Revenue Per User). Additionally, it is equally important to identify other attributes that may have contributed to user unsubscription with time series analysis and more data. 

 Telecom Dashboard (Excel, Power BI, SQL, Python)
![Screen Shot 2025-02-21 at 8 09 38 PM](https://github.com/UserDna95/Telecom-Dashboard/blob/main/2025-02-21.png)
![Screen Shot 2025-02-21 at 8 09 38 PM](https://github.com/UserDna95/Telecom-Dashboard/blob/main/2025-02-21%20(1).png)
![Screen Shot 2025-02-21 at 8 09 38 PM](https://github.com/UserDna95/Telecom-Dashboard/blob/main/2025-02-21%20(2).png)
