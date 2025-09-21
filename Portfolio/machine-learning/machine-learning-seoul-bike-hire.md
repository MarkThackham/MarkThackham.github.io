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
The [Seoul Bike Sharing Demand Dataset](https://archive.ics.uci.edu/dataset/560/seoul+bike+sharing+demand) contains hourly counts of bike rentals in Seoul across a full year, along with weather data (temperature, humidity, wind speed, visibility, dew point, solar radiation, rainfall, snowfall), temporal features (hour, date, season), and holiday / functional day indicators. Features can be used to predict the number of bikes rented in a given hour, based on both environmental and calendar variables. The dataset contains 8,760 examples and 13 features (units in brackets):

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
The response variable is the number of bikes rented in a given hour. The histogram below shows the distribution of bike rentals, with an overlaid density estimate. The distribution of bike rentals is right-skewed, with most hours having low to moderate rentals, and a few hours with very high rentals.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-count-histogram.png"
         alt="Bike Rentals Histogram"
         width="800">
    <figcaption>Bike Rentals Histogram, with Overlaid Density Estimate</figcaption>
  </figure>
</div>

The plot below shows the hourly rental counts across the entire year, with clear seasonal. There are in warmer months, especially summer, when rentals peak. January to March have the lowest rentals.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-count-hour.png"
         alt="Bike Rentals by Hour of Day"
         width="800">
    <figcaption>Bike Rentals by Hour of Day</figcaption>
  </figure>
</div>

The plot below looks at a single month (September) shows the daily rental patterns more clearly, with consistent repetitive peaks.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-count-hour-september.png"
         alt="Bike Rentals by Hour of Day - September 2018"
         width="800">
    <figcaption>Bike Rentals by Hour of Day - September 2018</figcaption>
  </figure>
</div>

Finally, the plot below looks at the first 7 days of September 2018.  Saturday and Sunday have a single peak while weekdays have two peaks, one in the morning and one in the evening, likely corresponding to commuting patterns.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-count-hour-september-1st-7th.png"
         alt="Bike Rentals by Hour of Day - September 2018"
         width="800">
    <figcaption>Bike Rentals by Hour of Day - September 2018</figcaption>
  </figure>
</div>

There are 295 hours where the bike rental service was not functioning, which are removed from subsequent analysis.

#### Features - Time

The plots below show the relation between time and bike rentals.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-features-time.png"
         alt="Distribution of Bike Rentals by Time"
         width="800">
    <figcaption>Distribution of Bike Rentals by Time</figcaption>
  </figure>
</div>

#### Features - Weather

The plots below show the relation between weather conditions and bike rentals.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-features-weather.png"
         alt="Bike Rentals by Weather Conditions"
         width="800">
    <figcaption>Bike Rentals by Weather Conditions</figcaption>
  </figure>
</div>

### Results


## Codebase
The codebase to implement this analysis is [here](https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/seoul-bike-hire/machine-learning-seoul-bike-hire.ipynb)

[← Back to Machine Learning](/machine-learning/)