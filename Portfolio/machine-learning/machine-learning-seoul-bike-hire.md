---
title: "Machine Learning"
permalink: /machine-learning/machine-learning-seoul-bike-hire/
---

# Seoul Bike Hire2

## Take Away

<div style="background-color: #f5f5f5; padding: 15px; border-radius: 8px;">

<p>
Dataset 
<a href="https://archive.ics.uci.edu/dataset/560/seoul+bike+sharing+demand" target="_blank">
Seoul Bike Sharing Demand
</a> qqqq
</p>
<ul>
  <li>xx</li>
</ul>

</div>

## Data
The [Seoul Bike Sharing Demand Dataset](https://archive.ics.uci.edu/dataset/560/seoul+bike+sharing+demand) contains hourly counts of bike rentals in Seoul across a full year, along with weather data (temperature, humidity, wind speed, visibility, dew point, solar radiation, rainfall, snowfall), temporal features (hour, date, season), and holiday / functional day indicators. It can be used to predict the number of bikes rented in a given hour, based on both environmental and calendar variables. The dataset contains 8,760 examples and 13 features (units in brackets):

1. **Date** (Date)
2. **Rented Bike** (Integer)
3. **Hour** (Integer)
4. **Temperature** (C)
5. **Humidity** (%)
6. **Wind speed** (m/s)
7. **Visibility** (10m)
8. **Dew point temperature** (C)
9. **Solar Radiation**	(Mj/m2)
10. **Rainfall** (mm)
11. **Snowfall** (cm)
12. **Seasons**	(Categorical)
13. **Holiday**	(Binary)
14. **Functioning Day**	(Binary)

## Analysis

### Exploratory Data Analysis

#### Response Variable
The response variable is the number of bikes rented in a given hour. The plot below shows the hourly rental counts across the entire year, with clear daily and seasonal patterns. 

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-count-histogram.png"
         alt="Bike Rentals Histogram"
         width="800">
    <figcaption>Bike Rentals Histogram</figcaption>
  </figure>
</div>


There are peaks in the morning and evening corresponding to commuting times, as well as higher overall rentals in warmer months.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-count-hour.png"
         alt="Bike Rentals by Hour of Day"
         width="800">
    <figcaption>Bike Rentals by Hour of Day</figcaption>
  </figure>
</div>

Looking at a single month (September) shows the daily rental patterns more clearly, with consistent morning and evening peaks.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-count-hour-september.png"
         alt="Bike Rentals by Hour of Day - September 2018"
         width="800">
    <figcaption>Bike Rentals by Hour of Day - September 2018</figcaption>
  </figure>
</div>

There are 295 hours where the bike rental service was not functioning, which are removed from subsequent analysis.

#### Features - Time

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-features-time.png"
         alt="Bike Rentals by Hour of Day - September 2018"
         width="800">
    <figcaption>Distribution of Bike Rentals by Time</figcaption>
  </figure>
</div>
The boxplots above show the distribution of bike rentals by various time features.  

#### Features - Weather


### Results


## Codebase
The codebase to implement this analysis is [here](https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/seoul-bike-hire/Seoul-bike-hire.ipynb)

[← Back to Machine Learning](/machine-learning/)