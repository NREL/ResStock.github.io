---
layout: default
title: PV System Assignment and Distributions
parent: Resources
nav_order: 8
---

# PV System Assignment and Distributions

## Overview
ResStock assigns photovoltaic (PV) systems to residential dwelling units based on housing characteristic distributions. However, the data sources[^1]  for PV systems do not include specific building characteristics. Instead, they provide:
- The number of PV systems by county
- A distribution of PV system sizes
- A distribution of PV system orientations

The units with PV systems are applied to single-family detached units with a system size and orientation assigned by the input characteristics and not any electricity consumption, roof area, or roof orientation information.

## Limitations and Assumptions

1. PV systems are **not** sized based on individual building energy consumption. A system may be significantly over- or under-sized for a given dwelling.
2. No checks are performed to verify if a PV system fits on the roof or if the roof is oriented correctly for the assigned PV system.
3.	Snow cover is **not** accounted for in PV energy estimates.
4.	Mobile homes, multi-family units, and single-family attached homes do not have PV systems in ResStock. As a result, single-family detached units may have a slightly higher-than-expected PV system saturation.
5.	Vacant units do **not** have PV systems.
6.	Imposed an upper bound of 14 kWDC, which contains 95% of all installations. 
7.	Counties with PV system counts less than 10 are backfilled with aggregates at the State level.

## Recommended Use Cases
ResStock PV data is best suited for:
1. Aggregate energy estimates
2. Baseline PV utility-level annual load and load shape estimates

## When to Scrutinize the Results
1. Distributional Analysis
- In both baseline and upgrade scenarios, PV-equipped units may skew results or create unrealistic outliers.

2. Units with Large Negative Net Energy Consumption
- If a unit has an oversized PV system, it may show significantly negative net energy consumption.
- Since ResStock does not size PV systems to match individual energy loads, this can also affect utility bill estimates, which may appear negative depending on other fuel consumption.


[^1]: American Community Survey unit counts and RiDER project data on PV installation that combines LBNL's 2020 Tracking the Sun and Wood Mackenzie's 2020 Q4 PV reports.