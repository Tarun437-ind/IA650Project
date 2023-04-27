# IA650 Final Project
# PREDICTION OF TEMPERATURE AROUND THE GLOBE
Every continent has the different average temperature based on region and thier location our main aim for this project is to predict the temperature of that region,city and year
# DATA COLLECTION
Every continent has the different average temperature based on region and thier location our main aim for this project is to predict the temperature of that region
The Dataset is extracted from the data world bank and referred from University of Dayton daily average temperatures for 157 U.S. and 167 international cities. The Data updated on a regular basis and contain data from January 1, 1995 to present.
Source data for this site are from the National Climatic Data Center. The data is available for research and non-commercial purposes only.
Reference : https://academic.udayton.edu/kissock/http/Weather/default.htm
# DATA DESCRIPTION AND DIRECTORY
-> The overall data contains 2.9 millons rows and 8 columns 
1) REGION : Continent name such as Africa,Asia
2) COUNTRY : Country Name across the globe 
3) STATE : Territory of that Country
4) CITY : City of that state in the country
5) MONTH : Month of that year ranges from 1 to 12
6) DAY : Day of that Month present ranges 
7) YEAR : Year of which the details were recorded
8) AVERAGE TEMPERATURE : Avgerage temperature recorded on that date by city and region

# IMPORTING ALL THE NECESSARY PYTHON LIBRARIES 
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.preprocessing import LabelEncoder
import xgboost as xgb
from sklearn.ensemble import GradientBoostingRegressor
from sklearn.metrics import mean_squared_error
from sklearn.metrics import r2_score

# READING CSV FILE AND GOING THROUGH THE DATA
df=pd.read_csv("city_temperature.csv")
df

OUTPUT :

![image](https://user-images.githubusercontent.com/93997961/234970304-776fd02f-b452-4228-a8f8-27b67ea92306.png)

-> Dropping the duplicate rows

df=df.drop_duplicates()

-> see how null value exist in each column
df.isna().sum()

OUTPUT:  

![image](https://user-images.githubusercontent.com/93997961/234971850-db3d9b20-5c3b-46d9-a2fa-24e02264baff.png)


df.describe()

OUTPUT : 

![image](https://user-images.githubusercontent.com/93997961/234972279-5cc2d420-931b-42f5-b8a0-33e9be2c1554.png)

# Removing the rows that contains 200 and 201 in the year and contains 0 in the day
df =df[ (df['Year'] != 200) & (df['Year'] != 201) & (df['Day'] != 0) ]

# Transform the Average Temperature from Fahrenheit to Celsius
df["AvgTemperature"]=(df["AvgTemperature"]-32)*(5/9)

# Add a datetime column to use it in plotting
df['Date'] = pd.to_datetime(df[['Year','Month','Day']])

#  Remove values that are less than -50 and year equal or greater than 2020 since there exists some random drops in it
df =df[(df['AvgTemperature'] >= -50) & (df['Year'] < 2020)]

# PLOTTING THE DATASET
# PLOTTING BY REGION


![image](https://user-images.githubusercontent.com/93997961/234974857-2328df5d-904b-40e4-93be-698a5c8f659b.png)

# The hottest Average Temperature in the Dataset
df.sort_values(by = ['AvgTemperature'], ascending  = False).head(1)


![image](https://user-images.githubusercontent.com/93997961/234975164-e814f627-501f-4a1b-a36e-0d1602bed2a2.png)

# The coldest Average Temperature in the Dataset
df.sort_values(by = ['AvgTemperature'], ascending  = True).head(1)

![image](https://user-images.githubusercontent.com/93997961/234975481-43ceaa66-d431-468d-8f3f-91a2ef7823ff.png)


# PLOTTING SOME CITIES

![image](https://user-images.githubusercontent.com/93997961/234975668-fcd8951f-6c21-4906-a1ec-cfa80d51ec64.png)

# plotting the temperature of every country in a region


![image](https://user-images.githubusercontent.com/93997961/234976740-7c61e3dd-4284-4d0b-b363-d90becd4a046.png)






