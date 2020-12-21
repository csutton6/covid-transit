---
layout: default
altair-loader:
  altair-chart-1: "charts/covid_lines_1.json"
  altair-chart-2: "charts/first_cluster_chart.json"
  altair-chart-3: "charts/ridership_byCluster.json"

hv-loader:
  hv-chart-1: ["charts/office_table.html", "400"] # second argument is the desired height
folium-loader:
  folium-chart-1: ["charts/foliumChart.html", "400"] # second argument is the desired height
  folium-chart-2: ["charts/percent_no_internet.html", "400"] # second argument is the desired height
---

<style>
  .figure-caption{
    font-size: 12px;
  }
</style>

# COVID Transit Ridership

<br>

## Introduction
The COVID-19 pandemic dealt a harsh blow to the public transit industry in the United States. Ridership numbers for some agencies have plummeted asfar as 90% below their pre-covid levels.

<div id="altair-chart-1"></div>
<div class='figure-caption'><strong>Figure 1.</strong> Monthly ridership at the 20 transit agencies with the highest January 2020 ridership, excluding New York's MTA. NY MTA is excluded because its ridership is 8 times larger than the next closest system, which distorts the scale of the graph. Source: National Transit Database. </div>
<br>

However, not all agencies have been effected equally. Some have suffered greater ridership losses than others while some have recovered to a greater extent or at different times. For example, Figure 1 shows that Chicago Transit Authority, which once carried 5 million monthly passengers more than LA Metro, has consistently ranked below LA Metro since April. In this project, I use clustering analysis to identify agencies that experienced similar ridership changes throughout the pandemic. 

This analysis offers two potential insights. Clustering can help us understand the differences between transit agencies. Agencies with lesser drops in ridership may draw more from essential workers or reside in regions that have sustained higher levels of travel activity during the pandemic. These differences may prove to be informative once transit agencies are forced to make long-term decisions in response to the pandemic.After experiencing such staggering ridership losses, some agencies may need to make service cuts. New York's MTA has warned it [could cut service](https://www.pix11.com/news/local-news/transit-officials-around-the-country-warn-of-service-cuts-and-layoffs) up to 40%. The idea behind my clustering analysis is that agencies with similar patterns of ridership changes form a group of peer agencies and may make similar service changes as they cope with these challenging circumstances. This could be useful to transit planners as they look for examples from peer agencies or to transit advocates seeking to organize for better service.

## Methods

I performed a K-means clustering algorithm on monthly ridership data as reported in the [National Transit Database](https://www.transit.dot.gov/ntd/ntd-data) from the Federal Transit Administration. I analyzed a relative measure, the percent loss in ridership, to facilitate comparisons across agencies regardless of service levels or ridership numbers. I used three such features: 
- percent change in April ridership
- percent change in July ridership
- percent change in October ridership

To account for seasonal ridership variation, each percent change was calculated compared to the same calendar month the previous year. April was chosen since it's the nadir of the data. October is the most recent month available in the NTD, and July falls at the halfway point. After clustering, I compare the resulting groups against additional attributes, such as the percent of the budget that comes from fares, to help draw conclusions about possible service changes. 

## Clustering
I grouped the data into five clusters, named as follows: 
- "Office Workers and Universities"
- "Struggling Legacy Systems"
- "Bus-Driven Recovery"
- "Small and Essential"
- "Small and Growing"

<div id="altair-chart-2"></div>
<div class='figure-caption'><strong>Figure 2.</strong> Clustering results using K-means clustering with 5 clusters. Features included percent ridership change between 2020 and 2019 in April, July, and October. Sized according to peak vehicles to give a sense of agency size.</div>

<div id='altair-chart-3'></div>

### Cluser 1: Office Workers and Universities

<div id="hv-chart-1"></div>
This cluster suffered the highest ridership losses in 2020. Almost all of the commuter rail agencies are in this cluster, including Metro North in New York and Metra in Chicago. Because the ridership of such services tends to draw from suburban office commuters, I named this cluster after office workers. It includes a number of university transit systems. Some city transit agencies, including WMATA and BART fall in this cluster as well. Since they experience similar ridership trends as commuter rail systems, one could conclude that they also draw heavily from office commuters who worked from home during the pandemic. 

### Struggling legacy systems

text here

### Bus-Driven Recovery

text here

### Small and Essential 

text here

### Small and Growing

text here

## Map of Clusters

## Clusters by Volume of Ridership

the big agencies are all below

## Clusters by Metro Area

look at new york metro area. see modal differences. commuter rail vs heavy rail vs bus vs not in other two categories

## Demand Response vs Fixed Transit

## Fare Reliance

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
