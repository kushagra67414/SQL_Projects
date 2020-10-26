Let's Start the Project

## Task-1 : Instruction

```
Inspect the international debt data.

Read the line of code provided for you, which connects you to the international_debt database.
Select all of the columns from the international_debt table and limit the output to the first 10 rows.
Good to know
The only prerequisite to complete this project is familiarity with the contents covered in DataCamp's Intro to SQL for Data Science course.

SQL DataCamp projects are completed in Jupyter Notebooks. If you're not familiar with Jupyter Notebooks, that's okay! All you need to know is that you can execute SQL commands in the code cells provided, as long as you have %%sql at the top of them. If you'd like more info on Jupyter Notebooks, go here.

If you experience odd behavior you can reset the project by clicking the circular arrow in the bottom-right corner of the screen. Resetting the project will discard all code you have written so be sure to save it offline first.
```
* The World Bank's international debt data

```It's not that we humans only take debts to manage our necessities. A country may also take debt to manage its economy. For example, infrastructure spending is one costly ingredient required for a country's citizens to lead comfortable lives. The World Bank is the organization that provides debt to countries.
In this notebook, we are going to analyze international debt data collected by The World Bank. The dataset contains information about the amount of debt (in USD) owed by developing countries across several categories. We are going to find the answers to questions like:
•	What is the total amount of debt that is owed by the countries listed in the dataset?
•	Which country owns the maximum amount of debt and what does that amount look like?
•	What is the average amount of debt owed by countries across different debt indicators?
```
![1](https://user-images.githubusercontent.com/46487696/97202436-a051f580-17d9-11eb-9da0-aae3e6242011.jpg)

```
The first line of code connects us to the international_debt database where the table international_debt is residing. 
Let's first SELECT all of the columns from the international_debt table.
Also, we'll limit the output to the first ten rows to keep the output clean.
```

```
## ANSWER :
    In [37]: 
    %%sql
    postgresql:///international_debt

    SELECT *
    FROM international_debt
    LIMIT 10;
``` 
```

Out[37]:
country_name	country_code	          indicator_name	                                indicator_code  	debt
Afghanistan	 AFG	  Disbursements on external debt, long-term (DIS, current US$)	    DT.DIS.DLXF.CD	  72894453.700000003
Afghanistan	 AFG	  Interest payments on external debt, long-term (INT, current US$)	DT.INT.DLXF.CD	  53239440.100000001
Afghanistan	 AFG	  PPG, bilateral (AMT, current US$)	                                DT.AMT.BLAT.CD	  61739336.899999999
Afghanistan	 AFG	  PPG, bilateral (DIS, current US$)	                                DT.DIS.BLAT.CD	  49114729.399999999
Afghanistan	 AFG	  PPG, bilateral (INT, current US$)	                                DT.INT.BLAT.CD  	39903620.100000001
Afghanistan	 AFG	  PPG, multilateral (AMT, current US$)                             	DT.AMT.MLAT.CD	  39107845
Afghanistan	 AFG	  PPG, multilateral (DIS, current US$)	                            DT.DIS.MLAT.CD	  23779724.300000001
Afghanistan	 AFG	  PPG, multilateral (INT, current US$)	                            DT.INT.MLAT.CD	  13335820
Afghanistan	 AFG	  PPG, official creditors (AMT, current US$)                       	DT.AMT.OFFT.CD  	100847181.900000006
Afghanistan	 AFG	  PPG, official creditors (DIS, current US$)                        DT.DIS.OFFT.CD  	72894453.700000003

```
## Task-2: Instructions
* Finding the number of distinct countries
```
Find the number of distinct countries.

Use the DISTINCT clause and the COUNT() function in pair on the country_name column.
Alias the resulting column as total_distinct_countries.
Jupyter Notebook trick: if you click the white area to the left of the output for this task's code cell, the output area will be collapsed and become scrollable.
```
```
From the first ten rows, we can see the amount of debt owed by Afghanistan in the different debt indicators.
But we do not know the number of different countries we have on the table. 
There are repetitions in the country names because a country is most likely to have debt in more than one debt indicator.

Without a count of unique countries, we will not be able to perform our statistical analyses holistically.
In this section, we are going to extract the number of unique countries present in the table.
```
```
ANSWER:
    In [39]: 
    %%sql
    SELECT 
        COUNT(DISTINCT country_name) AS total_distinct_countries
    FROM international_debt;
     * postgresql:///international_debt
    1 rows affected.
```
```
Out[39]:
total_distinct_countries
124
```
