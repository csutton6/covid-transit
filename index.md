---
layout: default
altair-loader:
  altair-chart-1: "charts/covid_lines_1.json"
hv-loader:
  hv-chart-1: ["charts/measlesHvplot.html", "500"] # second argument is the desired height
folium-loader:
  folium-chart-1: ["charts/foliumChart.html", "400"] # second argument is the desired height
  folium-chart-2: ["charts/percent_no_internet.html", "400"] # second argument is the desired height
---

<style>
  .figure-caption{
    font-size: 10px;
  }
</style>

# COVID Transit Ridership

### The Problem
The COVID-19 pandemic has dealt a harsh blow to the public transit industry in the United States. Ridership numbers for some agencies have plummeted a far as 90% below their pre-covid levels.

<div id="altair-chart-1"></div>
<div class='figure-caption'>*2020 Ridership Chart*. Monthly ridership at the 20 transit agencies with the highest January 2020 ridership, excluding New York's MTA. NY MTA is excluded because its ridership is 8x larger than the next closest system, which would make for an uninteresting scale for most other agencies. Source: FTA National Transit Database. </div>

However, not all agencies have been affected equally. Some agencies have different temporal patterns, such as not plummeting until the second wave in July or making a stronger recovery in the fall. Other differences relate to the magnitude of ridership losses: some agencies have not seen ridership plummet quite as much as other. In this project, I use clustering analysis to identify agencies that experienced similar ridership changes throughout the pandemic. 

I see this as interesting in two ways. Firstly as an exploratory exercise to understand the ways in which different transit agencies have fared. This general understanding could help us predict what will happen in the future. After experiencing such staggering ridership losses, it remains unclear if transit agencies will be able to maintain the same level of service they operated before the pandemic. New York's MTA has warned it [could cut service](https://www.pix11.com/news/local-news/transit-officials-around-the-country-warn-of-service-cuts-and-layoffs) up to 40%. 


# Example: Embedding Altair & Hvplot Charts

This section will show examples of embedding interactive charts produced using [Altair](https://altair-viz.github.io) and [Hvplot](https://hvplot.pyviz.org/).

## Altair Example

Below is a chart of the incidence of measles since 1928 for the 50 US states.

<!-- <div id="altair-chart-1"></div> -->

This was produced using Altair and embedded in this static web page. Note that you can also display Python code on this page:

```python
import altair as alt
alt.renderers.enable('notebook')
```

## HvPlot Example

Lastly, the measles incidence produced using the HvPlot package:

<div id="hv-chart-1"></div>

## Notes

- See the [raw source code](https://raw.githubusercontent.com/MUSA-550-Fall-2020/github-pages-starter/master/_posts/2019-04-13-measles-charts.md) of this post for details on how these charts were embedded.
- See the [lecture 13A slides](https://github.com/MUSA-550-Fall-2020/week-13/blob/master/lecture-13A.ipynb) for the code that produced these plots.

**Important: When embedding charts, you will likely need to adjust the width/height of the charts before embedding them in the page so they fit nicely when embedded.**

# Example: Embedding Folium charts

This post will show examples of embedding interactive maps produced using [Folium](https://github.com/python-visualization/folium).

## OSMnx and Street Networks

The shortest route between the Art Museum and the Liberty Bell:

<div id="folium-chart-1"></div>

<br/>

## Percentage of Households without Internet

The percentage of households without internet by county:

<div id="folium-chart-2"></div>

See the [lecture 9B slides](https://musa-550-fall-2020.github.io/slides/lecture-9B.html) and the [lecture 10A slides](https://musa-550-fall-2020.github.io/slides/lecture-10A.html) for the code that produced these plots.
