---
layout: default
title: ISRM
parent: Supporting Code Objects
grand_parent: Code Details
nav_order: 6
---

## `isrm.py` 
The `isrm` object loads, stores, and manipulates the ISRM grid data. 

### Inputs
* `isrm_path`: a string representing the folder containing all ISRM data
* `output_region`: a geodataframe of the region for results to be output, as calculated by `get_output_region` in `tool_utils.py`
* `region_of_interest`: the name of the region contained in the `output_region`
* `load_file`: a Boolean indicating whether or not the file should be loaded (for debugging)
* `verbose`: a Boolean indicating whether or not detailed logging statements should be printed

### Attributes
* `nh3_path`, `nox_path`, `pm25_path`, `sox_path`, `voc_path`: the filepath strings for each of the primary pollutant ISRM variables
* `valid_file`: a Boolean indicating whether or not the file provided is valid
* `valid_geo_file`: a Boolean indicating whether the ISRM geometry file provided is valid
* `geodata`: a geodataframe containing the ISRM feather file information
* `crs`: the inherent coordinate reference system associated with the ISRM geometry
* `geometry`: geospatial information associated with the ISRM geometry

### Calculated Attributes
* `receptor_IDs`: the IDs associated with ISRM receptors within the `output_region`
* `receptor_geometry`: the geospatial information associated with the ISRM receptors within the `output_region`
* `PM25`, `NH3`, `NOx`, `SOX`, `VOC`: the ISRM matrices for each of the primary pollutants

### Internal Functions
* `get_isrm_files`: appends the file names to the isrm_path input to generate full file paths
* `check_path`: checks if the files exist at the paths specified (both data and geo files)
* `load_and_cut`: loads the numpy layers for a pollutant and trims the columns of each vertical layer's matrix to only include the `receptor_IDs` within the `output_region`
* `load_isrm`: calls the `load_and_cut` function for each ISRM numeric layer and returns a list of pollutant matrices
* `load_geodata`: loads the feather file into a geopandas dataframe
* `clip_isrm`: clips the ISRM receptor geodata to only the relevant ones based on the `output_region` (i.e., returns the `receptor_IDs` and `receptor_geometry` objects)

### External Functions
* `get_pollutant_layer`: returns the ISRM matrix for a single pollutant
* `map_isrm`: simple function for mapping the ISRM grid cells
