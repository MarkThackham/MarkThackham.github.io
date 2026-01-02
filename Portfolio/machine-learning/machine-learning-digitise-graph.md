---
title: "Machine Learning"
permalink: /machine-learning/machine-learning-digitise-graph/
---

# Graph Digitisation with Machine Learning

## Take Away

<div style="background-color: #f5f5f5; padding: 15px; border-radius: 8px;">

<p>
Computer Vision techniques applied to the 
<a href="https://www.spglobal.com/ratings/en/regulatory/article/default-transition-and-recovery-us-corporate-defaults-fall-to-the-lowest-level-since-february-s101661849" target="_blank">Standard and Poor's (S&P) Default Study
</a> to extract data points from a graph. Key take-outs are:
</p>
<ul>
  <li>A cropped image of the graph is used as input</li>
  <li>Image processing isolates the coloured graph lines (using HSV thresholds) and the gray-ish grid/baseline lines (using RGB thresholds)</li>
  <li>Mask-based tracing (column-wise sampling) extracts a y-value for each x-position along each line</li>
  <li>Pixel coordinates are mapped back to the original chart axes (y from detected gridlines; x assumed uniformly spaced in time)</li>
  <li>The extracted series are saved to a CSV file for further analysis</li>
</ul>

This approach works well because it leverages two strong cues that charts usually contain: (1) gridlines/baselines that define the coordinate system, and (2) saturated coloured strokes that stand out from neutral grays. By isolating those cues separately, you can calibrate the axes and trace the series without needing heavy computer vision machinery.

</div>

## Data
The [S&P Default Study](https://www.spglobal.com/ratings/en/regulatory/article/default-transition-and-recovery-us-corporate-defaults-fall-to-the-lowest-level-since-february-s101661849) analyses historical default rates for speculative grade corporate borrowers, stratified by: GLobal; United States; Europe; and Emerging Markets 

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/digitise-graph/Input/digitise-graph.png"
         alt="S&P Default Study Graph"
         width="800">
    <figcaption>S&P Default Study Graph</figcaption>
  </figure>
</div>

## Analysis
The approach to digitising the graph involves several steps:

### 1) Start with a clean input: crop to the plot area
The PNG is cropped to the chart region. Cropping removes titles, margins, and legends so the later detection steps focus only on pixels that could plausibly be part of the plot.

### 2) Separate “structure” (grid/baseline) from “signal” (data lines)
Gridlines and axes are mostly gray, so these are detected using simple RGB (Red, Green, Blue) rules (R≈G≈B plus a brightness range). It scans rows to find horizontal gridlines, clusters adjacent rows (gridline thickness), and uses their midpoints as the gridline y-positions. It also detects the baseline near the bottom and uses it to estimate the plot’s x-range. From this it builds a **plot mask** so analysis only happens inside the plot area.

### 3) Isolate each coloured series using HSV thresholds
The coloured lines are segmented in HSV (Hue, Saturation, Value) space, where hue cleanly separates colours. This converts the image to HSV, then creates one boolean mask per series using tuned hue bands plus minimum saturation/value thresholds to reject gray gridlines and background noise.

### 4) Turn pixels into data: column-wise sampling (mask-based tracing)
For each x pixel column across the plot, the approach finds pixels that are both (a) inside the plot mask and (b) inside a series’ colour mask. If it finds any, it takes the **median y** to represent the line’s position at that x. Missing columns become NaN and are later filled by interpolation.

### 5) Calibrate to the chart axes (pixels → real values)
Using the detected horizontal gridlines (assumed to correspond to values 7..0), a linear mapping is fit from **y pixel → chart value**. For x, it assumes the chart is uniformly spaced in time and samples the trace onto a monthly date index from Jan 2017 to Nov 2025.

### 6) Export and validate by re-plotting
The extracted monthly series are assembled into a DataFrame and saved to a single CSV. The result is re-plotted  as a visual check that the digitised curves match the original chart.

## Results
These are the results of the digitisation process, showing the extracted series plotted against time.  

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/digitise-graph/digitised-chart-output.png"
         alt="S&P Default Study Graph"
         width="800">
    <figcaption>S&P Default Study Graph</figcaption>
  </figure>
</div>

## Codebase
The codebase to implement this analysis is [here](https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/digitise-graph/digitise-graph.ipynb)

[← Back to Machine Learning](/machine-learning/)