---
layout: default
title: Health Calculation Functions
parent: Model Scripts
grand_parent: Code Details
nav_order: 2
---

## `health_impact_calcs.py` 
The `health_impact_calcs` script file contains a number of functions that help calculate health impacts from exposure concentrations.

###`create_hia_inputs`
Creates the hia_inputs object.
1. Inputs:
   * `pop`: population object input
   * `load_file`: a Boolean telling the program to load or not
   * `verbose`: a Boolean telling the program to return additional log statements or not
   * `geodata`: the geographic data from the ISRM
   * `incidence_fp`: a string containing the filepath where the incidence data is stored
2. Outputs:
   * a health data object ready for health calculations
3. Methodology
   1. Allocates population to the ISRM grid using the population object and the ISRM geodata.
   2. Initializes a health_data object from that allocated population.

### `krewski`
Defines a Python function around the Krewski et al. (2009) function and endpoints
1. Inputs:
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
   * `conc`: a float with the exposure concentration for a given geography
   * `inc`: a float with the background incidence for a given group in a given geography
   * `pop`: a float with the population estimate for a given group in a given geography
   * `endpoint`: a string containing either 'ALL CAUSE', 'ISCHEMIC HEART DISEASE', or 'LUNG CANCER'
2. Outputs
   * a float estimating the number of excess mortalities for the `endpoint` across the group in a given geography
3. Methodology:
   1. Based on the `endpoint`, grabs a `beta` parameter from Krewski et al. (2009).
   2. Estimates excess mortality using the following equation, where $\beta$ is the endpoint parameter from Krewski et al. (2009), $d$ is the disease endpoint, $C$ is the concentration of PM<sub>2.5</sub>, $i$ is the grid cell, $I$ is the baseline incidence, $g$ is the group, and $P$ is the population estimate.

   $$ 1 - ( \frac{1}{\exp(\beta_{d} \times C_{i})} ) \times I_{i,d,g} \times P_{i,g} $$

### `create_logging_code`
Makes a global logging code for easier updating
1. Inputs: None
2. Outputs:
   * `logging_code`: a dictionary that maps endpoint names to log statement codes
3. Methodology:
   1. Defines a dictionary and returns it.
  
### `calculate_excess_mortality`
Estimates excess mortality for a given `endpoint` and `function`
1. Inputs:
   * `conc`: a float with the exposure concentration for a given geography
   * `health_data_obj`: a `health_data` object as defined in the `health_data.py` supporting script
   * `endpoint`: a string containing either 'ALL CAUSE', 'ISCHEMIC HEART DISEASE', or 'LUNG CANCER'
   * `function`: the health impact function of choice (currently only `krewski` is built out)
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
2. Outputs
   * `pop_inc_conc`: a dataframe containing excess mortality for the `endpoint` using the `function` provided
3. Methodology:
   1. Creates clean, simplified copies of the `detailed_conc` method of the `conc` object and the `pop_inc` method of the `health_data_obj`.
   2. Merges these two dataframes on the ISRM_ID field.
   3. Estimates excess mortality on a row-by-row basis using the `function`.
   4. Pivots the dataframe to get the individual races as columns.
   5. Adds the geometry back in to make it geodata.
   6. Updates the column names such that the excess mortality columns are ENDPOINT_GROUP.
   7. Merges the population back into the dataframe.
   8. Cleans up the dataframe.
 
### `plot_total_mortality`
Creates a map image (PNG) of the excess mortality associated with an `endpoint` for a given `group`.
1. Inputs:
   * `hia_df`: a dataframe containing excess mortality for the `endpoint` using the `function` provided
   * `ca_shp_fp`: a filepath string of the California state boundary shapefile
   * `group`: the racial/ethnic group name
   * `endpoint`: a string containing either 'ALL CAUSE', 'ISCHEMIC HEART DISEASE', or 'LUNG CANCER'
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information) 
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
2. Outputs
   * `fname`: a string filename made by combining the `f_out` with the `group` and `endpoint`.
