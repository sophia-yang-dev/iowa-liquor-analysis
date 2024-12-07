
# Problem Definition:
# Methodology
## Data Processing and Cleaning
  
[See More Details](Data_Processing_Cleaning/DataCleaning_README.md#data_processing_cleaning)  

## Sales Basic Info

[See More Details](Sales%20Basic%20Info/Readme.md)
## Sales Trend Analysis

[See More Details](SalesTrends_Analysis_README.md)
## Regional Analysis
We studied two topics regarding regional information. One is more general on the sales analysis at County level. The other is more local focusing on the local geospatial factors that could influence sales.  
### Topic 1: Regional Analysis on County Level
Iowa State has 99 Counties. We wonder how liquor sales and consumption differ across Counties. There are a few questions we can ask that might be interesting.
* Q1. What are the top five Counties with the most liquor stores?
* Q2. Which County spend the most money on liquors each year?
* Q3. People from which County drink the most? How much do they drink on average?
* Q4. Which County has the best performing liquor stores on average?  

To perform regional analysis, we implemented the following tasks:
* Summarize Liquor Sales and Consumption Data by County
* Combine with US Census Population Data
* Plot Findings on Iowa State Map

[See More Details](Regional%20Analysis/Topic1.md#methodology)

### Topic 2: What Geospatial Factors Might Influence Liquor Sales
Some liquor stores have higher sales, some lower. We wonder, could there be any spatial factors affecting the store performance? For example, if a store is surrounded by bars or restaurants, maybe they will purchase beverages from the liquor store quite often. Or, if there is a stadium nearby, people might buy more drinks when there are sports events. In order to study these geospatial factors, we again retrieve data from OpenStreetMap, and explore the correlation between these factors and store sales performances. From the County-level analysis, we have already known that Polk County has the most number of liquor stores, and also best performing stores on average. So Polk County could be a good example for us to explore.

To perform geospatial analysis, we implemented the following tasks:
* Search Places of Interests (POI) by OpenStreetMap
* Count Number of POIs Within 2km for each Liquor Store
* Summarize Transactions, Sales, and Consumption Data by Store
* Analyze Correlation between Store Performance and Nearby POIs

[See More Details](Regional%20Analysis/Topic2.md#methodology).  

## Crime and Liquor Consumption Analysis


# Problems
### Integrate big data analysis with non-big data tools
We want to do some geospatial analysis, such as interacting with OSM, spatial join two locations, plot maps, etc. Unfortunately, many popular geospatial analysis tools are not big data tools (for example, Geopy, GeoPandas, Osmnx, etc.). Our strategy is to use Spark to “shrink” the data into a minimum number of rows before we feed it to Pandas, do whatever geospatial operation with this smaller table, save the result and convert back to Spark, and use Spark to join back this result with the original big data for whatever further analysis.  
[See More Details](Regional%20Analysis/Problems.md#integrate-big-data-analysis-with-non-big-data-tools)
### Messy data from OpenStreetMap
OpenStreetMap is good in its rich contents and API services, and it is totally free. However, because anyone can annotate, the data on OSM is sometimes messy. Here are some situations we encountered and how we dealt with:

* When searching locations based on store name or store address.
* Looking for tags that are relevant but cannot find any result.
* Repetitive annotation of the same building.
[See More Details](Regional%20Analysis/Problems.md#messy-data-from-openstreetmap)
### Normalize data for fair comparision
This one is just a small tips when we tried to compare sales among different stores. We noticed that it is not fair to compare the total sales or total transactions, since some shop has opened for several years but other stores might just opened for a few months. It also does not help if divide the sales with the same time span (say for example 10 years of our dataset). The method we use is to find the earlist and latest record a store has, divide the difference by 365 days and round to a whole year. Now the normalization is store-wise, depending on the number of years it has opened.

# Results
## Basic Sales Data

[See More Details](Sales%20Basic%20Info#results)
## Sales Trend Analysis

[See More Details](SalesTrends_Analysis_README.md#result-analysis)
## Regional Analysis
### Regional Analysis on County Level
[See More Details](Regional%20Analysis/Topic1.md#result)

### Geospatial Factors that Influence Liquor Sales
[See More Details](Regional%20Analysis/Topic2.md#result)
# Project Summary

* Getting the data: Acquiring/gathering/downloading.(1). 
* ETL: Extract-Transform-Load work and cleaning the data set. (3)
* Problem: Work on defining problem itself and motivation for the analysis.(3).  
We have already answered it in “Problem Definition” and “Some Questions We Intend to Answer” sections.
* Algorithmic work: Work on the algorithms needed to work with the data, including integrating data mining and machine learning techniques.(4). 
* Bigness/parallelization: Efficiency of the analysis on a cluster, and scalability to larger data sets.(1). 
* UI: User interface to the results, possibly including web or data exploration frontends. (2). 
We used the Github Pages and Github CI/CD pipleine to create this website to host our report and User interface to result of our analysis and Visualizations.  
* Visualization: Visualization of analysis results. (3). 
We used Matplotlib python package and Orange Data Mining to plot a lot of charts to demonstrate the result of our analysis, such as scatter plot, bar charts and line charts.Instances of these can be found in the report and “README.md” of each problem.  
* Technologies: New technologies learned as part of doing the project. (3). 
A few technologies we learned and used while completing this project are Orange Data Mining, Amazon S3, Python Spark, Amazon AWS EC2, Socrata, Matplotlib, Github Pages, Kafka streaming, Parquet file format.  
Total: 20. 

Project Contributors: Sophia Yang (xya134, 301627219), Yingzi Yuan (yya, ), Weiwei Zhang (, ), Wenqian Yue( , ) 
