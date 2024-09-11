---
layout: default
title: Aggregated Output Files
parent: Output Files
grand_parent: File Specifications
nav_order: 5
---
## Aggregated Output Files
When the user selects an `OUTPUT_RESOLUTION` larger than the ISRM level, some of the output files previously discussed are slightly different.

For the concentration module, there are two concentration maps instead of one. The two concentration maps display average exposure concentrations (1) spatially and (2) population-weighted. 

For the health module, additional aggregated health plots are also outputted for all cause, ischemic heart disease, and lung cancer. The png plots developed for each endpoint are in the format: [batch]_[run]total[endpoint]_excess_mortality_aggregated.png. are each aggregated to the output resolution specified (C, AB, or AD). These plots are outputted in addition to the original pngs, as explained in [Health Output Files](https://github.com/echo-air-model/echo-air-model.github.io/main/docs/file_specifications/output_file_specifications)

