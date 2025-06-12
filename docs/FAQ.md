---
layout: default
title: FAQ
nav_order: 6
has_children: false
has_toc: false
---
# Frequently Asked Questions
{: .fw-500}

Below are some frequently asked questions (FAQ) about ResStock and ComStock. The questions are divided into general questions about ResStock and ComStock, specific questions about ResStock, and then questions about how to use the Data Viewer. If you have another question, please email our team at [ResStock@nrel.gov](mailto:ResStock@nrel.gov) and we can get back to you.

## General Questions about ResStock and ComStock

<details>
    <summary>How do I access the dataset?</summary>
    <p>There are several access platforms available to access ComStock and ResStock datasets. See the <a href="https://nrel.github.io/ComStock.github.io/docs/data.html">ComStock Data page</a> and <a href="https://nrel.github.io/ResStock.github.io/docs/data.html">ResStock Data page</a>[ResStock Data page] for more detail about dataset access and links to the public datasets.</p>
</details>

<details>
    <summary>What do the codes used to describe "county_id" and other geographic fields mean?</summary>
    <p>ComStock and ResStock use the National Historical GIS (NHGIS) GISJOIN standard codes for county, census PUMA, and census tract, which are based on Federal Information Processing System (FIPS) codes. The datasets use the 2010 version of the GISJOIN codes--2020 are not available at this time. For more information about the geospatial fields available in the datasets, see this explanation for ComStock, and this explanation for ResStock.
    
    In most ComStock and ResStock datasets, county name is available in addition to the GISJOIN county code. For both tools, the column in the metadata_and_annual_results files on OEDI is called "in.county_name". 
    </p>
</details>

<details>
    <summary>Can I run ComStock and ResStock myself?</summary>
    <p>The code required to run ComStock and ResStock is available on our public GitHub repositories: <a href="https://github.com/NREL/ComStock">https://github.com/NREL/ComStock</a> ; <a href="https://github.com/NREL/ResStock">https://github.com/NREL/ResStock</a>. Other related code repositories are provided on the For Developers page for <a href="https://nrel.github.io/ComStock.github.io/docs/for_developers/for_developers.html">ComStock</a> and <a href="https://nrel.github.io/ResStock.github.io/docs/developers.html">ResStock</a>.
    
    While these resources are available, ComStock and ResStock are complex modeling tools and there is no documentation for running the model other than what exists in the codebase, and we are not able to support running the models at this time. We generally do not recommend running the model unless you have a deep understanding of the methodology and objectives. Please email us at <a href="mailto:ComStock@nrel.gov">ComStock@nrel.gov</a> or <a href="mailto:ResStock@nrel.gov">ResStock@nrel.gov</a>  if you have suggestions for improvements or specific needs.
    </p>
</details>

<details>
    <summary>I am interested in an upgrade measure combination that is not currently available as an upgrade package in the public datasets. Can I combine results from the individual measures?</summary>
    <p>Our general guidance is to <b>NOT<b> combine measure results. There are interactions between most upgrade measures that affect the amount of savings and make results of multiple measures together misleading.
    
    See an explanation and examples on this topic, for <a href="https://nrel.github.io/ComStock.github.io/docs/resources/explanations/combining_measure_results.html">ComStock</a> and <a href="https://nrel.github.io/ResStock.github.io/docs/resources/explanations/Individual_Measures_Not_Combined.html">ResStock</a>.
    
    Please email us at <a href="mailto:ComStock@nrel.gov">ComStock@nrel.gov</a> or <a href="mailto:ResStock@nrel.gov">ResStock@nrel.gov</a> if you have questions about combining specific measures.
    </p>
</details>

<details>
    <summary>I am trying to match buildings between releases, but noticed the building IDs do not match between them.</summary>
    <p>The building IDs and exact building characteristics between releases will not match because we re-sample our input characteristic distributions for every release. However, you can filter the building models using building characteristics to identify similar samples between releases. For instance, using building type, size, location, and wall construction type to identify similar models. The fields with the prefix “in.” show the available model inputs that you can use to do the comparison. You can see a complete list and description of available fields in the “data_dictionary.tsv” file on the OEDI Data Lake.</p>
</details>

