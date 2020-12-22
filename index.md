---
layout: default
altair-loader:
  altair-chart-1: "charts/covid_lines_1.json"
  altair-chart-2: "charts/first_cluster_chart_wider.json"
  altair-chart-3: "charts/ridership_byCluster.json"
  altair-chart-4: "charts/fare_chart.json"


hv-loader:
  hv-chart-1: ["charts/office_table_2.html", "400"] # second argument is the desired height
  hv-chart-2: ["charts/cluster_table_2.html", "350"]
  hv-chart-3: ['charts/legacy_table.html', "400"]
  hv-chart-4: ['charts/bus_driven_table.html', "400"]
  hv-chart-5: ['charts/small_essential_table.html', '400']
  hv-chart-6: ['charts/small_growing_table_2.html', '400']
  hv-chart-7: ['charts/cluster_byRidership.html', '400']
  hv-chart-8: ['charts/cluster_byMetro.html', '400']



folium-loader:
  folium-chart-3: ['charts/map_clustering.html', '400']
---

<style>
  .figure-caption{
    font-size: 12px;
  }
  #altair-chart-1{
    width: 500px;
  }
  #altair-chart-2{
    width: 500px;
  }
  #hv-chart-2{
    width: 600px;
  }
  #hv-chart-1{
    width: 600px;
  }
  #hv-chart-3{
    width: 600px;
  }
  #hv-chart-4{
    width: 600px;
  }
  #altair-chart-3{
    width: 100px;
  }
  #folium-chart-3{
    width: 600px;
  }
  #hv-chart-7{
    width: 400px;
  }
  #hv-chart-8{
    width: 400px;
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

| Cluster ID | Name |
|------------|------|
|1|Office Workers and Universities|
|2|Struggling Legacy Systems|
|3|Bus-Driven Recovery|
|4|Small and Essential|
|5|Small and Growing|

<br>
<div id="altair-chart-2"></div>
<div class='figure-caption'><strong>Figure 2.</strong> Clustering results using K-means clustering with 5 clusters. Features included percent ridership change between 2020 and 2019 in April, July, and October. Sized according to peak vehicles to give a sense of agency size.</div>

<br>

We see that most agencies experienced ridership losses during the pandemic, with the majority having lost more than 40% in April. Many agencies also recovered slightly by October, and a few small operators experienced growth in 2020.

<div id='hv-chart-2'></div>

Comparing percent ridership losses, *Office Workers and Universities* suffered the most, losing 94% of ridership in April and only recovering to an 86% loss by October. As Cluster ID increases, the percent loss in ridership becomes less severe during all 3 months under comparison. 


<div id='altair-chart-3'></div>
<div class='figure-caption'><strong>Figure 3.</strong> Ridership by cluster in selected months of 2019 and 2020. Each column represents the mean of the ridership at every ageny in the cluster for that month.</div>
<br>

The two highest performing clusters, *Small and Essential* and *Small and Growing*, are comprised of agencies with much smaller passenger levels, both before and after the pandmic. The *Struggling Legacy Systems* category carried the most riders, followed by *Bus-Driven Recovery* and *Office Workers and Universities*.


### Cluser 1: Office Workers and Universities

<div id="hv-chart-1"></div>

<div class='figure-caption'><strong>Figure 4.</strong> All agencies in Cluster <i>Office Workers and Universities</i>. Default sorting is according to volume of October 2020 ridership. Table is scrollable.</div>
<br>

This cluster suffered the highest percent ridership losses in 2020. Almost all of the commuter rail agencies are in this cluster, including Metro North in New York and Metra in Chicago. Because the ridership of such services tends to draw from suburban office commuters, I named this cluster after office workers. It includes a number of university transit systems. Some city transit agencies, including WMATA and BART fall in this cluster as well. Since they experience similar ridership trends as commuter rail systems, one could conclude that they also draw heavily from office commuters who worked from home during the pandemic. 

### Struggling Legacy Systems
<div id="hv-chart-3"></div>

<div class='figure-caption'><strong>Figure 5.</strong> All agencies in Cluster <i>Struggling Legacy Systems</i>. Default sorting is according to volume of October 2020 ridership. Table is scrollable.</div>
<br>

This category includes many of the transit agencies with the highest ridership in the U.S., such as New York's MTA, Chicago's CTA, and Boston's MBTA. This category contains the bulk of the legacy systems, i.e. the heavy rail systems that were built in the U.S. before the 1960s, though there are many agencies without heavy rail as well. The fact that these systems performed better than *Office Workers and Universities* suggests that they draw from a more diverse ridership pool and have more riders who continued to need or want transit during the pandemic. However, they still suffered great losses. Since many of these cities are areas with dense urban cores, passengers may have more easily been able to substitute walking or biking for their former transit trips. 

