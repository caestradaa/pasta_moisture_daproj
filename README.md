# Project: Pasta Moisture Data Analysis
*Exploratory data analysis on pasta moisture (food industry) for manufacturing efficiency improvement.*

## Overview
- In this research work, a deep analysis on the moisture data of pasta in a food factory was carried out, in order to answer questions and help make decisions to improve the efficiency of the pasta drying process.
- Data obtained from moisture testers through an IOT data capture system and stored on a csv file. 2 final datasets, 14.121 rows.
- Project tools: Power BI for ETL and graphics, Infostat for statistics, Excel. <!--- Important insights:-->
- Built a formal report.

<!--### Code and Resourses Used-->
## Problem statement and hypothesis
The challenge of the pasta drying process is to be able to obtain the highest possible moisture results in the finished product without entailing a risk of non-conforming product by exceeding the maximum legal level of 13.00%. The objective of the production team, and the business in general, is to reach the range of 12.30% - 12.50%.

This data analytical approach was made to answer specific questions and check some hypotheses about the actual pasta drying process, and help detect pain-points where opportunities can be capitalized. Some of the most importants are:
- Which production line/pasta format has the most variant moisture results? Which pasta format tends to be dryer?
- Does the weight of the pasta samples have any significant impact on the results of the moisture testers?
- How much moisture does the pasta lose from the end of the cooling stage to the cutting stage, resting in the storage silo?
- Will it be necessary to modify the drying recipes individually for each drying cell instead of having a single modified recipe for all?

## Data Collection
The main database is composed by the moisture test results of the pasta from all production lines. The pasta moisture is measured at different stages of the drying process using moisture testers, and the obtained data is transferred via an IoT divice to a csv file on the cloud. Raw data preview table:

![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Raw_data_preview.png "Raw data preview")

<!--Fecha Final: Date and Time
Linea: production line
Referencia: pasta format
Zona: drying zone where the pasta sample is taken
Resultado: moisture test result
Duración: moisture test time duration
Peso Muestra: sample initial weight
Peso Final: sample final weight
Temperatura: moisture test temperature (°C)
Serial: tester ID serial-->

## Data Cleaning
Ater extrating the data it needed to be cleaned so I uploaded into Power Query and made the following changes:
- Removed "Duración" and "Temperatura" columms which had the same value in all rows and were not relevant for the analysis.
- Eliminated duplicates, registry errors and empty rows.
- Splited "Fecha Final" into two columms: "Fecha" and "Hora".
- Renamed columm "Serial" for "Determinadora" and change long serial values for D1, D2 and D3 according to the corresponding tester.
- December 2019 records were discarded to have a greater reliability of the data (during that period the IoT system was still testing).
- Set data types and format. 
- Made an auxiliary Date table using DAX.
![alt text]( "Data cleaning resume")
![alt text]( "Final dataset preview")

## Exploratory Data Analysis (EDA)

## Featured Analysis (Specific EDA)

## Conclusions and recomendations

## Communication

<!--- Collecting structuring, analyzing, and turning raw data into actionable business insights.
T- he main purpose og BI is to provide actionable business insights and support data-driven decision making.-->
