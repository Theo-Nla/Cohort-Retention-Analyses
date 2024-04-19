# Cohort-Retention-Analyses

# Introduction
This project performs cohort retention analysis on an online retail sales dataset using SQL for data manipulation and Tableau for visualization.
Cohort retention analysis is a valuable technique for businesses to understand how different groups of customers behave over time. By grouping customers based on shared characteristics or experiences, this analysis helps uncover patterns in customer retention and informs strategies for improving customer engagement and loyalty.

## Dataset
The dataset used for this analysis is obtained from the UCI Machine Learning Repository. It contains information on customer IDs, invoice details, product descriptions, quantities, and prices.

## Analysis Steps
1.	** Data Cleaning:** The dataset is cleaned to remove duplicates and records with missing customer IDs.

2.	**Cohort Creation:** Customers are grouped into cohorts based on their first purchase dates.
```
Select
Customerid,
min(InvoiceDate) first_purchase_date,
DATEFROMPARTS(year(min(InvoiceDate)), month(min(InvoiceDate)),1) Cohort_Date
into #cohort
from #Clean_Online_Retail
group by CustomerID
```

3.	**Cohort Retention Analysis:** Cohort retention rates are calculated to track how many customers from each cohort remain active over subsequent months.
```
select Cohort_Date , 
1.0 *[1]/[1] * 100 as [1],
1.0 *[2]/[1] * 100 as [2],
1.0 *[3]/[1] * 100 as [3],
1.0 *[4]/[1] * 100 as [4],
1.0 *[5]/[1] * 100 as [5],
1.0 *[6]/[1] * 100 as [6],
1.0 *[7]/[1] * 100 as [7],
1.0 *[8]/[1] * 100 as [8],
1.0 *[9]/[1] * 100 as [9],
1.0 *[10]/[1] * 100 as [10],
1.0 *[11]/[1] * 100 as [11],
1.0 *[12]/[1] * 100 as [12],
1.0 *[13]/[1] * 100 as [13]
from #cohort_pivot
order by Cohort_Date
```

4.	**Tableau Visualization:** The cohort retention rates are visualized in Tableau to identify trends and patterns.

## Tableau Visualization
The Tableau visualization of cohort retention rates is available here.

![Cohort Table](https://github.com/Theo-Nla/Cohort-Retention-Analyses/assets/135545087/b0d32205-436f-4e35-96b8-5a9a814a7079)

**Cohort Table**

![Cohort Retention Dashboard (1)](https://github.com/Theo-Nla/Cohort-Retention-Analyses/assets/135545087/77b6c3d3-a4c3-49f8-908a-c7b4262752a2)

**Cohort Retention Rate**