### Bus-Driven Recovery
<div id='hv-chart-4'></div>
<div class='figure-caption'><strong>Figure 6.</strong> All agencies in Cluster <i>Bus-Driven Recovery</i>. Default sorting is according to volume of October 2020 ridership. Table is scrollable.</div>
<br>

This cluster is similar to the previous in that it carries the second-highest average passenger levels, but it is predominated by bus transit systems. Though the agency does have rail, ridership at LA Metro [predominantly draws from its bus lines](http://isotp.metro.net/MetroRidership/Index.aspx). MTA Bus company is also an exclusively bus operator. The systems in this cluster likely draw from essential workers to an even greater extent than the *Struggling Legacy Systems*. A [study in 2018](https://www.its.ucla.edu/2018/01/31/new-report-its-scholars-on-the-cause-of-californias-falling-transit-ridership/) identified that the core of LA Metro's ridership is formed by low-income and immigrant riders without vehicles. The [LA Metro Customer Survey](https://media.metro.net/projects_studies/research/images/infographics/fall_2019__onboard_survey_results_and_trend_report.pdf) also indicates that bus riders have a lower median income than rail riders ($17,975 vs $27,723). If these same trends hold across other cities, we might expect that bus ridership would remain stronger at a time when low-wage hourly workers are more likely to work in-person or rely on public transportation for their trips. MARTA stands out as the largest second-generation transit system in this cluster, suggesting its ridership draws more from essential workers than BART or WMATA. 


### Small and Essential 
<div id='hv-chart-5'></div>
<div class='figure-caption'><strong>Figure 7.</strong> All agencies in Cluster <i>Small and Essential</i>. Default sorting is according to volume of October 2020 ridership. Table is scrollable.</div>
<br>

The agencies in this cluster form the bulk of the remaining agencies in this study. They have much lower mean ridership than the three previous clusters and come from smaller cities or metropolitan regions. They have on average experienced the strongest recoveries in October with some, such as the City of Asheville, experiencing growth in October. Perhaps these are the agencies with an even higher percentage of their riders drawing from essential workers, or perhaps these cities and regions saw a lesser reduction in activity levels during the pandemic. 

### Small and Growing
<div id='hv-chart-6'></div>
<div class='figure-caption'><strong>Figure 8.</strong> All agencies in Cluster <i>Small and Growing</i>. Default sorting is according to volume of October 2020 ridership.</div>
<br>


The last cluster is very small, comprising only 6 agencies, almost all of which experienced growth during one of the three months studied. Some of these systems, such as in Memphis, were launched as recently as 2019, so they had a small starting point from which to grow. The [California Vanpool Authority](https://calvans.org/history), which provides 15-passenger vans for commuters traveling to nearby destinations, has grown since its inception in 2002. 

## Map of Clusters

**U.S. Transit Clusters Map**
<div id="folium-chart-3"></div>
<div class='figure-caption'><strong>Figure 9.</strong> Map of transit agencies by cluster. Colored according to cluster (1=teal, 2=orange, 3=purple, 4=magenta, 5=green).</div>
<br>


## Clusters by Volume of Ridership
<div id='hv-chart-7'></div>
<div class='figure-caption'><strong>Figure 10.</strong> Chart of clusters grouped by ridership category. Ridership category calculated based on October 2020 ridership.</div>
<br>

We see that all large agencies fall into the bottom three clusters, suggesting that none of the transit operators that carry the most passengers will emerge from the pandemic unscathed. 

## Clusters by Metro Area
<div id='hv-chart-8'></div>
<div class='figure-caption'><strong>Figure 11.</strong> Chart of clusters grouped by metro area. </div>
<br>

To find a transit agency in your city, filter by metro area. 


## Fare Reliance
<div id='altair-chart-4'></div>
<div class='figure-caption'><strong>Figure 12.</strong> Fare reliance by October percent change in ridership. Fare reliance calculated as the percent of the operating budget that comes from fare revenue.</div>
<br>

To make true estimates about whether the transit agencies in a cluster will be similarly impacted by their ridership losses, it's important to know to what extent the agency relies on fare revenue. If an agency's operating budget is more reliant on fares, we might expect that agency to be more likely to implement service cuts in the event of large-scale ridership losses. Other sources of revenue, such as sales tax, may also be at risk during the pandemic. Exploring fare reliance in an operating budget therefore provides a starting point to assess budget vulnerability.

Even though fare reliance was not included as a feature in the clustering process, we see that the agencies of a particular cluster do tend to fall near each other on the above chart. The agencies suffering higher ridership losses appear to have a higher reliance on fares. This does not bode well for the ability of U.S. transit agencies to weather the COVID-19 pandemic without outside financial support. 
