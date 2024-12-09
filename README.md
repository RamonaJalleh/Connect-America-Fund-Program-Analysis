# Connect America Overview
Connect America was created about 10 years ago to disburse funding to Eligible Telecommunications Carriers to provide voice and broadband services in rural America. This project reviews  data from 2024  back to 2014 and analyzes budget allocation, spending trends, disparities and compliance within the program. This large data set before it was cleaned and prepared contained 1,048,569 rows of data. 

## Table of Contents

[Connect America Overview](#connect-america-overview)

[Recommendations](#recommendations)

[Referenecs](#referenecs)



## Tools that were used 
- Excel - Data Cleaning 
- MySQL - Data Analysis 
- Tablaeu - Visulizations and reports 

### Data Cleaning/Preperation 
In the initial data preperation phase, the following tasks were performed: 
1. Trimming 
2. Formatting
3. Removing Duplicates 
4. Dropping rows 

### The data from this dashboard are results of SQL Queries that sought out to: 
- identify areas with the largest desicrepancies between capped and uncapped disbursements
- calculate average monthly allocations per state for each fund type
- determind year-over-year disbursemtn growth or delcine
- find the rolling 3-month average disbursement
- discover any funding disparities across regions
- identify areas receiving below average funding
- identify which carriers receive more of less than the average allocated budget
- track how grequently funds are delayed or below allocation

```sql
SELECT state, 
	SUM(uncapped_support-capped_support) AS Discrepancy
FROM StudyArea
JOIN Funding
ON StudyArea.Form_ID = Funding.Form_ID
GROUP BY SAC, StudyArea_Name, State
Order By Discrepancy DESC
LIMIT 10;
```

You can find all queries used for this visualization under file "Connet America Queries.txt "

### Results / Findings 
- 3 Rivers Telephone Cooperative and Accipiter Communications, are areas with the largest descrepancy between capped an uncapped disbursements
- In 2017 only .92% on of the budget was being utilized. Underutilization of disbursements can result in delays in expanding broadband acesses. We can see that by 2020 .99% of the budget was being utilized
- Montana had the highest increase in year-over-year change which indicaes strong progress in broadband serive deployment to targeted rural areas.
- Seeing a heavier amount of delayed disbursements between September - December which could indicate seasonal challenges in implemnting projects or a lag of fund utilization and preparation for the year-end-reporting cycle. 

### Recommendations 
- The areas with large discrepancy may indicate funding limitations due to capping and could use additional support. Uregent Reveiew is suggested
- Conduct further analysis into what strategies were put into place and duplicated across the board to increase utilization percentages. 
- With such a strong year-over-year increase, would recommend further analysis into Montana's strategy,  as service deployment to targeted rural areas is the overall goal.
- Enhance funding allocation efficency by aligning disbursements with project timelines this should help reduce delays. Also optimize scheduling to account for season and year-end challenges. 

### Referenecs 
[USAC Open DATA] (https://opendata.usac.org/High-Cost/High-Cost-Detailed-Payment-Tool-Data-Payments-/54bu-6jcj/about_data) 




