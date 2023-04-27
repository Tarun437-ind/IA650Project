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
OUTPUT : ![image](https://user-images.githubusercontent.com/93997961/234970304-776fd02f-b452-4228-a8f8-27b67ea92306.png)
