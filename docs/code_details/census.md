---
layout: default
title: Census
parent: Supporting Code Objects
grand_parent: Code Details
nav_order: 3
---

## `census.py`
The `census` object is used to process census data from IPUMS and output population data in the form of a feather file.

### Inputs
* `codebook_fp`: the file path of the codebook data
* `tractdata_fp`: the file path of the tract data
* `ipums_shp_fp`: the file path of the shapefile data
* `output_dir`: a string pointing to the output directory
* `f_out`: a string containing the filename pattern to be used in output files
* `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
* `debug_mode`: a Boolean indicating whether or not to output debug statements

### Attributes
* `codebook_fp`: the file path of the codebook data
* `tractdata_fp`: the file path of the tract data
* `ipums_shp_fp`: the file path of the shapefile data
* `output_dir`: the output directory
* `f_out`: the filename pattern for output files
* `verbose`: a Boolean indicating whether detailed logging statements should be printed
* `debug_mode`: a Boolean indicating whether to output debug statements
* `codebook`: a dictionary mapping column headers to their descriptions
* `tract_data`: pandas DataFrame containing tract data
* `census_geo`: geopandas GeoDataFrame containing shapefile data

### Internal Functions
* `load_codebook`: loads the codebook file and parses it into a dictionary
* `process_codebook`: processes the loaded codebook to create a combined codebook with race codes
* `split_description`: splits the description based on ':' or '>>'. this is necessary since census data differs in different years, and sometimes is split with >> or :. 
* `preprocess_data`: preprocesses the census data by filtering, melting, mapping age bins, and merging with geographic data
* `get_start_age`: helper function to get the start age from the age bin
* `get_end_age`: helper function to get the end age from the age bin
