---
layout: default
title: Getting Started
nav_order: 1
---

# Getting Started with ResStock
{: .fw-500 }

![](/assets/images/city-skyline-istock-1155981768.jpg)

## What Is ResStock?

The U.S. residential building sector stock energy model, ResStock™, is a highly granular, bottom-up model that uses multiple data sources, statistical sampling methods, and advanced building energy simulations of the residential building stock across the contiguous United States.

ResStock asks and answers two main types of questions: 1) How is energy used in the U.S. housing stock? and 2) What are the impacts of modifying the housing stock with different technologies?

ResStock, along with our partner model ComStock™, make up BuildStock. BuildStock allows for full modeling of the U.S. building stock.

This document serves as a guide and resource for the methodology and assumptions behind ResStock.

## Quick Links

### Access the Dataset
Visit the [Datsets page](https://resstock.nrel.gov/datasets) for access to the published datasets and details about the ways to access them.

## What does ResStock do
As the demand for decarbonization initiatives expands across the country, the need for energy modeling does as well. ResStock meets this need as a national residential building energy stock model. It enables a new approach to large-scale residential energy analysis across the U.S. by combining large public and private data sources, statistical sampling, detailed sub-hourly building simulations, and high-performance computing. ResStock is funded by the U.S. Department of Energy (DOE), and built by the National Renewable Energy Laboratory (NREL).

ResStock is more than just a basic modeling tool for analyzing energy efficiency and consumption in residential buildings. It integreates a variety of features and capabilities that make it a comprehensive analytical platform. Here's a broader description of it's functionalities:

1. **Simulation Tool**: ResStock performs detailed simulations that can project the impact of various energy efficiency measures acros millions of building prototypes, tailored to different climates, construction types, and demographics. This allows for a granular analysis of potential energy savings and efficiency improvements.

2. **Policy Analysis Instrument**: ResStock provides data and insights that can help inform state and local energy policies by illustrating the potential impacts of building code modifications, energy efficiency programs, and retrofit incentives.

3. **Decision Support System**: By offering robust datasets and modeling capabilities, ResStock aids decision-makers in prioritizing energy strategies that are most effective for specific regions or types of buildings.

4. **Research and Development Tool**: ResStock is used by researchers to study residential energy trends, assess energy needs, and evaluate the market potential of new energy technologies.

5. **Educational Resource**: ResStock also serves as an educational tool for professionals in the energy sector, helping them understand the complexities of residential energy use and the potential for energy efficiency gains.

In summary, ResStock could be aptly described as an **advanced energy analysis platform** that combines elements of simulation, policy analysis, decision support, research facilitation, and educational outreach. These elements are all focused on enhancing residential energy efficiency and understanding energy consumption patterns.

ResStock helps states, municipalities, utilities, and manufacturers understand the make-up of their area's housing stock; identify the energy, emissions, or economic impacts of energy efficiency or electrification measures; and explore the impact of new technologies such as cold-climate heat pumps for both customers and the grid.

In the pursuit of understanding when and where energy consumption occurs, ResStock can be tailored to answer the core questions many people have (explained in the next section). The results are available in multiple different formats and resolutions:

| Format | Resolution |
| --- | --- |
| Spatial | U.S., census division, climate zone, state, county, balancing authority, ISO/RTO, and Public Use Microdata Areas (PUMAs)|
| Temporal | 15 minutes to annual aggregations |
| Sectoral | All U.S. housing by Census and RECS classifications |

To achieve clean energy objectives and enhance the alignment of building stock with the evolving power grid, a detailed analysis method is essential. This method must be able to evaluate the location, timing, and methods through which clusters of buildings use energy and identify potential energy savings. This tool is designed to aid professoinals and researchers engaged in advancing these initiatives.

## What Questions Can and Cannot be Answered with ResStock
These are the type of questions that can be answered via data processing, distillation, and visualization of this dataset. This is not a complete list.

_Questions that can be answered:_
1. Housing makeup and current snapshot of energy consumption

    a. How many homes are heated by electricity versus gas? How leaky or well insulated are these homes?

    b. How are low-income and renter-occupied housing different from other housing units?

    c. What are the largest opportunities for energy efficiency and electrification?

2. Technology potentials and what-if scenarios

    a. What is the range of savings per household if X, Y, or Z are implemented? What are the total expected savings for a program or community with X, Y, or Z?

    b. What are the energy, carbon, and utility bill impacts of a home envelope upgrade versus a heat pump upgrade?

3. Addressable questions with timeseries and customization?

    a. Does residential electrification shift a region from summer peaking to winter peaking?

    b. What is the total change in peak demand from energy efficiency?
    
    c. How do higher efficiency equipment or envelope improvements affect the change in peak demand?

These are the types of questions that ResStock data alone cannot answer.

_Questions that cannot be answered:_
1. What is the potential for rooftop or community solar?
2. How many homes qualify for the Weatherization Assistance Program or other specific policies?
3. How might different income groups leverage financing mechanisms for their home upgrades?
4. What is the cost of installing a heat pump?
5. What is the electrification potential for a specific home address?

## How to use ResStock
ResStock provides access to results through many different forms, including a web data viewer, dashboards, and raw data available for download.
ResStock leverages and is deeply indepted to DOE's open source buidling energy modeling ecosystem of [Open Studio<sup>R</sup>](https://openstudio.net/) and [Energy Plus<sup>R</sup>](https://energyplus.net/). 