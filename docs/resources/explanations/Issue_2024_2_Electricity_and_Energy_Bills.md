---
layout: default
title: ResStock 2024 Release 2 Electricity and Energy Bills
parent: Resources
nav_order: 9
---

# Issue Report: ResStock 2024 Release 2 Electricity and Energy Bills
## Summary of Issue
The electricity bills and energy bills are incorrectly calculated in the ResStock™ 2024 Release 2 (ResStock 2024.2) dataset. This has a moderate impact on electricity and energy bill results and a large impact on the electricity bill savings and energy bill savings results, which in some cases are nonsensical. 

## Status
Impacts ResStock™ 2024 Release 2 (ResStock 2024.2) only. Preliminary investigation complete. Detailed investigation complete.

## Details
ResStock™ calculates electric utility bills using two components. The first is a fixed charge, annual or monthly, which represents meter charges and other non-volumetric portions of electricity rates. The second is a volumetric charge, a utility rate in dollars per kilowatt-hour that is multiplied by the net electricity consumption.[^1]  ResStock calculates the total electricity bill as the sum of these two components.

The ResStock 2024 Release 2 (ResStock 2024.2) dataset intended to calculate the electric utility bill using a fixed charge of $10/month (or $120/year) for each dwelling unit, and a volumetric charge that varies by state and is calculated from 2022 EIA state average residential electricity data. This is the approach detailed in the dataset release [documentation](https://oedi-data-lake.s3.amazonaws.com/nrel-pds-building-stock/end-use-load-profiles-for-us-building-stock/2024/resstock_tmy3_release_2/resstock_documentation_2024_release_2.pdf). In using the dataset, the ResStock team discovered that the published electricity rates were not calculated using these values. Instead, the dwelling units with measure packages applied used the OpenStudio-HPXML default electricity rate values, and the dwelling units in the baseline and dwelling units in measure packages where the measure package was not applicable used the correct volumetric charges but a fixed charge of $10/year instead of $120/year for each dwelling unit, and did not use the standard OpenStudio-HPXML approach for annual excess sellback of onsite PV generation in the case of net metering. This means that there are three different sets of electric rate information:

- One set was used in the documented methodology and in the rate outputs
- One set was used in the baseline bill outputs (and in the bill outputs for measure package datasets for dwelling units where applicability = False)
- One set was used in the bill outputs in cases where a measure package was applied.

ResStock calculates the total energy or utility bill as the sum of the electricity, natural gas, propane, and fuel oil energy bills. The error in the electricity bill results therefore also carries through into the energy bill results.

## Impacts
The electricity bill results in the ResStock™ 2024 Release 2 (ResStock 2024.2) dataset do not match what is in the documentation for that release and are not consistent throughout the dataset. The baseline (upgrade 0) results and measure package results where applicability is False are calculated with one set of values, and the results for measure packages where applicability is True are calculated with a different set of values. The energy bill results are calculated using these electricity bill results as an input and are, therefore, also impacted. No other fields are impacted. In particular, the bill results for other utility bills (natural gas, propane, and fuel oil) are unaffected, and the utility bill rate fields (e.g., **in.utility_bill_electricity_marginal_rates**) are unaffected and correctly match the documentation.

The greatest impact is in the electricity and energy bill savings calculations, because they are calculated by taking the difference of values that were themselves calculated using two different sets of electric rates. In some cases, the results are nonsensical: electricity bills may increase even when electricity consumption decreases, which would not be possible using the methodology in the dataset documentation. The relatively few dwelling unit models with annual excess sellback of onsite PV generation in the case of net metering are also greatly impacted.

The total electricity bill and energy bill impacts for any set of dwelling units whose bills were calculated using any one set of rate inputs are less impacted. This could be either a set of baseline dwelling units or a set of dwelling units with a measure package applied and True applicability. The range of values (i.e., difference between minimum and maximum utility bill), trends in terms of where bills are higher or lower and by how much, and other similar statistics are all either unaffected or only minorly impacted.  

## Recommendation
Users are always encouraged to calculate utility bills using location-specific or project-specific utility rates in conjunction with ResStock™ energy consumption outputs, if it is feasible to do so. If it is not feasible to use specific rates, we encourage users to recalculate the utility bills using a consistent set of ResStock-provided utility rates when using the ResStock 2024 Release 2 (ResStock 2024.2) dataset. All three sets of relevant rates, including the set of electric utility rates that was intended to be used in ResStock 2024.2, are in the table below[^2].

When using ResStock results to compare the utility bills for the baseline building stock to the utility bills for the building stock with a measure package applied, it is critical to recalculate the electricity and the energy bills. When calculating utility bill savings for a measure or measure package, the electricity savings[^3] can be multiplied directly by the volumetric electricity rate. The electricity fixed charge ($/dwelling unit/year or $/dwelling unit/month) is not relevant.[^4] Users can then add this calculated electricity bill savings to the ResStock-provided natural gas, propane, and fuel oil bill savings to calculate a total utility bill savings.

When using ResStock electricity or energy bill results for only the baseline or the upgraded (applicability = True) building stock, recalculation of the electricity and energy bill results is optional but encouraged. The electricity bill results should be calculated as:

Electricity_bill [$/year] = Electricity_fixed_charge [$/year] + electricity_net_consumption [kwh] * electricity_volumetric_rate [$/kwh].

<table><thead>
  <tr>
    <th></th>
    <th colspan="3">Electricity Volumetric Rate [$/kWh]</th>
    <th colspan="3"> Electricity Fixed Charge [$/dwelling unit/year]</th>
  </tr></thead>
<tbody>
  <tr>
    <td>State</td>
    <td><a href="https://oedi-data-lake.s3.amazonaws.com/nrel-pds-building-stock/end-use-load-profiles-for-us-building-stock/2024/resstock_tmy3_release_2/resstock_documentation_2024_release_2.pdf" target="_blank" rel="noopener noreferrer">Documentation</a></td>
    <td> <a href="https://github.com/NREL/resstock/blob/eussrr2/resources/data/simple_rates/State.tsv" target="_blank" rel="noopener noreferrer">Baseline, and Upgrades with Applicability = False</a></td>
    <td>Measure Packages where Applicability = True</td>
    <td>Documentation</td>
    <td> Baseline, and Upgrades with Applicability = False</td>
    <td><a href="https://openstudio-hpxml.readthedocs.io/en/latest/workflow_inputs.html#hpxml-utility-bill-scenarios" target="_blank" rel="noopener noreferrer">Measure Packages where Applicability = True</a></td>
  </tr>
  <tr>
    <td>AL</td>
    <td>0.128835397</td>
    <td>0.128835397</td>
    <td>0.134</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>AR</td>
    <td>0.111922976</td>
    <td>0.111922976</td>
    <td>0.108</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>AZ</td>
    <td>0.124597967</td>
    <td>0.124597967</td>
    <td>0.119</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>CA</td>
    <td>0.226679363</td>
    <td>0.226679363</td>
    <td>0.241</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>CO</td>
    <td>0.129536304</td>
    <td>0.129536304</td>
    <td>0.125</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>CT</td>
    <td>0.21792542</td>
    <td>0.21792542</td>
    <td>0.230</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>DC</td>
    <td>0.12969196</td>
    <td>0.12969196</td>
    <td>0.126</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>DE</td>
    <td>0.124282629</td>
    <td>0.124282629</td>
    <td>0.125</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>FL</td>
    <td>0.118232586</td>
    <td>0.118232586</td>
    <td>0.129</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>GA</td>
    <td>0.124291253</td>
    <td>0.124291253</td>
    <td>0.130</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>IA</td>
    <td>0.126296868</td>
    <td>0.126296868</td>
    <td>0.117</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>ID</td>
    <td>0.100697839</td>
    <td>0.100697839</td>
    <td>0.093</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>IL</td>
    <td>0.130608035</td>
    <td>0.130608035</td>
    <td>0.143</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>IN</td>
    <td>0.132857551</td>
    <td>0.132857551</td>
    <td>0.138</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>KS</td>
    <td>0.128880871</td>
    <td>0.128880871</td>
    <td>0.128</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>KY</td>
    <td>0.114262838</td>
    <td>0.114262838</td>
    <td>0.118</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>LA</td>
    <td>0.109522557</td>
    <td>0.109522557</td>
    <td>0.117</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>MA</td>
    <td>0.227501635</td>
    <td>0.227501635</td>
    <td>0.242</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>MD</td>
    <td>0.130352361</td>
    <td>0.130352361</td>
    <td>0.134</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>ME</td>
    <td>0.168769405</td>
    <td>0.168769405</td>
    <td>0.202</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>MI</td>
    <td>0.174115791</td>
    <td>0.174115791</td>
    <td>0.160</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>MN</td>
    <td>0.133928744</td>
    <td>0.133928744</td>
    <td>0.127</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>MO</td>
    <td>0.113347519</td>
    <td>0.113347519</td>
    <td>0.112</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>MS</td>
    <td>0.114840419</td>
    <td>0.114840419</td>
    <td>0.117</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>MT</td>
    <td>0.111271702</td>
    <td>0.111271702</td>
    <td>0.100</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>NC</td>
    <td>0.112440772</td>
    <td>0.112440772</td>
    <td>0.110</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>ND</td>
    <td>0.107682983</td>
    <td>0.107682983</td>
    <td>0.098</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>NE</td>
    <td>0.106677571</td>
    <td>0.106677571</td>
    <td>0.098</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>NH</td>
    <td>0.197202997</td>
    <td>0.197202997</td>
    <td>0.236</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>NJ</td>
    <td>0.162330696</td>
    <td>0.162330696</td>
    <td>0.151</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>NM</td>
    <td>0.133873183</td>
    <td>0.133873183</td>
    <td>0.122</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>NV</td>
    <td>0.114051302</td>
    <td>0.114051302</td>
    <td>0.125</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>NY</td>
    <td>0.193439341</td>
    <td>0.193439341</td>
    <td>0.200</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>OH</td>
    <td>0.126737761</td>
    <td>0.126737761</td>
    <td>0.127</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>OK</td>
    <td>0.109249996</td>
    <td>0.109249996</td>
    <td>0.115</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>OR</td>
    <td>0.112855169</td>
    <td>0.112855169</td>
    <td>0.102</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>PA</td>
    <td>0.136613018</td>
    <td>0.136613018</td>
    <td>0.147</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>RI</td>
    <td>0.221590129</td>
    <td>0.221590129</td>
    <td>0.212</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>SC</td>
    <td>0.127866343</td>
    <td>0.127866343</td>
    <td>0.131</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>SD</td>
    <td>0.121410547</td>
    <td>0.121410547</td>
    <td>0.110</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>TN</td>
    <td>0.109976447</td>
    <td>0.109976447</td>
    <td>0.115</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>TX</td>
    <td>0.120291028</td>
    <td>0.120291028</td>
    <td>0.125</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>UT</td>
    <td>0.103232299</td>
    <td>0.103232299</td>
    <td>0.094</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>VA</td>
    <td>0.118883665</td>
    <td>0.118883665</td>
    <td>0.125</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>VT</td>
    <td>0.191097568</td>
    <td>0.191097568</td>
    <td>0.181</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>WA</td>
    <td>0.100247613</td>
    <td>0.100247613</td>
    <td>0.091</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>WI</td>
    <td>0.1440078</td>
    <td>0.1440078</td>
    <td>0.138</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>WV</td>
    <td>0.120767908</td>
    <td>0.120767908</td>
    <td>0.122</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
  <tr>
    <td>WY</td>
    <td>0.110756249</td>
    <td>0.110756249</td>
    <td>0.098</td>
    <td>120</td>
    <td>10</td>
    <td>144</td>
  </tr>
</tbody></table>

[^1]: Net electricity consumption is total electricity consumption less any on-site generation. Note that cases in which on-site electricity generation exceeds consumption have additional complexities in the calculation of their bills.
[^2]: In the case of annual excess sellback of PV generation, Measure Packages where Applicability is True use the OpenStudio-HPXML default of $0.03/kWh, as described in the PV Compensation [documentation](https://openstudio-hpxml.readthedocs.io/en/v1.7.0/workflow_inputs.html#pv-compensation). 
[^3]: Either net or total, these are the same for every upgrade in ResStock 2024.2.
[^4]: Note this is not true for natural gas, because some ResStock upgrades remove all natural gas consumption and therefore also the natural gas fixed charge.