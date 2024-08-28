---
layout: default
title: Control File
parent: Input Files
grand_parent: File Specifications
nav_order: 5
---
## Aggregated Health Output Files
When the model is run with RUN_HEALTH and the OUTPUT_RESOLUTION is larger than the ISRM level, additional 
aggregated health plots are also outputted for all cause, ischemic heart disease, and lung
cancer. The png plots developed for each endpoint are in the format: 
[batch]_[run]total[endpoint]_excess_mortality_aggregated.png. are each aggregated to the output 
resolution specified (C, AB, or AD). These plots are outputted in addition to the original pngs, 
as explained in [Health Output Files](https://github.com/echo-air-model/echo-air-model.github.io/new/output_file_pages/docs/file_specifications/output_file_specifications)

