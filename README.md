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

```sql
SELECT *
FROM product_emissions pe 
LIMIT 5;

```

|id|company_id|country_id|industry_group_id|year|product_name|weight_kg|carbon_footprint_pcf|upstream_percent_total_pcf|operations_percent_total_pcf|downstream_percent_total_pcf|
|--|----------|----------|-----------------|----|------------|---------|--------------------|--------------------------|----------------------------|----------------------------|
|10056-1-2014|82|28|2|2014|Frosted Flakes(R) Cereal|0.7485|2|57.50|30.00|12.50|
|10056-1-2015|82|28|15|2015|"Frosted Flakes, 23 oz, produced in Lancaster, PA (one carton)"|0.7485|2|57.50|30.00|12.50|
|10222-1-2013|83|28|8|2013|Office Chair|20.68|73|80.63|17.36|2.01|
|10261-1-2017|14|16|25|2017|Multifunction Printers|110.0|1488|30.65|5.51|63.84|
|10261-2-2017|14|16|25|2017|Multifunction Printers|110.0|1818|25.08|4.51|70.41|  
 

Table 'companies'  
id: Unique identifier for each company.  
company_name: The name of the company, identifying the specific organization within the dataset.  

```sql
SELECT *
FROM companies 
LIMIT 5;
```
|id|company_name|
|--|------------|
|1|"Autodesk, Inc."|
|2|"Casio Computer Co., Ltd."|
|3|"Cisco Systems, Inc."|
|4|"CNX Coal Resources, LP"|
|5|"Coca-Cola Enterprises, Inc."|  

 
Table 'countries'  
id: Unique identifier for each country.  
country_name: The name of the country.  

```sql
SELECT *
FROM countries 
LIMIT 5; 
```

|id|company_name|
|--|------------|
|1|"Autodesk, Inc."|
|2|"Casio Computer Co., Ltd."|
|3|"Cisco Systems, Inc."|
|4|"CNX Coal Resources, LP"|
|5|"Coca-Cola Enterprises, Inc."|

## 2. Project brief
 Project brief
You are required to analyze the data to answer the given questions and compile a comprehensive report in the repository on Github, which includes the following:

[❗mandatory] Logical division using headers of different levels.
[❗mandatory] Listings of SQL queries.
[❗mandatory] Tables with the results of SQL queries.
[❗mandatory] Text explanations for the executed queries.
[❗mandatory] Conclusions and insights based on the obtained database responses.
(where you can identify potentially useful insights, interesting facts, or patterns; for example, upon closer examination, it can be observed that the "Pharmaceuticals, Biotechnology & Life Sciences" industry is one of the leaders in carbon emissions - "Now we know what our health comes at.").
Additional requirements
[❗mandatory] The project report should begin with a description of the task and an overview of the tables (SQL query to each table for selecting all columns for the first 5-10 rows).
[❗mandatory] All fractional values should be rounded to 2 decimal places.
Optional points
[⭐️optional] Illustrations such as photographs (e.g., cover photo at the beginning of the report), graphs (e.g., graphs generated using MS Excel or Google Sheets based on data), diagrams (database schema), and others.
[⭐️optional] Any additional research and conclusions are welcome. For example:
Research of carbon emissions over continents.
Checking correlations, such as the correlation between product weight and carbon emissions levels.
Exploring the environmental friendliness of industrial sectors.
🛠️ Tools to use
To execute this project, you are encouraged to utilize any tools they find useful without limitations.

However, we have prepared a set of tools that will greatly assist them in completing the project:

Online SQL Console: Link to SQL Console
(⚠️ Note that at the bottom of the SQL console, there is a panel for conveniently generating Markdown code, which will aid you in report formatting for Github).

Online Markdown Editor: Link to Markdown Editor
(This editor is ideal for writing and formatting Markdown code for the report. It features a toolbar for quick text formatting in Markdown, even if the student is not proficient in writing Markdown code independently.
⚠️ Additionally, it is recommended to write the report in this editor, as it saves the code every second, preventing situations where the student accidentally loses their work without saving).

You can also connect to the database and execute queries using any MySQL-compatible client, including DBeaver.

 

Connection details for a database client 
(only if you decided not to use online console, that is highly discouraged): 

