# Project: Pasta Moisture Data Analysis
*Exploratory data analysis on pasta moisture (food industry) for manufacturing efficiency improvement.*

## Overview
- In this research work, a deep analysis on the moisture data of pasta in a food factory was carried out, in order to answer questions and help make decisions to improve the efficiency of the pasta drying process.
- Data obtained from moisture testers through an IOT data capture system and stored on a csv file. 1 final dataset with 14.121 rows.
- Project tools: Power BI for ETL and graphics, Infostat for statistics, Excel. <!--- Important insights:-->
- Built a formal report.

<!--### Code and Resourses Used-->
## Problem statement and hypothesis
The challenge of the pasta drying process is to be able to obtain the highest possible moisture results in the finished product without entailing a risk of non-conforming product by exceeding the maximum legal level of 13.00%. The objective of the production team, and the business in general, is to reach the range of 12.30% - 12.50%.

This data analytical approach was made to answer specific questions and check some hypotheses about the actual pasta drying process, and help detect pain-points where opportunities can be capitalized. Some of the most importants are:
- Which production line/pasta format has the most variant moisture results? Which pasta format tends to be dryer?
- Does the weight of the pasta samples have any significant impact on the results of the moisture testers?**
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

![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Data_cleaning_summary.png "Data cleaning summary")
![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Final_dataset_preview.png "Final dataset preview")

## Exploratory Data Analysis (EDA)
After ETL process The data was analyzed in a structured way to answer the questions posed. A segmentation was carried out by Production line and by Zone, which allows to have a better idea of the pasta moisture obtained in each stage of the process, especially in the final stage because is the one that interests the most.

Below are a few highlights from the analysis.

<!---
- 1. Linea con humedad promedio mas alta/baja: tabla resumen de medidas de tendencia central.
- 2. La linea mas/menos variable: juntar histogramas de cada una de las líneas.
- 3. Top 3 de las referencias mas altas/bajas: Resultado de las referncias mas secas por línea.
- 4. Scatterplots de los pesos de las muestas
- 5. Line B Enfriador vs Corte Scatterplot
- 6. Line B boxplot and hypothesis test
- 7. Line C boxplot and hypothesis test

![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Measures%20summary.PNG "Final stage zone measures summry for each Line")
![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Stripplot_by_Line_(Final_zone_data%20distribution).PNG "Final zone moisture distribution")

Looking at the measures (summary table) and  distribution (strip plot) of the pasta moisture for each production line we can easily figure out some issues: average pasta moisture, process dispersion, outliers, and general behavipur for each line.

<!---1. la Línea con mayor promedio de humedades de salida y menor variación es la Línea B (12,03%), D.E. = 0,32 y C.V. = 2,68%. La Línea A posee el menor promedio de humedades de salida (11,60%).

<!---2. Atendiendo las medidas de dispersión de Línea D(SD=0,50 y CV=4,37%), y la distribución de humedades de salida en el histograma, estas encuentran dispersas sobre un rango más amplio que en cualquiera de las otras líneas. Por lo tanto es la línea con mayor variabilidad en el proceso de secado.

![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Top_5_References.PNG)
![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Bottom_5_References.PNG)
<!---3. Tablas de referencias top 5 de las mas humedas y secas:Se decide analizar individualmente solo aquellas referencias que poseen más de 50 datos como tamaño muestral. No es apropiado realizar una comparación de las humedades entre todas las referencias, ya que los estadísticos obtenidos de muestras muy pequeñas no representan una aproximación adecuada de la realidad. Distinguidamente se nota que las de línea B y C son las mas húmedas, las de Línea A y D son las mas secas.

## Featured Analysis (Specific EDA)..
![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Scatterplot_SampleWeight_vs_Moisture_Line_B.PNG)
![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Scatterplot_SampleWeight_vs_Moisture_Other_Lines.PNG)
<!---4. Scatterplots de los pesos de las muestas: Al comparar los pesos de las muestras (eje x) con los resultados de humedad (eje x) en gráfico de dispersión (scatterplot), vemos que se dibuja un patrón común en todas las líneas de producción. éste podría ser el patrón que muestra el efecto que tiene el peso de las muestras sobre la precisión en los resultados de las determinadoras de humedad Este patrón cónico indica que a medida que los pesos de las muestran aumentan, los resultados de humedad se van acercando a un valor central.

![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Enfriador_vs_Corte_Moisture_Scatter_chart.PNG)
<!---5. Line B Enfriador vs Corte Scatterplot.

## Conclusions and recomendations

## Communication

<!--- Collecting structuring, analyzing, and turning raw data into actionable business insights.
T- he main purpose og BI is to provide actionable business insights and support data-driven decision making.-->
