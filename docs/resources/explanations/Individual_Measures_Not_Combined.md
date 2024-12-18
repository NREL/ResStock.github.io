---
layout: default
title: Why Individual ResStock Measures Should Not Be Combined
parent: Resources
nav_order: 6
---

# Why Individual ResStock Measures Should Not Be Combined

Some users of ResStock data might have questions about the combined effects of multiple upgrade measures being installed together. However, unless the upgrades have been jointly run as an upgrade package in ResStock, the energy savings results should not be added together as doing so could produce misleading results.

For example, in the 2024.1 ResStock dataset, there are two individual packages:
- 2.03: Envelope, Light Touch, package
- 6.01: ASHP, ENERY STAR Ducted, Existing NG Backup

Then these two packages modeled together in package 10.01: ASHP, ENERGY STAR Ducted, Existing NG Backup with Envelope, Light Touch.

Looking at a small subset of homes that received each of these upgrades separately, and then together, showed a site energy savings difference of almost 10%. <ins> That means, adding the package 2.03 site energy savings with the package 6.01 site energy savings resulted in almost 10% greater site energy savings than the package 10.01 where the packages were modeled together. <ins> This is just one example of why multiple upgrade measures should not be added directly together. In this case, the site energy savings were too large. For documentation on these three packages, see the [2024.1 documentation](https://www.nrel.gov/docs/fy24osti/88109.pdf).

For a systems level description, ResStock models the heat transfer of individual representative dwelling units. Any device, person, or animal in the home giving off heat will impact the heat transfer between the interior of the home and the exterior environment. As such, nearly all of the ResStock upgrades interact on a heat transfer level and this will impact both the necessary equipment size for heating and cooling the home as well as the operation time and necessary energy. In the above example, when the air source heat pump is modeled with the envelope, the overall site energy is decreased initially because of the more effective envelope. Therefore the site energy impact that the air source heat pump can have is smaller, because there is less energy being consumed by the home.

The interactions between different thermal and mechanical systems are often not trivial and can have significant energy implications that are only captured when the systems are simulated jointly. <ins> We therefore advise against combining individual upgrade results when examining the combined impacts of multiple upgrade measures. <ins> Users should consult directly from upgrades that have the combined measures simulated. In extremely rare circumstances, energy savings from a piece of electric equipment which gives off minimal heat or which is external to the building (e.g., pool heaters) might be able to be added to another upgrade measure as a rough approximation of energy impacts, but users should exercise extreme caution in this approach.