3. Methodology:
   1. Sets a few formatting standards within `seaborn` and `matplotlib.pyplot`.
   2. Creates the output file directory and name string using `f_out`, `group`, and `endpoint`.
   3. Reads in the California boundary and projects the `hia_df` to match the coordinate reference system of the California dataset.
   4. Clips the dataframe to the California boundary.
   5. Adds area-normalized columns to the `hia_df` for more intuitive plotting.
   6. Grabs the minimums and sets them to 10<sup>-9</sup> in order to avoid logarithm conversion errors.
   7. Updates the 'MORT_OVER_POP' column to avoid 100% mortality that arises from the update in step 6.
   8. Initializes the figure and plots four panes:
      1. Population density: plots the area-normalized population estimates for the group on a log-normal scale.
      2. PM<sub>2.5</sub> exposure concentrations: plots the exposure concentration on a log-normal scale.
      3. Excess mortality per area: plots the excess mortality per unit area on a log-normal scale.
      4. Excess mortality per population: plots the excess mortality per population for the group on a log-normal scale.
   9. Performs a bit of clean-up and formatting before exporting.
  
### `export_health_impacts`
Exports mortality as a shapefile
1. Inputs:
   * `hia_df`: a dataframe containing excess mortality for the `endpoint` using the `function` provided
   * `group`: the racial/ethnic group name
   * `endpoint`: a string containing either 'ALL CAUSE', 'ISCHEMIC HEART DISEASE', or 'LUNG CANCER'
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information) 
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
2. Outputs
   * `fname`: a string filename made by combining the `f_out` with the `group` and `endpoint`.
3. Methodology:
   1. Creates the output file path (`fname`) using inputs.
   2. Creates endpoint short labels and updates column names since shapefiles can only have ten characters in column names.
   3. Exports the geodataframe to shapefile.

### `export_health_impacts_csv`
Exports mortality as a csv
1. Inputs:
   * `hia_df`: a dataframe containing excess mortality for the `endpoint` using the `function` provided
   * `endpoint`: a string containing either 'ALL CAUSE', 'ISCHEMIC HEART DISEASE', or 'LUNG CANCER'
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information) 
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
2. Outputs
   * `fname`: a string filename made by combining the `f_out` with the `group` and `endpoint`.
3. Methodology:
   1. Creates the output file path (`fname`) using inputs.
   2. Revises column names for clarity
   3. Exports the geodataframe to csv.

### `create_summary_hia`
Creates a summary table of health impacts by racial/ethnic group
1. Inputs:
   * `hia_df`: a dataframe containing excess mortality for the `endpoint` using the `function` provided
   * `endpoint`: a string containing either 'ALL CAUSE', 'ISCHEMIC HEART DISEASE', or 'LUNG CANCER'
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
   * `l`: an intermediate string that has the endpoint label string (e.g., ACM_)
   * `endpoint_nice`: an intermediate string that has a nicely formatted version of the endpoint (e.g., All Cause) 
2. Outputs
   * `hia_summary`: a summary dataframe containing population, excess mortality, and excess mortality rate per demographic group
3. Methodology:
   1. Cleans up the hia_df by changing column names and splitting population and mortality
   2. Gets total population and mortality by group
   3. Combines into one dataframe and cleans it up for export

### `visualize_and_export_hia`
Calls `plot_total_mortality` and `export_health_impacts` in one clean function call.
1. Inputs:
   * `hia_df`: a dataframe containing excess mortality for the `endpoint` using the `function` provided
   * `ca_shp_fp`: a filepath string of the California state boundary shapefile
   * `group`: the racial/ethnic group name
   * `endpoint`: a string containing either 'ALL CAUSE', 'ISCHEMIC HEART DISEASE', or 'LUNG CANCER'
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information) 
   * `shape_out`: a filepath string for shapefiles
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
2. Outputs
   * `hia_summary`: a summary dataframe containing population, excess mortality, and excess mortality rate per demographic group
3. Methodology:
   1. Calls `plot_total_mortality`.
   2. Calls `export_health_impacts.

### `combine_hia_summaries`
Combines the three endpoint summary tables into one export file
1. Inputs:
   * `acm_summary`: a summary dataframe containing population, excess all-cause mortality, and all-cause mortality rates
   * `ihd_summary`: a summary dataframe containing population, excess IHD mortality, and IHD mortality rates 
   * `lcm_summary`: a summary dataframe containing population, excess lung cancer mortality, and lung cancer mortality rates
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information) 
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed 
2. Outputs: None
3. Methodology:
   1. Merges the summary dataframes together
   2. Removes excess columns
   3. Saves as CSV file

### `create_rename_dict`
Makes a global rename code dictionary for easier updating
1. Inputs: None
2. Outputs:
   * `logging_code`: a dictionary that maps endpoint names to log statement codes
3. Methodology:
   1. Defines a dictionary and returns it.