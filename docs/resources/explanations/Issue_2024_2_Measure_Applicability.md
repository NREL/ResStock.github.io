---
layout: default
title: ResStock 2024 Release 2 Measure Applicability
parent: Resources
nav_order: 10
---

# Issue Report: ResStock 2024 Release 2 Measure Applicability
## Summary of Issue
Certain models in the ResStock 2024 Release 2 dataset do not have the dual-fuel measures applied despite the documentation stating that they do.

## Status
Current. Impacts ResStock 2024 Release 2 (ResStock 2024.2) only.

## Details
This issue is specific to models with all of the following characteristics: central AC, non-ducted heating, no shared HVAC, heating fuel of natural gas, propane, or fuel oil, and HVAC ducts (for the central AC) . These models have Applicability = False for the measures that include dual-fuel heat pumps in ResStock 2024.2 (measure numbers 4, 9, 14). As a result, the measure results for these model-measure combinations are the same as the baseline results. According to the [ResStock 2024.2 documentation](https://oedi-data-lake.s3.amazonaws.com/nrel-pds-building-stock/end-use-load-profiles-for-us-building-stock/2024/resstock_tmy3_release_2/resstock_documentation_2024_release_2.pdf) these measures should be applicable to these models.

## Impacts
This documentation-results applicability discrepancy impacts 2.1% of all models in the ResStock 2024.2 dataset nationwide for the three impacted measures. The portion of impacted models varies by geography, from a statewide maximum of 8.5% in New Jersey to a statewide minimum of 0.2% in Florida. Because the dataset weight is constant for all models in ResStock 2024.2, the portion of the represented building stock impacted is the same as the portion of models.  

It is therefore not possible to use the ResStock 2024.2 dataset to conduct analysis on the impacts of the dual-fuel measures and measure packages when applied to certain subsets of the building stock that the documentation indicates should be possible. This most prominently includes houses that in the baseline have central AC for cooling and non-electric boilers for heating. It also includes all other dwelling units with central AC, non-ducted heating, no shared HVAC, and a heating fuel of natural gas, propane, or fuel oil.

## Recommendation
Users should interpret all 2024.2 results of measures that include dual-fuel heat pumps with the correct applicability context. Users that wish to analyze the impact of dual-fuel measures for the impacted subset of the building stock should consider using dual-fuel measure results from other published ResStock datasets, such as Measure 5 from ResStock 2022.1 (documentation [here](https://oedi-data-lake.s3.amazonaws.com/nrel-pds-building-stock/end-use-load-profiles-for-us-building-stock/2022/EUSS_ResRound1_Technical_Documentation.pdf)) or the 10+ relevant measures from ResStock 2024.1 (see Table 6 in the documentation [here](https://docs.nrel.gov/docs/fy24osti/88109.pdf) for a guide). 