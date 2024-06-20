---
layout: default
title: Control File
parent: Supporting Code Objects
grand_parent: Code Details
nav_order: 3
---

## `pop_control_file.py`
The `pop_control_file` object is used to check and read the control file for a run:

### Inputs
* `file_path`: the file path of the control file

### Attributes
* `file_path`: the path to the control file
* `output_file_name`: a string representing the name of the output file
* `codebook_fp`: a string representing the path to the codebook file
* `tractdata_fp`: a string representing the path to the tract data file
* `ipums_shp_fp`: a string representing the path to the IPUMS shapefile
* `verbose`: a Boolean indicating whether the user wants to run in verbose mode

### Internal Functions
* `get_input_value`: gets the input for a given keyword
* `get_all_inputs`: imports all values from the control file
