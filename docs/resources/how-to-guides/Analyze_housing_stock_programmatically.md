---
layout: default
title: Analyze Housing Stock Programmatically
parent: resources
nav_order: 1 # TODO - change this potentially
---
# How To: Analyze Housing Stock Programmatically

These example notebooks demonstrate how users can access the ResStock datasets programmatically.

## AWS Athena and SQL Queries
- [Example AWS Athena Queries]({{  site.baseurl  }}{% link docs/resources/how-to-guides/aws_athena_queries.md %}). These example address three questions using the ResStock 2025 Release 1 dataset.

## Python

### Jupyter Notebook
These example Jupyter notebooks were created using the ResStock 2025 Release 1 dataset. Some dataset attributes, like column names or weighting factor applications, may change in the future. Check out the [Data page](https://nrel.github.io/ResStock.github.io/docs/data.html) for the most up to date information on ResStock datasets.

Download the below notebooks for the formatting to properly render. Previewing the notebooks online can present unreadable formatting.

- [Download Annual Baseline and Upgrade Data]({{  site.baseurl  }}{% link docs/resources/how-to-guides/access_annual_data_programmatically.ipynb %}) Example Jupyter notebook for pulling annual baseline and upgrade results from the Open Energy Data Initiative (OEDI) data lake. This example filters to a specific geography and housing type, and then plots a comparison.
- [Download Timeseries Baseline and Upgrade Data]({{  site.baseurl  }}{% link docs/resources/how-to-guides/access_timeseries_data_programmatically %}) Example Jupyter notebook for pulling timeseries aggregate files from the OEDI data lake for a certain geography and housing type, and then plots a comparison.