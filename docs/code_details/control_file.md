---
layout: default
title: Control File
parent: Supporting Code Objects
grand_parent: Code Details
nav_order: 3
---

## `control_file.py`
The `control_file` object is used to check and read the control file for a run:

### Inputs
* `file_path`: the file path of the control file

### Attributes
* `valid_file`: a Boolean indicating whether or not the control file path is valid
* `keywords`: a hardcoded list of the keywords that should be present in the control file
* `blanks_okay`: a hardcoded list of whether each keyword can be blank (based on order of `keywords`)
* `valid_structure`, `no_incorrect_blanks`: Boolean keywords based on internal checks of the control file format
* `run_name`: a string representing the run name preferred by the user
* `emissions_path`: a string representing the path to the emissions input file
* `emissions_units`: a string representing the units of the emissions data
* `isrm_path`: a string representing the path of the folder storing ISRM numpy layers and geodata
* `population_path`: a string representing the path to the population input file
* `check`: a Boolean indicating whether the program should run, or if it should just check the inputs (useful for debugging)
* `population_path`: a string representing the path to the population data file
* `verbose`: a Boolean indicating whether the user wants to run in verbose mode
* `output_exposure`: a Boolean indicating whether exposure should be output
* `detailed_conc`: a Boolean indicating whether concentrations should should be output as totals or by pollutant

### Internal Functions
* `check_path`: checks if a file exists at the given control file path
* `get_input_value`: gets the input for a given keyword
* `check_control_file`: runs all of the internal checks to confirm the control file is valid
* `get_all_inputs`: imports all values from the control file
* `get_region_dict`: loads all of the acceptable values for the various regions
* `region_check_helper`: a helper function for checking the region of interest and region category inputs
* `out_res_check_helper`: a helper function for checking the output resolution input
* `check_inputs`: checks that all inputs are valid once imported

### External Functions
* `get_file_path`: returns the file path

