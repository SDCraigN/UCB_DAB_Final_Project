#  Demystifying ML: US Climate Change
 
In this project we were tasked with finding a problem worth solving, analyzing, or visualizing. After some consideration we landed on the topic of global warming. In America, one's view of climate change often depends on where they live. The majority of U.S. adults say they are taking some specific action in their daily lives to protect the environment and that 62% say climate change is at least having some impact on their local community. Most Pacific states followed by the Northeast see climate change as affecting their local areas.  [PEW Research Center, 11/22/2019.]

We will be looking at average weather temperatures and CO2 emmisions to evalute whether or not climate change is an actual problem in America or not. 

![Global Warming](https://www.psychologicalscience.org/redesign/wp-content/uploads/2017/01/Earth-melting-above-ocean-e1485893153798-609x419.jpg)

## Project Type and Technology
Our project analyzed existing data to make a prediction on temperature change using multiple linear regression, by utilizing the following technology: 
* Database: Google BigQuery (SQL)
* Notebook: Google Colab 
* Data Cleaning: Pandas
* Machine Learning: PySpark ML
* Visualization: Tableau


## Data

**Original Datasets**

https://www.kaggle.com/noaa/gsod 
National Oceanic and Atmospheric Administration (NOAA)’s *Global Surface Summary of the Day (GSOD)* dataset that compiles daily weather data (mean temp, dew point, pressure) from now 9,000 weather stations across the world with data dating back to 1929. 

https://www.kaggle.com/ucsandiego/carbon-dioxide
This dataset includes a monthly observation of atmospheric carbon dioxide (or CO2) concentrations (ppm) from the Mauna Loa Observatory in Hawaii dating back to 1958. 

**Database**

Created a Google BigQuery cloud data warehouse and uploaded the two datasets. From there,  we used SQL Queries to combine the data into tables that could be translate read into our Machine Learning Algorithm and Visualizations. 

1) Combine the daily weather stations’ readings with the station location & name data and filter down by US stations. 
![Query 1](https://github.com/SDCraigN/UCB_DAB_Final_Project/blob/main/Images/BigQuery_1.png)

2) Compute stations’ yearly temperature averages (F)
![Query 2](https://github.com/SDCraigN/UCB_DAB_Final_Project/blob/main/Images/BigQuery_2.png)

3) Compute yearly average atmospheric carbon dioxide (ppm)
![Query 3](https://github.com/SDCraigN/UCB_DAB_Final_Project/blob/main/Images/BigQuery_3.png)

4) Combine the average temperature and carbon dioxide datasets
![Query 4](https://github.com/SDCraigN/UCB_DAB_Final_Project/blob/main/Images/BigQuery_4.png)

Output - converted the yearly averages into CSVs that were then exported and hosted on Google Storage so that they could be used in Tableau (Visualizations) and Pyspark (Machine Learning)

## Machine Learning: Training & Testing

**Method**

On a Google Colab notebook, we used PySpark as opposed to SciKit Learn and Pandas to conduct our multiple linear regression. We chose PySpark instead because Pandas kept crashing due to the large nature of our intended dataframe.

**Variables**

The independent variables were year (1975-2016), latitude, elevation (Meters), and average atmospheric carbon dioxide (PPM). The dependent variable was average temperature (Fahrenheit) recorded at each data point (which were weather stations). 

**Summary**

Train
* RMSE = 4.38
* R2 = 0.86

Test
* RMSE = 4.29
* R2 = 0.86

## Machine Learning: Predictions
After training and testing, we used the model to predict what the **average yearly temperature** would be **for each US state capital in 2025, 2040 and 2055.**

**Inputs**
* Years = 2025, 2040, 2055
* Latitude = each capital’s latitude
* Elevation = each capital’s elevation (or mean elevation if the city contained drastic elevation changes)
* CO2 = see below

For the purpose of this prediction, we calculated the average yearly CO2 for our input years by taking the growth rates for the 15, 25 and 40 years leading up to our last year of data, which was 2016, and applying that to 2015. 
* 2007-2016 = 5% Growth | 2025 = 424.49 CO2 (PPM)
* 1992-2016 = 13% Growth | 2040 = 456.83 CO2 (PPM)
* 1977-2016 = 21% Growth | 2055 = 489.18 CO2 (PPM)

## Observations

Our model appears to have predicted the future average temperatures of US capital cities pretty accurately; albeit forebodingly…
* Honolulu, 2019 Avg Temp = 78 (Actual) 
* Honolulu, 2025 Avg Temp =  79.03 (Predicted)

From 2025 onwards, our model predicts ~ .3 increase in temperature across all regions

Our data definitely shows that increasing CO2 levels are causing US & global temperatures to rise. These temperature rises will soon have an irreversible impact on the world we know today……unless we do something!


## Visualizations

https://public.tableau.com/profile/nick.nasse#!/vizhome/USCapitalsTempPredictions/USClimateChange


## A Slack-Errr production by 
Nick Nasse
Craig Nowakowski
Hayden Rubin

![Logo](https://is4-ssl.mzstatic.com/image/thumb/Purple114/v4/b3/3a/a1/b33aa167-5a3a-1a09-332e-61d750453e28/AppIcon-0-0-1x_U007emarketing-0-0-0-7-0-0-sRGB-0-0-0-GLES2_U002c0-512MB-85-220-0-0.png/1200x630wa.png)

