---
layout: default
title: Considerations for ResStock Calibration and Validation
parent: Resources
nav_order: 1
---

# Considerations for ResStock Calibration and Validation
A common question is whether ResStock has been appropriately calibrated for a specific use case. The answer is dependent on many factors, including the robustness of the relevant model inputs, the type of data needed, the housing segment of interest, and the user's tolderance for uncertainty.
ResStock has been calibrated and validated as part of the three-year [End Use Load Profiles (EULP)](https://www.nrel.gov/buildings/end-use-load-profiles.html) project. EULP calibrated and validated ResStock against 33 measured datasets including utility load research data, advanced metering infrastructure (AMI) data from utilities, the EIA Residential Energy Consumption Survey (RECS) monthly data, and submetered datasets. ResStock is continually improved through new input and calibration/validata data as it becomes available.

There are two main ways to understand the calibration process and model inputs:
1. The [EULP Final Report](https://www.nrel.gov/docs/fy22osti/80889.pdf) provides a detailed description of the initial ResStock calibration and validation process and results.

    a. Section 2.3.6 Empirical Data Used for Residential Calibration and Validation

    b. Section 4.1 Final Calibration and Validation Results - Residential

2. [ResStock Documentation](https://www.nrel.gov/docs/fy18osti/68670.pdf) provides the methods, assumptions, and data sources used in ResStock. (Note, this documentaiton is for an older version of ResStock. New documentation is being written with expected release in Fall 2024.)

Determining if ResStock is appropriate for a given use case is ultimately a judgement call for the user with the combined help of these resources. **The ResStock team and the U.S. Department of Energy are not responsible for any actions or consequences that arise because of the assumptions, conclusions, or performed work that is based on ResStock.** The EULP Final Report should be referenced to understand how well ResStock aligns to other available data sources, both annually and subhourly. ResStock documentatino describes the data srouces and assumptions used to build the models. Keep in mind that the data sources used in ResStock potentially have their own errors and biases, and which can be reflected in ResStock. ResStock is a model of residential housing, not an actual representation of residential housing. Therefore, users should compare their own data with ResStock whenever possible. Users should rely on their own judgement, with the resources available, to decide if ResStock is suitable for their use case.