<details>
    <summary>Are descriptions available for the end-use categories and fields available for filtering?</summary>
    <p>Descriptions of each of the building characteristics and the end-use categories can be found in the “data_dictionary.tsv” file. Descriptions of the values used in those filters can be found in the “enumeration_dictionary.tsv”. Both files can be downloaded from the OEDI Data Lake and are unique to each dataset release. Use the correct data dictionary for the relevant dataset. They can be opened with Excel or a text editor.

    Links to the OEDI Data Lake for each dataset release can be found on the <a href="https://nrel.github.io/ComStock.github.io/docs/data.html">ComStock Data page</a> and <a href="https://nrel.github.io/ResStock.github.io/docs/data.html">ResStock Data page</a>.
    </p>
</details>

<details>
    <summary>What are the data units?</summary>
    <p>ComStock and ResStock data have multiple units. For annual results data downloaded from the Open Energy Data Initiative (OEDI) data lake, units can be found in the "data_dictionary.tsv" file. Some fields will also have the units in the column header at the end of the name (e.g., "out.electricity.total.jan.energy_consumption..**kwh**"). Timeseries energy consumption data on OEDI are provided in kWh. Natural gas, fuel oil, and propane are output in kwh--this is intentional though unconventional.

    The Data Viewer provides energy data in metric units, visible in the y-axis label. Depending on the scale of energy being shown, the metric prefix will automatically adjust (T for tera, G for giga, M for mega, etc.).

    For Tableau dashboards, use the relevant column headers or the graph axis to see the units.
    </p>
</details>

<details>
    <summary>What is the timezone of the timestamps?</summary>
    <p>The timestamps of all load profiles have been converted to Eastern Standard Time, to prevent issues when aggregating across time zones. The underlying modeling was conducted using local standard time for each location, with occupant schedules adjusted for daylight savings as applicable. All EnergyPlus timeseries outputs were converted from local standard time to Eastern Standard Time for publication in the web Data Viewer, Data Viewer exports, timeseries aggregates, and individual timeseries parquet files. In converting from local Standard Time to Eastern Standard Time, if necessary the last few hours of each dataset were moved to the beginning of the timeseries. For example, the first two hours of data from Colorado in Eastern Standard Time (Jan 1, midnight to 2 AM) were originally modeled as the last two hours of the year in Mountain Standard Time (Dec 31, 10 PM to midnight) using the corresponding weather.</p>
</details>

<details>
    <summary>Do the timeseries aggregates have the sample weighting factors applied?</summary>
    <p>Yes. The aggregates represent the total relevant building stock with all relevant weights applied (e.g., all small office buildings in the state of Colorado), not just the sum of the model results.</p>
</details>