Host/Server	112.213.86.31
Port	3360
Username	marshmallow
Password	N3unkNbXQYh33og
Database	carbon_emissions

## 3. Questions to research

1. Which products contribute the most to carbon emissions?

```sql
SELECT 
	industry_group_id,
	product_name,
	ROUND(AVG(carbon_footprint_pcf)) AS 'Carbon emissions'
FROM product_emissions pe 
GROUP BY product_name
ORDER BY ROUND(AVG(carbon_footprint_pcf)) DESC;
```
|industry_group_id|product_name|Carbon emissions|
|-----------------|------------|----------------|
|13|Wind Turbine G128 5 Megawats|3718044|
|13|Wind Turbine G132 5 Megawats|3276187|
|13|Wind Turbine G114 2 Megawats|1532608|
|13|Wind Turbine G90 2 Megawats|1251625|
|7|Land Cruiser Prado. FJ Cruiser. Dyna trucks. Toyoace.IMV def unit.|191687|

2. What are the industry groups of these products?
3. What are the industries with the highest contribution to carbon emissions?
```sql
SELECT
	i.industry_group,
	p.product_name,
	ROUND(AVG(carbon_footprint_pcf)) AS 'Carbon emissions'
FROM product_emissions AS p
JOIN industry_groups AS i ON p.industry_group_id = i.id
GROUP BY p.product_name
ORDER BY ROUND(AVG(carbon_footprint_pcf)) DESC
LIMIT 5;
```
|industry_group|product_name|Carbon emissions|
|--------------|------------|----------------|
|Electrical Equipment and Machinery|Wind Turbine G128 5 Megawats|3718044|
|Electrical Equipment and Machinery|Wind Turbine G132 5 Megawats|3276187|
|Electrical Equipment and Machinery|Wind Turbine G114 2 Megawats|1532608|
|Electrical Equipment and Machinery|Wind Turbine G90 2 Megawats|1251625|
|Automobiles & Components|Land Cruiser Prado. FJ Cruiser. Dyna trucks. Toyoace.IMV def unit.|191687|

4. What are the companies with the highest contribution to carbon emissions?

```sql
SELECT
	c.company_name,
	p.product_name,
	ROUND(SUM(carbon_footprint_pcf)) AS 'Carbon emissions'
FROM product_emissions AS p 
JOIN companies AS c ON c.id=p.company_id
GROUP BY c.company_name
ORDER BY ROUND(AVG(carbon_footprint_pcf)) DESC
LIMIT 5;
```
|company_name|product_name|Carbon emissions|
|------------|------------|----------------|
|"Gamesa Corporación Tecnológica, S.A."|Wind Turbine G90 2 Megawats|9778464|
|"Hino Motors, Ltd."|Land Cruiser Prado. FJ Cruiser. Dyna trucks. Toyoace.IMV def unit.|191687|
|Arcelor Mittal|Organic coated coil for the Nature product range (which includes the products Granite® and Estetic®) having a mean surface mass of 4.7kg. The Nature range of innovative chromium-free organic coated steels for the construction industry is the result of 15 years of research in partnership with paint suppliers to develop safer and greener corrosion-inhibiting pigments.|167007|
|Weg S/A|Electric Motor|160655|
|Daimler AG|Mercedes-Benz CLS-Class|1594300|

5. What are the countries with the highest contribution to carbon emissions?

```sql
SELECT
	t.country_name,
	p.product_name,
	ROUND(SUM(carbon_footprint_pcf)) AS 'Carbon emissions'
FROM product_emissions AS p
JOIN countries AS t ON t.id = p.country_id
GROUP BY t.country_name
ORDER BY ROUND(SUM(carbon_footprint_pcf)) DESC
LIMIT 5;
```
|country_name|product_name|Carbon emissions|
|------------|------------|----------------|
|Spain|Filtro 26 WS|9786130|
|Germany|VW Polo V 1.6 TDI BlueMotion Technology|2251225|
|Japan|Multifunction Printers|653237|
|USA|Frosted Flakes(R) Cereal|518381|
|South Korea|Mobile Batteries|186965|

6. What is the trend of carbon footprints (PCFs) over the years?

