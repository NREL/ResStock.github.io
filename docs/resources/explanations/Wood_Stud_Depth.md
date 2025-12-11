---
layout: default
title: Wood Stud Depth and Wall R-Value Calculations
parent: Resources
nav_order: 9
---

## Wood Stud Depth and Wall R-Value Calculations

Wood stud walls in ResStock are characterized by overall wall assembly R-values that can include layers like exterior finish, OSB sheathing, the stud and cavity layer, and drywall. The assembly R-values are used to determine a detailed wall construction set[^1] that incorporates stud depth (2x4 or 2x6), framing factor, and other thermal properties such that the calculated R-value of the whole wall assembly matches the ResStock assembly R-value.

When an insulation level is chosen, either in the baseline model or in an upgrade model, EnergyPlus calculates the heat transfer of the stud and wall cavity in a one-dimensional heat transfer path. Two-dimensional heat calculations are used for foundation walls and slabs in contact with the ground.

[^1]: For more information how ResStock plans to address wall construction, see this GitHub issue: https://github.com/NREL/OpenStudio-HPXML/issues/1182 