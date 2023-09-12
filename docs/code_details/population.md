---
layout: default
title: Population
parent: Supporting Code Objects
grand_parent: Code Details
nav_order: 7
---

## `population.py` 
The `population` object stores detailed Census tract-level population data for the environmental justice exposure calculations and the health impact calculations from an input population dataset.

### Inputs
* `file_path`: the file path of the raw population data
* `load_file`: a Boolean indicating whether or not the file should be loaded (for debugging)
* `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
* `debug_mode`: a Boolean indicating whether or not to output debug statements

### Attributes
* `valid_file`: a Boolean indicating whether or not the file provided is valid
* `geometry`: geospatial information associated with the emissions input
* `pop_all`: complete, detailed population data from the source
* `pop_geo`: a geodataframe with population IDs and spatial information
* `crs`: the inherent coordinate reference system associated with the emissions input
* `pop_exp`: a geodataframe containing the population information with associated spatial information, summarized across age bins
* `pop_hia`: a geodataframe containing the population information with associated spatial information, broken out by age bin

### Internal Functions
* `check_path`: checks to see if the file exists at the path specified and returns whether the file is valid
* `load_population`: loads the population data based on the file extension
* `load_shp`: loads the population shapefile data using geopandas and post-processes
* `load_feather`: loads the population feather data using geopandas and post-processes
* `make_pop_exp`: makes the exposure population data frame by summing across age bins
* `make_pop_hia`: makes the health impact assessment population data frame by retaining key information

### External Functions
* `project_pop`: projects the population data to a new coordinate reference system
* `allocate_population`: reallocates population into new geometry using a spatial intersect
