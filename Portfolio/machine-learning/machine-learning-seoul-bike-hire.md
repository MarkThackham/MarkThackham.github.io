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

This way, midnight (0) and 11 PM (23) are close together, preserving the natural cycle.
In short: cyclical encoding lets machine learning models “see” the circular structure of time-like features.

</p>
<ul>
  <li>xx</li>
</ul>

</div>

## Data
The [Seoul Bike Sharing Demand Dataset](https://archive.ics.uci.edu/dataset/560/seoul+bike+sharing+demand) contains hourly counts of bike rentals in Seoul across a full year, along with weather data (temperature, humidity, wind speed, visibility, dew point, solar radiation, rainfall, snowfall), temporal features (hour, date, season), and holiday / functional day indicators. Features can be used to predict the number of bikes rented in a given hour, based on both environmental and calendar features. The dataset contains 8,760 examples and 13 features (units in brackets):

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

#### Response
The response is the number of bikes rented in a given hour. The histogram below shows the distribution of bike rentals, with an overlaid density estimate. The distribution of bike rentals is right-skewed, with most hours having low to moderate rentals, and a few hours with very high rentals.

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
- **DayOfWeek** → rentals are fairly steady across weekdays, with Fri/Sat slightly higher.  
- **Hour** → strong commuting pattern, peaking at 7–9 AM and 5–7 PM.  
- **Month** → lowest in winter, highest from late spring through early autumn.  
- **Seasons** → summer has the most rentals, winter the least.  
- **Holiday** → rentals drop on holidays compared to normal days.  

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
- **Temperature** → rentals increase steadily with warmer temperatures, peaking in the 20–30°C range.  
- **Humidity** → moderate humidity supports higher rentals, but very high humidity reduces usage.  
- **Wind speed** → higher wind speeds are linked to fewer rentals.  
- **Visibility** → better visibility is associated with slightly more rentals.  
- **Dew point temperature** → higher dew points (warmer, humid air) generally align with more rentals.  
- **Solar Radiation** → more sunlight corresponds to increased bike rentals.  
- **Rainfall Indicator** → bike rentals drop sharply when it rains.  
- **Snowfall Indicator** → rentals are much lower on snowy days.  

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-features-weather.png"
         alt="Bike Rentals by Weather Conditions"
         width="800">
    <figcaption>Bike Rentals by Weather Conditions</figcaption>
  </figure>
</div>

## Modelling

### Preparation
Machine learning models need categorical features numerically encoded.  Cyclical encoding accounts for features that repeat in cycles (like hour of day). For example, Hour 0 and Hour 23 are close in time, which cyclic encoding reflects. Cyclical encoding maps a periodic feature \( v \ = the value (e.g., 0–23 for hours)) with period \( N \ = the total number of categories (e.g., 24 for hours) ) onto a circle:

$$
x_{\sin} = \sin\left(\frac{2\pi v}{N}\right)
$$

$$
x_{\cos} = \cos\left(\frac{2\pi v}{N}\right)
$$

The below plots show the cyclical encoding for DayOfWeek, Hour and Month.

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">

  <figure style="flex: 1; text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-features-cyclic-days.png"
         alt="Cyclical Days" style="max-width: 100%; height: auto;">
    <figcaption>Cyclical Encoding - Days</figcaption>
  </figure>

  <figure style="flex: 1; text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-features-cyclic-hours.png"
         alt="Cyclical Hours" style="max-width: 100%; height: auto;">
    <figcaption>Cyclical Encoding - Hours</figcaption>
  </figure>

  <figure style="flex: 1; text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-features-cyclic-months.png"
         alt="Cyclical Months" style="max-width: 100%; height: auto;">
    <figcaption>Cyclical Encoding - Months</figcaption>
  </figure>

</div>

The Seasons (Spring, Summer, Autumn, Winter) and Holiday (Yes, No) categorical features are one-hot encoded into binary features.

### Modelling

### Results

## Codebase
The codebase to implement this analysis is [here](https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/seoul-bike-hire/machine-learning-seoul-bike-hire.ipynb)

[← Back to Machine Learning](/machine-learning/)

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
