# Project: Pasta Moisture Data Analysis
*Exploratory data analysis on pasta moisture (food production industry) for manufacturing efficiency improvement.*

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
- How much moisture does the pasta lose from the end of the cooling phase to the stripper (cutting stage)?
- Will it be necessary to modify the drying recipes individually for each drying cell instead of having a single modified recipe for all?

## Data Collection
The main database is composed by the moisture test results of the pasta from all production lines. The pasta moisture is measured at different stages of the drying process using moisture testers, and the obtained data is transferred via an IoT divice to a csv file on the cloud. Raw data preview table:

![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Raw_data_preview.png "Raw data preview")

<!--Fecha Final: Date and Time, Linea: production line, Referencia: pasta format, Zona: drying zone where the pasta sample is taken, Resultado: moisture test result, Duración: moisture test time duration, Peso Muestra: sample initial weight, Peso Final: sample final weight, Temperatura: moisture test temperature (°C), Serial: tester ID serial-->

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
After ETL process The data was analyzed in a structured way to answer the questions posed. A segmentation was carried out by Production line and by Zone, which allows to have a better idea of the pasta moisture obtained in each phase of the process, especially in the final phase because is the one that interests the most. Below are a few highlights from the analysis.

![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Measures%20summary.PNG "Final stage zone measures summry for each Line")
![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Histograms_All_Lines.PNG "Final moisture distribution by line")
Considering the graphics above (summary measures table and histograms) we can easily figure out the distribution, general behaviour and the process dispersion for each line. Line B has the highest pasta moisture average (12.03%) and the least variation in moisture (S.D. = 0.32, C.V. = 2.68%). Line A has the lowest average pasta moisture (11.60%). For Line D, standard deviation is the highest (0,50) as well as CV (4,37%). Line D moisture data is scattered over a wider range than any of the other lines, therefore, it is the line with the greatest variability in the drying process.

Top and bottom 5 References by Moiture AVG:

![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Top_5_References.PNG "Top 5 References by Moiture AVG")-----
![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Bottom_5_References.PNG "Bottom 5 References by Moiture AVG")
<!---Se decide analizar individualmente solo aquellas referencias que poseen más de 50 datos como tamaño muestral. No es apropiado realizar una comparación de las humedades entre todas las referencias, ya que los estadísticos obtenidos de muestras muy pequeñas no representan una aproximación adecuada de la realidad. Distinguidamente se nota que las de línea B y C son las mas húmedas, las de Línea A y D son las mas secas.-->

Sample Weight vs Moisture Results:

![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Scatterplot_SampleWeight_vs_Moisture_Line_B_and_Others.PNG)

When comparing the weights of the samples (x-axis) with the moisture results (x-axis) on a scatterplot, a common pattern is drawn in all the production lines. This pattern shows the effect that the weight of the samples has on the precision of the moisture testers: as the sample weights increase, the moisture results are approaching a core value.

## Specific Analysis
### Line B-BPL (long-cut pasta line)
Cooler Moisture vs Stripper Moisture:
The cooler is the last drying phase, it allows to lower the temperature of pasta and make it suitable for storage in the buffer silo.
The stripper automatically removes the sticks and cuts the pasta to the length required for the next phase of packaging.

![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Average_Difference_Enfriador_vs_Corte_(LineB).PNG)

To know how much moisture does the pasta lose from the Cooler (Enfriador) to the Stripper (Corte), we study the difference between the average pasta moisture per day in these two stages. On average, pasta loses 0.41% of moisture in the time it takes to go from one stage to the other.

![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Enfriador_vs_Corte_Moisture_Scatter_chart.PNG)

The scatterplot shows an increasing pattern in the Cuttting zone moistures as the Cooler moistures increase, however, the relationship is not very strong since the points do not have a very sharp alignment. The correlation coefficient R, takes the value of 0.67, which confirms that there is a positive moderate linear correlation. On the other hand, the coefficient of determination R2 is 0.45 and it is telling us that only 45% of the variability of the moisture in the Cutting zone is explained by the moisture of the Cooler zone. The moisture in the Cooler zone is not the only factor determining the moisture in the Cutting zone, there are other factors that affect to a great extent such as the pasta resting time in the buffer storage silo.


Moisture by Cut Zone boxplot:

![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Boxplot_%25Moisture_by_Cut_Zone_LineB.PNG)

### Line C-STR (Special pasta line)
Moisture by DryingCell - Hypothesis test

![alt text](https://github.com/caestradaa/pasta_moisture_daproj/blob/main/Images/Boxplot_Moisture_by_DryingCell_LineC_and_Hypothesis_Test.PNG)

## Dashboard preview
## Conclusions and recomendations

<!--- Collecting structuring, analyzing, and turning raw data into actionable business insights.
T- he main purpose og BI is to provide actionable business insights and support data-driven decision making.-->