<details>
    <summary>Are weather data files available in EPW format?</summary>
    <p>Weather data used for the modeling have been provided in .csv format for regression modeling, forecasting, or other analyses. The TMY3 weather files in EnergyPlus input format (EPW) can be downloaded from the NREL Data Catalog (https://data.nrel.gov/submissions/156), with filenames that correspond to county IDs in the ResStock and ComStock metadata. EPW format weather files for 2018 or other actual meteorological years (AMY) have not been publicly released. These files can be purchased from private sector vendors. See <a href="https://energyplus.net/weather/simulation">here</a> for a list of providers.</p>
</details>

<details>
    <summary>Is there an API to access data without downloading locally?</summary>
    <p>Currently, there is no API. However, we have posted a <a href="https://www.youtube.com/watch?v=qSR1MFpSiro&list=PLmIn8Hncs7bEYCZiHaoPSovoBrRGR-tRS&index=4">tutorial</a> showing how to load the datasets into cloud services such as Amazon Web Services (AWS) so the data can be queried by analytic tools like Athena.

    Example notebooks and SQL queries are also available on the <a href="https://nrel.github.io/ComStock.github.io/docs/resources/how_to_guides/example_scripts.html">Access ComStock datasets programmatically</a> page, and more will be added as we develop them. The queries and example notebooks are a good starting point for accessing ResStock programmatically, too.</p>
</details>

<details>
    <summary>What software can I use to open the .parquet files?</summary>
    <p>Parquet files can be read using programming languages such as Python, using the pyarrow package. For other options, see <a href="https://arrow.apache.org/docs/index.html">https://arrow.apache.org/docs/index.html</a>. There are a few third-party graphical tools for viewing parquet files, but we have not tested them and the third-party support is limited.

    See below for example Python code to convert parquet file to csv.
        import pandas as pd
        import os
        folder_path = 'C:/Users/username/Documents/EUSS/Results’
        file_name = ‘813-2’
        suffix = '.parquet'
        file = pd.read_parquet(os.path.join(folder_path, file_name+suffix))
        new_suffix = '.csv'
        file.to_csv(os.path.join(folder_path, file_name+new_suffix), index = False)
    </p>
</details>

<details>
    <summary>Does the timestamp represent the beginning, middle, or end of each 15-minute interval?</summary>
    <p>The timestamp indicates the end of each 15-minute interval. So "12:15" represents the energy use between 12:00 and 12:15.</p>
</details>

## ResStock questions

<details>
    <summary>Where can I find information about input data sources, modeling methodology, and assumptions?</summary>
    <p>ResStock reference documentation is available in the Published Datasets section of the <a href="https://nrel.github.io/ResStock.github.io/docs/data.html">Data page</a>. This includes baseline and upgrade measure information. We generally publish an updated version with every dataset release.</p>
</details>

<details>
    <summary>Is ResStock credible?</summary>
    <p>Yes. The models underwent extensive calibration as part of the End Use Load Profiles (EULP) project where we compared model load profiles to AMI data from around the country, and updated baseline model schedules, power densities, among other things using various data sources. Reference the <a href="https://www.nrel.gov/docs/fy22osti/80889.pdf">EULP final report</a> for more details. The EULP project concluded in 2021.

    For details about how to determine whether the models are appropriate for a specific analysis, reference <a href="https://nrel.github.io/ResStock.github.io/docs/resources/explanations/Considerations_for_ResStock_Calibration_and_Validation.html">this explanation</a>.</p>
</details>

<details>
    <summary>Which dataset release should I use?</summary>
    <p>We recommend using the latest data release whenever possible. However, older datasets still provide valuable information and can be used if newer datasets are not appropriate for a specific use. We do not recommend a comparison of upgrade measures across different dataset releases due to the changes and improvements made in each dataset release. Each new dataset release includes its own set of upgrade measures, some of which are repeats, and improvements made to the baseline model and modeling methodology. See the [Data page](https://nrel.github.io/ResStock.github.io/docs/data.html) for a list of available datasets and access links, as well as technical documentation for the ResStock tool.</p>
</details>

<details>
    <summary>What are weights in ResStock and how are they used?</summary>
    <p>Weights in ResStock represent the number of real buildings in the U.S. building stock that a ResStock model represents. Each ResStock dataset release has a different weighting factor for the building models. As seen in [this paper](https://www.nrel.gov/docs/fy22osti/80889.pdf), our model or sample weights are constructed using U.S. EIA 2009 RECS microdata. Use the weights by multiplying the column of interest by the weight. Some results columns already have the weight applied. These have the word “weighted” in the name.</p>
</details>

<details>
    <summary> What building types does ResStock model?</summary>
    <p>ResStock models most types of housing including single-family, multifamily, and manufactured or mobile homes. See [this explanation](https://nrel.github.io/ResStock.github.io/docs/resources/explanations/Building_Types.html) for more detail on what is not modeled.</p>
</details>

<details>
    <summary>Where is there documentation on what technologies are available in the upgrade measures?</summary>
    <p></p>
</details>

<details>
    <summary>Where is there documentation on what technologies are available in the upgrade measures?</summary>
    <p>The [Data page](https://nrel.github.io/ResStock.github.io/docs/data.html) links to each dataset and the dataset technical documentation which covers the technologies and upgrades that are available. </p>
</details>

<details>
    <summary>Does ResStock model rooftop solar PV?</summary>
    <p>Yes, ResStock does model rooftop solar PV. See more details on rooftop PV, assumptions, and limitations on [this explanation](https://nrel.github.io/ResStock.github.io/docs/resources/explanations/PV_System_Assignment_and_Distributions.html).We recommend using [PVWatts](https://pvwatts.nrel.gov/) or [ReOPT](https://reopt.nrel.gov/tool) to evaluate PV for a more comprehensive analysis. </p>
</details>