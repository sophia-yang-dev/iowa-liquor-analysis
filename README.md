
# Methodology
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



# Problems
### Integrate big data analysis with non-big data tools
We want to do some geospatial analysis, such as interacting with OSM, spatial join two locations, plot maps, etc. Unfortunately, many popular geospatial analysis tools are not big data tools (for example, Geopy, GeoPandas, Osmnx, etc.). Our strategy is to use Spark to “shrink” the data into a minimum number of rows before we feed it to Pandas, do whatever geospatial operation with this smaller table, save the result and convert back to Spark, and use Spark to join back this result with the original big data for whatever further analysis.  
[See More Details](Regional%20Analysis/Problems.md#integrate-big-data-analysis-with-non-big-data-tools)
