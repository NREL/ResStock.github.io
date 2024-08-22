---
layout: default
title: Geographic Fields and Codes
parent: resources
nav_order: 4
---

# Geographic Fields and Codes
ResStock provides many geographic fields to allow for a variety of analysis. Many of the geographic codes are self explanatory, like the name of the county, but there are some that are not as user friendly. Sometimes these codes can represent counties, census tracts, and Public Microdata Areas (PUMAs). ResStock uses the National Historical GIS (NHGIS) GISJOIN standard codes for county, Census PUMA, and Census Tract. These are based on Federal Information Processing System (FIPS) codes. Example names of columns that include these geographic codes include in.county or in.county_and_puma. They can even be seen in the Data Viewer when trying to filter by PUMA. It starts with a G and then has seven or eight numbers after it. Below is an example.

![](../../../assets/images/gis-join.png)

Two steps are required to understand a GISJOIN string. First the geography needs to be specified using a numeric FIPS code or codes. There ae many resources that can help with this, and one of them is this [Wikipedia page listing State and County FIPS codes](https://en.wikipedia.org/wiki/List_of_United_States_FIPS_codes_by_county). Specifying Census Tracts is generally best done using a Geographic Information System (GIS) tool, but maps for 2010 and 2020 can be found [here](https://www.census.gov/geographies/reference-maps/2010/geo/2010-census-tract-maps.html) and [here](https://www.census.gov/geographies/reference-maps/2020/geo/2020pl-maps/2020-census-tract.html) respectively. [This](https://nrel.sharepoint.com/sites/NRELBuildings/Shared Documents/BuildStock/Front Office/ResStock Documentation/General Audience/census.gov/geographies/reference-files/time-series/geo/relationship-files.2020.html) is a good resource for seeing how Census Tracts change over time and how to use the files between different years.

Additionally, each published dataset has a spatial lookup table: [spatial_tract_lookup_table.csv](https://data.openei.org/s3_viewer?bucket=oedi-data-lake&prefix=nrel-pds-building-stock%2Fend-use-load-profiles-for-us-building-stock%2F2021%2Fresstock_amy2018_release_1%2Fgeographic_information%2F) is one example. County and PUMA codes can be looked up using the "nhgis_county_gisjoin" and "nhgis_puma_gisjoin" columns respectively. If you want to find the pre-aggregated timeseries file for a county or PUMA, you can use this lookup to find the code for the county or PUMA of interest.