---
layout: default
title: One Row of Data Is Not One Real House
parent: Resources
nav_order: 3
---

# One Row of Data Is Not One Real House
When working with raw ResStock data, it is easy to assume that each line of data or each file represents one real U.S. house. However, this is not the case. Instead, each row of data in a ResStock metadata file has one sampled dwelling unit that represents a segment of the housing stock with the same characteristics. A row of data is just representative and cannot be tracked or linked to an actual building or address.

For example, in the illustrative table below with a subset of ResStock metadata, the first few columns are labeled *bldg_id* and *weight*.

| bldg_id | weight | in.city | ... | in.geometry_building_type | in.geometry_floor_area |
| --- | --- | --- | --- | --- | --- |
| 186 | 242.13101 | AL, Huntsville | ... | Single-Family Detached | 2,500--2,999 |
| 212 | 242.13101 | AL, Mobile | ... | 3 or 4 unit | 4000+ |
| 239 | 242.13101 | AL, Birmingham | ... | Mobile Home | 750--999 |

*bldg_id* is the identification number of the dwelling unit simulated in ResStock. *weight* is the sample weight, or the number of real dwelling units in the U.S. housing stock that the individual *bldg_id* represents. In the table above, *bldg_id* 186 has a weight of 242.13101, meaning that this simulation represents approximately 242 real single-family detached homes in Alabama. With ResStock's typical quota-based sampling approach, each ResStock run equally weights all housing units. For this example, each of the 550,000 sampled housing units in ResStock represents about 242 real housing units. The *weight* field is included in all ResStock data files.
<!--
The *weight* field is also the appropriate factor to scale ResStock energy and emissions outputs as discussed in the Weighting/Sampling example. -->

The other column titles such as *in.city*, *in.geometry_building_type*, and *in.geometry_floor_area* highlight different characteristics about the line of data. *in.city* represents state, city so the first line represents Alabama, Huntsville. *in_geometry_building_type* is the geometry building type and the format *in.* represents that it is in an input. *in.geometry_floor_area* provides the square footage of the floor area of the dwelling unit. Descriptions of each column name can be found in the data_dictionary files in all ResStock datasets.

For a comprehensive solution that limits uncertainty to about 15%, we recommend using at least 1,000 samples (representing about 242,000 real dwelling units) in this example. More guidance on this topic can be found in the explanation titled ["Why At Least 1,000 Samples Is Recommended"]({{ site.baseurl }}{% link docs/resources/explanations/Why_at_Least_1000_Samples_is_Recommended.md %}).

An additional point to emphasize is that ResStock models dwelling units, not entire buildings. For example, in the table above, *bldg_id* 212 says the *in.geometry_building_type* is 3- or 4-unit. That means the row of data represents one dwelling unit or one apartment within a building that has 3 or 4 units total. The point is especially important for analyses that focus on multifamily buildings or for regions that have a high proportion of multifamily buildings.