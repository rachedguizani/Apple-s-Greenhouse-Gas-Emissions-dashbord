# Apple's Greenhouse Gas Emissions (dashbord)

# Data understanding
The dataset includes three CSV tables (available top in the main):

-Greenhouse Gas Emissions: Lists Apple’s greenhouse gas emissions from 2015 to 2022, categorized by source (corporate vs. product life cycle), scope (direct Scope 1, indirect Scopes 2 and 3), and type (emissions vs. removals).

-Carbon Footprint by Product: Details emissions from the product life cycle for each baseline iPhone model released between 2015 and 2022.

-Normalizing Factors: Contains Apple’s revenue, market cap, and employee counts for the same period.
# Data Modelling: Then dataset was cleaned and transformed, it was ready for data modeled.
input :

![image](https://github.com/user-attachments/assets/a71ae574-8185-4596-8bd3-9a262877850a)

output : we create star shema using Power Query (star schema is a type of relational database schema consisting of a single central fact table surrounded by dimension tables)

![image](https://github.com/user-attachments/assets/6f2ab3a7-ea7c-476a-8627-dea79da9dd52)

Fact_analyse: - We recovered the primary keys of each dimension                                                                                                          
              - Contains our measurements  
              
![image](https://github.com/user-attachments/assets/291d2626-7bb4-4682-8d69-32edc144b456)
# Data Analysis Expression (DAX) Calculation :
Measures used for the visualization:

•	avg_carbone_footprint = AVERAGE(dim_produit[Carbon Footprint] )
•	Taux de reduction = 
VAR Emissions2022 = CALCULATE(fact_analyse[Total_emission], dim_periode[Year] = 2022)
VAR Emissions2015 = CALCULATE(fact_analyse[Total_emission], dim_periode[Year] = 2015)
RETURN
DIVIDE(Emissions2022 - Emissions2015, Emissions2015)

•	Total_emission = SUM(dim_source_emission[Emissions] )

•	Total_employees = SUM(dim_economique[Employees])

•	Total_market_capitalization = SUMX(dim_economique,dim_economique[Market Capitalization] )

•	Total_revenu = SUMX(dim_economique,dim_economique[Revenue] )

•	Revenue Growth Rate = VAR CurrentYearRevenue = SUMX(FILTER('dim_economique', 'dim_economique'[Fiscal Year] = MAX('dim_economique'[Fiscal Year])), 'dim_economique'[Revenue]) VAR PreviousYearRevenue = SUMX(FILTER('dim_economique', 'dim_economique'[Fiscal Year] = MAX('dim_economique'[Fiscal Year]) - 1), 'dim_economique'[Revenue]) RETURN DIVIDE(CurrentYearRevenue - PreviousYearRevenue, PreviousYearRevenue) 

•	Market Capitilation Growth Rate = VAR CurrentYearRevenue = SUMX(FILTER('dim_economique', 'dim_economique'[Fiscal Year] = MAX('dim_economique'[Fiscal Year])), 'dim_economique'[Market Capitalization]) VAR PreviousYearRevenue = SUMX(FILTER('dim_economique', 'dim_economique'[Fiscal Year] = MAX('dim_economique'[Fiscal Year]) - 1), 'dim_economique'[Market Capitalization]) RETURN DIVIDE(CurrentYearRevenue - PreviousYearRevenue, PreviousYearRevenue) 

•	Employees Growth Rate = VAR CurrentYearEmployees = SUMX(FILTER('dim_economique', dim_economique[Fiscal Year] = MAX(dim_economique[Fiscal Year])), dim_economique[Employees]) VAR PreviousYearEmployees = SUMX(FILTER('dim_economique', dim_economique[Fiscal Year] = MAX(dim_economique[Fiscal Year]) - 1), 'dim_economique'[Employees]) RETURN DIVIDE(CurrentYearEmployees - PreviousYearEmployees, PreviousYearEmployees)

•	Taux revenu between 2015 ET 2022 = 
VAR RE2022 = CALCULATE(fact_analyse[Total_revenu], dim_periode[Year] = 2022)
VAR RE2015 = CALCULATE(fact_analyse[Total_revenu], dim_periode[Year] = 2015)
RETURN
DIVIDE(RE2022 - RE2015, RE2015)

# 📈 Dashbord :
Data visualization was done using Microsoft Power BI Desktop 

![image](https://github.com/user-attachments/assets/562f4d4b-245a-4275-8f18-7a639bfd195f)
![image](https://github.com/user-attachments/assets/bbfbc90d-62e2-4a07-ae0f-e297325ef6c2)
![image](https://github.com/user-attachments/assets/ce21c37c-41c8-4cbc-b62a-08f0bd9381d3)
![image](https://github.com/user-attachments/assets/5cb44e94-3570-4659-b422-e65d158c9e1f)










                                          



