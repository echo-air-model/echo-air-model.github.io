---
layout: default
title: Health Data
parent: Supporting Code Objects
grand_parent: Code Details
nav_order: 5
---

## `health_data.py` 
The `health_data` object stores and manipulates built-in health data (population and incidence rates) from BenMAP. It inputs a dictionary of filepaths and two Boolean run options (`verbose` and `race_stratified`) to return dataframes of population, incidence, and combined population-incidence information (`pop_inc`).

### Inputs
* `pop_alloc`: a geodataframe of population allocated to the ISRM grid geometry
* `incidence_fp`: a string containing the file path to the background incidence dataset
* `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
* `race_stratified`: a Boolean indicating whether race-stratified incidence rates should be used
* `debug_mode`: a Boolean indicating whether or not to output debug statements
  
### Calculated Attributes
* `population`: a geodataframe containing the population allocated to the ISRM grid geometry
* `incidence`: a geodataframe containing the raw incidence data from BenMAP
* `pop_inc`: a geodataframe containing the combined population and incidence data based on the requested geographies

### Internal Functions
* `load_data`: reads in the population and incidence data from feather files
* `update_pop`: updates the population dataset by melting (unpivot) and renaming columns
* `update_inc`: updates the incidence dataset by pivoting columns around endpoints and renaming columns
* `get_incidence_lookup`: creates a small incidence lookup table based on the name and age ranges
* `get_incidence_pop`: helper function that returns the incidence for a given name, race, age range, and endpoint
* `make_incidence_lookup`: creates a lookup dictionary using the `get_incidence_pop` function for each endpoint
* `incidence_by_age`: creates a smaller incidence table for merging by calling `get_incidence_lookup` for each endpoint
* `combine_pop_inc`: creates the `pop_inc` dataframe by doing a spatial merge on the population and incidence data and then using lookup tables to determine the appropriate values
