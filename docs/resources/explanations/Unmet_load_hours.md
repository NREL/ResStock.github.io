---
layout: default
title: Unmet Load Hours
parent: Resources
nav_order: 9
---

## Unmet Load Hours

### Overview
Unmet load hours in EnergyPlus represent the number of hours during which a thermal zone's operative temperature falls outside the desired heating or cooling setpoint range. This metric is commonly used to evaluate HVAC performance, particularly in sizing and control diagnostics, and is often reported in compliance simulations or quality assurance checks. EnergyPlus typically counts unmet load hours at the zone timestep level, comparing zone temperatures against defined setpoint schedules with a default tolerance band of ±0.2°C (±0.36°F). Information on annual unmet load hours from an OS_HPXML standpoint can be found [here](https://openstudio-hpxml.readthedocs.io/en/latest/workflow_outputs.html#annual-unmet-hours). This applies to output columns titled out.unmet_hours.heating.hour and out.unmet_hours.cooling.hour .

### Assumptions behind unmet load hours
The unmet load hours calculation in EnergyPlus is based on several simplifying assumptions. It uses a strict temperature band around setpoints, less than half a degree,  which may not align with real-world thermal comfort expectations or adaptive comfort models. Unmet load hours are also sensitive to timestep resolution—short spikes in temperature deviations may be missed or overemphasized depending on timestep length. The metric assumes accurate HVAC schedules, control strategies, and zone temperature sensing, but doesn't always account for occupancy or whether HVAC systems are actively running. Complex system interactions, such as shared equipment across zones or floating setpoints, may yield misleading results. Known issues in past versions of EnergyPlus have included improper counting of unmet hours during system-off periods or rounding errors at timestep boundaries.

### Recommended use cases
Unmet load hours are most useful during HVAC system sizing, initial design reviews, and performance diagnostics where temperature control issues are suspected. They can help flag zones that are underserved by heating or cooling capacity, or zones affected by poor control strategies. Unmet load hours are also helpful for code compliance or program requirements that set thresholds for acceptable comfort levels, especially in early design or simulation iterations. When used carefully, they can inform design adjustments, control refinements, or re-sizing decisions.

### When to look closely at the results
In ResStock, unmet load hour results should be carefully reviewed when they occur during times when the HVAC system is expected to be off. This includes periods like night setbacks, vacancy, or when ResStock simulates a broken HVAC system. Unmet load hours should also be scrutinized during low-load conditions, where temperature deviations may not noticeably impact comfort. High unmet load hours can sometimes occur due to unrealistic thermostat settings, such as fixed setpoints that don’t reflect actual occupant behavior, or from large setbacks that delay recovery. Because residential systems often use single-zone control, unmet load hours may reflect small temperature deviations rather than true comfort problems. Reviewing zone temperature trends, occupancy assumptions, and HVAC operation schedules is key to determining whether unmet hours indicate a real issue or just a modeling artifact.