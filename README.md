# COVID-19 Transit Ridership Patterns
## Caleb Sutton | MUSA 550

For my final project in Geospatial Data Science in Python, I created a single-page blog to explore transit ridership during the COVID-19 pandemic. I did a clustering analysis because I wanted to understand which agencies have fared similarly in regards to ridership. The blog itself is very detailed in regards to my methods and conclusions, so I'll provide a simple overview here. 

## Steps

- download data from National Transit Database on monthly ridership and budget
- clean data in a Jupyter notebook
- calculate percent change columns for April, October, and July 2020
- perform a K-means clustering with 5 clusters on those 3 percent change columns
- explore descriptive statistics to name clusters
- explore the relationship between clusters and reliance on fare revenue 
- add charts and a map of the clusters to the blog

Though I did the elbow method to select the number of clusters, it did not have a strong elbow. I ultimately selected 5 clusters because I wanted to better separate out those agencies with growth during 2020 instead of the typical loss. 

Link to the website: https://csutton6.github.io/covid-transit/

Link to the repo with a jupyter notebook and data: https://github.com/MUSA-550-Fall-2020/final-project-ksutt
