---
layout: default
title: Acknowledgments
nav_order: 1
---

## Creating Population Files
`create_population_files.py` serves as the counterpart to `run_echo_air.py` specifically designed for generating population files. A dedicated population control file is essential for this process, which you can create by either duplicating `pop_control_file_template.txt` located in the templates directory. 

The population data inputs are available from the [IPUMS National Historical Geographic Information System (NHGIS)](https://www.nhgis.org/), which provides comprehensive census and survey data. To access these files, click on Get Data, apply the necessary filters, select the source tables, time series tables, and GIS files, and then submit your request. If you do not already have an account, you will need to create one. Once submitted, you should receive an email with the download links. While the scripts for creating population files are still under development, they have been successfully tested with the 2000 and 2010 Summary Files (SF1). In the future, we hope to expand these scripts to accommodate all types of files from various years.

For detailed instructions on completing the population control file, please consult the [Population Control File Specifications](https://echo-air-model.github.io/docs/file_specifications/input_file_specifications/pop_control_file_input.html).

Once you have filled out the population control file, it can be utilized to execute create_population_files.py. For further guidance on using this script, please refer to [Create Population Files](https://echo-air-model.github.io/docs/code_details/create_population_files.html).

Aside from creating population files, the `create_population_files.py` and `pop_control_file.py` files are unused. During normal ECHO-AIR runs, the main control file should be used. 
