# Apple's Greenhouse Gas Emissions (dashbord)

# Data understanding
The dataset includes three CSV tables:

-Greenhouse Gas Emissions: Lists Apple’s greenhouse gas emissions from 2015 to 2022, categorized by source (corporate vs. product life cycle), scope (direct Scope 1, indirect Scopes 2 and 3), and type (emissions vs. removals).

-Carbon Footprint by Product: Details emissions from the product life cycle for each baseline iPhone model released between 2015 and 2022.

-Normalizing Factors: Contains Apple’s revenue, market cap, and employee counts for the same period.
# Data Modelling:
input :

![image](https://github.com/user-attachments/assets/a71ae574-8185-4596-8bd3-9a262877850a)

output : we create star shema using Power Query (star schema is a type of relational database schema consisting of a single central fact table surrounded by dimension tables)

![image](https://github.com/user-attachments/assets/6f2ab3a7-ea7c-476a-8627-dea79da9dd52)

Fact_analyse: - We recovered the primary keys of each dimension
              - Contains our measurements                                                  ![image](https://github.com/user-attachments/assets/9fed573a-6dcc-4097-b86b-6f53c5c9d9ab)

                                          