```sql
SELECT
	year,
	ROUND(SUM(t.avg_carbon_footprint_pcf)) AS total_emissions_by_year
FROM 
	(
		SELECT
			year,
			product_name,
			AVG(carbon_footprint_pcf) AS avg_carbon_footprint_pcf
		FROM product_emissions
		GROUP BY year, product_name 
	) AS t
GROUP BY year;
```
|year|total_emissions_by_year|
|----|-----------------------|
|2013|496006|
|2014|548214|
|2015|10810407|
|2016|1608962|
|2017|224800|

7. Which industry groups has demonstrated the most notable decrease in carbon footprints (PCFs) over time?

```sql
SELECT
    ig.industry_group AS 'Industry Group',
    ROUND(SUM(CASE WHEN pe.year = 2013 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS '2013 Emission',
    ROUND(SUM(CASE WHEN pe.year = 2014 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS '2014 Emission',
    ROUND(SUM(CASE WHEN pe.year = 2015 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS '2015 Emission',
    ROUND(SUM(CASE WHEN pe.year = 2016 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS '2016 Emission',
    ROUND(SUM(CASE WHEN pe.year = 2017 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS '2017 Emission'
FROM product_emissions AS pe
LEFT JOIN industry_groups AS ig ON ig.id = pe.industry_group_id
GROUP BY ig.industry_group
ORDER BY 
'2017 Emission', 
'2016 Emission', 
'2015 Emission', 
'2014 Emission', 
'2013 Emission';
```

|Industry Group|2013 Emission|2014 Emission|2015 Emission|2016 Emission|2017 Emission|
|--------------|-------------|-------------|-------------|-------------|-------------|
|"Food, Beverage & Tobacco"|4995.00|2685.00|0.00|100289.00|3162.00|
|Food & Beverage Processing|0.00|0.00|141.00|0.00|0.00|
|Capital Goods|60190.00|93699.00|3505.00|6369.00|94949.00|
|Technology Hardware & Equipment|61100.00|167361.00|106157.00|1566.00|27592.00|
|Materials|200513.00|75678.00|0.00|88267.00|213137.00|
|Consumer Durables & Apparel|2867.00|3280.00|0.00|1162.00|0.00|
|"Textiles, Apparel, Footwear and Luxury Goods"|0.00|0.00|387.00|0.00|0.00|
|Software & Services|6.00|146.00|22856.00|22846.00|690.00|
|Chemicals|0.00|0.00|62369.00|0.00|0.00|
|Semiconductors & Semiconductor Equipment|0.00|50.00|0.00|4.00|0.00|
|Commercial & Professional Services|1157.00|477.00|0.00|2890.00|741.00|
|Retailing|0.00|19.00|11.00|0.00|0.00|
|Utilities|122.00|0.00|0.00|122.00|0.00|
|Gas Utilities|0.00|0.00|122.00|0.00|0.00|
|Telecommunication Services|52.00|183.00|183.00|0.00|0.00|
|Electrical Equipment and Machinery|0.00|0.00|9801558.00|0.00|0.00|
|Containers & Packaging|0.00|0.00|2988.00|0.00|0.00|
|"Mining - Iron, Aluminum, Other Metals"|0.00|0.00|8181.00|0.00|0.00|
|Media|9645.00|9645.00|1919.00|1808.00|0.00|
|Automobiles & Components|130189.00|230015.00|817227.00|1404833.00|0.00|
|"Pharmaceuticals, Biotechnology & Life Sciences"|32271.00|40215.00|0.00|0.00|0.00|
|Tires|0.00|0.00|2022.00|0.00|0.00|
|Trading Companies & Distributors and Commercial Services & Supplies|0.00|0.00|239.00|0.00|0.00|
|"Forest and Paper Products - Forestry, Timber, Pulp and Paper, Rubber"|0.00|0.00|8909.00|0.00|0.00|
|"Consumer Durables, Household and Personal Products"|0.00|0.00|931.00|0.00|0.00|
|Energy|750.00|0.00|0.00|10024.00|0.00|
|Food & Staples Retailing|0.00|773.00|706.00|2.00|0.00|
|Household & Personal Products|0.00|0.00|0.00|0.00|0.00|
|Tobacco|0.00|0.00|1.00|0.00|0.00|
|Semiconductors & Semiconductors Equipment|0.00|0.00|3.00|0.00|0.00|












