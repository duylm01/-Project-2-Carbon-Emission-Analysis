# -Project-2-Carbon-Emission-Analysis
## 1. Introduction
What is the project about?  
![image](https://github.com/user-attachments/assets/f23021ab-a542-43ad-8c83-2e2e1ed9b2c0)  
Photo by Chris LeBoutillier (unsplash.com)  

This report aims to analyze carbon emissions to examine the carbon footprint across various industries. We aim to identify sectors with the highest levels of emissions by analyzing them across countries and years, as well as to uncover trends.  

Carbon emissions play a crucial role in the environment, accounting for over 75% of global emissions and posing a significant environmental challenge. These emissions contribute to the accumulation of greenhouse gases in the atmosphere, leading to climate change, planetary warming, and involvement in various environmental disasters.  

Through this analysis, we hope to gain an understanding of the environmental impact of different industries and contribute to making informed decisions in sustainable development.  

## Data Source: Where Our Data Comes From  
Our dataset is compiled from publicly available data from nature.com and encompasses the product carbon footprints (PCF) for various companies. PCFs represent the greenhouse gas emissions associated with specific products, quantified in CO2 (carbon dioxide equivalent).  

## Data Structure  
The dataset consists of 4 tables containing information regarding carbon emissions generated during the production of goods.  
![image](https://github.com/user-attachments/assets/96cf50c1-ebe1-4d12-9b56-8b6b0ca924b2)  

## Tables' columns description  
1) Table 'product_emissions'  
2) id: Identifier for each product emission record.  
3) company_id: Identifier for the company associated with the product.  
4) country_id: Identifier for the country where the product is being produced.
5) industry_group_id: Identifier for the industry group to which the product belongs.
6) year: The year in which the emissions data was recorded.
7) product_name: The name of the product associated with the emissions data.
8) weight_kg: The weight of the product in kilograms.
9) carbon_footprint_pcf: The carbon footprint of the product, measured in CO2 equivalent.
10) upstream_percent_total_pcf: The percentage of the total carbon footprint attributed to upstream activities.
11) operations_percent_total_pcf: The percentage of the total carbon footprint attributed to operations.
12) downstream_percent_total_pcf: The percentage of the total carbon footprint attributed to downstream activities.

Table 'industry_groups'
id: Unique identifier for each industry group.
industry_group: The name of the industry group, categorizing businesses within similar sectors based on their products or services offered.
 

Table 'companies'  
id: Unique identifier for each company.  
company_name: The name of the company, identifying the specific organization within the dataset.  
 

Table 'countries'  
id: Unique identifier for each country.  
country_name: The name of the country.  







