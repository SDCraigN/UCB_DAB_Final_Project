#  Demystifying ML: US Global Warming
 
In this project we were tasked with finding a problem worth solving, analyzing, or visualizing. After some consideration we landed on the topic of global warming. In America, one's view of climate change often depends on where they live. The majority of U.S. adults say they are taking some specific action in their daily lives to protect the environment and that 62% say climate change is at least having some impact on their local community. Most Pacific states followed by the Northeast see climate change as affecting their local areas.  [PEW Research Center, 11/22/2019.]

We will be looking at average weather temperatures and CO2 emmisions to evalute whether or not climate change is an actual problem in America or not. 

![Global Warming](https://www.psychologicalscience.org/redesign/wp-content/uploads/2017/01/Earth-melting-above-ocean-e1485893153798-609x419.jpg)

## Getting Started
Create a front-end interface that maps to an API to “smarten” the algorithm.
Perform a deep dive of existing data using machine learning.
Create a visualization that continues to learn where clusters lie based on ML.
(Use D3 or Plotly to change the visualization.)
Create an idea with mock data that simulates how machine learning might be used.
Create an analysis of existing data to make a prediction, classification, or regression. 
 
## Prerequisites

 Find a problem worth solving, analyzing, or visualizing.
 Use ML in the context of technologies learned.
 You must use: Scikit-Learn and/or another machine learning library.
 You must use at least two of the below:
 
Python Pandas 
HTML/CSS/Bootstrap 
Python Matplotlib 
JavaScript Plotly
JavaScript D3.js
JavaScript Leaflet 
SQL Database 
MongoDB Database
Google Cloud SQL 
Amazon AWS 
Tableau

## Data

**Original Datasets**

https://www.kaggle.com/noaa/gsod 
National Oceanic and Atmospheric Administration (NOAA)’s *Global Surface Summary of the Day (GSOD)* dataset that compiles daily weather data (mean temp, dew point, pressure) from now 9,000 weather stations across the world with data dating back to 1929. 

https://www.kaggle.com/ucsandiego/carbon-dioxide
This dataset includes a monthly observation of atmospheric carbon dioxide (or CO2) concentrations (ppm) from the Mauna Loa Observatory in Hawaii dating back to 1958. 

**Database**

Created a Google BigQuery cloud data warehouse and uploaded the two datasets. From there,  we used SQL Queries to combine the data into tables that could be translate read into our Machine Learning Algorithm and Visualizations. 

1) Combine the daily weather stations’ readings (temp, dew, etc) with the station characteristic data (name, latitude, longitude) and filter down by US stations. 
![Query 1](https://github.com/SDCraigN/UCB_DAB_Final_Project/blob/main/Images/BigQuery_1.png)

2) Compute Stations’ Monthly Weather Averages
![Query 2](https://github.com/SDCraigN/UCB_DAB_Final_Project/blob/main/Images/BigQuery_2.png)

3) Combine Monthly Station Weather Data with the Monthly CO2 Data from the Mauna Loa dataset
![Query 3](https://github.com/SDCraigN/UCB_DAB_Final_Project/blob/main/Images/BigQuery_3.png)

4) Compute Yearly Averages for the combine Weather and CO2 datasets
![Query 4](https://github.com/SDCraigN/UCB_DAB_Final_Project/blob/main/Images/BigQuery_4.png)

Output - converted the yearly averages into CSVs that were then exported and hosted on Google Storage so that they could be used in Tableau (Visualizations) and Pyspark (Machine Learning)


## A Slack-Errr production by 
Nick Nasse
Craig Nowakowski
Hayden Rubin

![Logo](https://is4-ssl.mzstatic.com/image/thumb/Purple114/v4/b3/3a/a1/b33aa167-5a3a-1a09-332e-61d750453e28/AppIcon-0-0-1x_U007emarketing-0-0-0-7-0-0-sRGB-0-0-0-GLES2_U002c0-512MB-85-220-0-0.png/1200x630wa.png)

