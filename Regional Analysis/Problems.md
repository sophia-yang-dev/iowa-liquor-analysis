# Challenges
## Integrate big data analysis with non-big data tools
We want to do some geospatial analysis, such as interacting with OSM, spatial join two locations, plot maps, etc. Unfortunately, many popular geospatial analysis tools are not big data tools (for example, Geopy, GeoPandas, Osmnx, etc.). Those tools are well integrated with Pandas so making geospatial analysis with Pandas very convenient and easy. 

There indeed is one big data tool that can handle large size of spatial data, which is the [Apache Sedona](https://sedona.apache.org/latest/setup/overview/) (previously called GeoSpark). However, the documentation of Sedona is not that friendly, and it costs a lot of time making the environment and dependencies work.

But wait, are we really working with large geospatial data? Think about the scenario where we want to use geospatial data. It is only when we want to find the store locations, or plot store distribution, or find nearby amenities near stores. It is all about stores. So how many stores do we get? Check the original data and we found, there are only 3354 stores in total, which means, the geospatial data we want to use is at most 3354 rows. We can tolerate that with Pandas and other Pandas-friendly tools.

So our strategy is quite straightforward, we use Spark to “shrink” the data into a minimum number of rows before we feed it to Pandas, do whatever geospatial operation with this smaller table, save the result and convert back to Spark, and use Spark to join back this result with the original big data for whatever further analysis. Which means, we only use Pandas when we have to, and we always check the number of rows we send to Pandas.

This strategy can be reflected in the implementations of [POI analysis](Topic2.md#count-number-of-pois-within-2km-for-each-liquor-store) and [filling missing location data]().

## Messy data from OpenStreetMap

## Tips on normalizing data for comparison
