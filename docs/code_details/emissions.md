---
layout: default
title: Emissions
parent: Supporting Code Objects
grand_parent: Code Details
nav_order: 4
---

## `emissions.py`
The `emissions` object is primarily built off of `geopandas`. It has the following attributes:

### Inputs
* `file_path`: the file path of the raw emissions data
* `output_dir`: a filepath string for the output directory
* `f_out`: a string containing the filename pattern to be used in output files
* `units`: units associated with the emissions (e.g., μg/s)
* `name`: a plain English name tied to the emissions data, either provided or automatically generated from the filepath
* `details_to_keep`: any additional details to be preserved throughout the processing (e.g., sector, fuel type) (not fully built out yet)
* `filter_dict`: filters the emissions inputs based on inputted dictionary 
* `emis_delta`: the dictionary containing emissions change
* `emis_change_only`: a Boolean indicating whehter or not the emissions object is solely the emissions change
* `boundary_change`: a shapefile containing the boundary for where emissions would be adjusted
* `load_file`: a Boolean indicating whether or not the file should be loaded (for debugging)
* `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
* `debug_mode`: a Boolean indicating whether or not to output debug statements

### Attributes
* `valid_file`: a Boolean indicating whether or not the file provided is valid
* `valid_units`: a Boolean indicating whether or not emissions units are compatible with the program
* `valid_emissions`: a Boolean indicating whether or not emissions passed required tests
* `file_type`: the type of file being used to provide raw emissions data (for now, only `.shp` is allowed)
* `geometry`: geospatial information associated with the emissions input
* `crs`: the inherent coordinate reference system associated with the emissions input
* `emissions_data`: complete, detailed emissions data from the source
* `emissions_data_clean`: simplified emissions in each grid cell

### Calculated Attributes
* `PM25`: primary PM<sub>2.5</sub> emissions in each grid cell
* `NH3`: ammonia emissions in each grid cell
* `VOC`: VOC compound emissions in each grid cell
* `NOX`: NOx emissions in each grid cell
* `SOX`: SOx emissions in each grid cell
* `L0_flag`, `L1_flag`, `L2_flag`, `isrm_hole_flag`: Booleans indicating whether each layer should be calculated based on emissions release heights

### Internal Functions
* `get_file_path`: returns the file path
* `get_name`: returns the name associated with the emissions (`emissions_name`)
* `get_unit_conversions`: returns two dictionaries of built-in unit conversions
* `check_path`: uses the `path` library to check if the provided `file_path` exists and if the file is a file
* `check_units`: checks that the provided units are valid against the `get_unit_conversions` dictionaries
* `load_emissions`: detects the filetype of the emissions file and calls the appropriate load function
* `check_id`: checks for I_CELL and J_CELL and adds them if they are missing
* `load_shp`: loads the emissions data from a shapefile
* `load_feather`: loads the emissions data from a feather file
* `load_csv`: loads the emissions data from a csv file
* `check_height`: checks that the height column is present in the emissions file; if not, assumes emissions are released at ground-level
* `check_emissions`: runs a number of checks on the emissions data to ensure data are valid before running anything
* `map_pollutant_names`: replaces pollutant names if they are not found in the emissions data based on near-misses (e.g., PM2.5 for PM25)
* `filter_emissions`: filters the emissions based on the `filter_dict` input
* `check_geo_types`: checks what geometries are present in the emissions shapefile (e.g., points, polygons, multipolygons); if points exist, uses `buffer_emis` to convert to polygons
* `check_polygon_area`: checks if the maximum polygon area exceeds 2500 km^2 and outputs a warning to the user if so
* `buffer_emis` converts points to polygons by adding a buffer of `dist`
* `clean_up`: simplifies the emissions data by removing unnecessary dimensions, converting units as appropriate, and updating the column names
* `convert_units`: converts units from provided units to μg/s using the unit dictionaries built-in
* `split_polutants`: converts the emissions layer into separate objects for each pollutant
* `which_layers`: determines the `L0_flag`, `L1_flag`, `L2_flag`, and `linear_interp_flag` variables based on the HEIGHT column of the emissions data
* `change_percentages`: changes emissions by x% for a given pollutant given the the EMISSIONS_CHANGE input

### External Functions
* `visualize_emissions`: creates a simple map of emissions for a provided pollutant
* `get_pollutant_layer`: pulls a single pollutant layer based on `pol_name`

