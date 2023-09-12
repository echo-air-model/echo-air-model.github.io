---
layout: default
title: Environmental Justice Functions
parent: Model Scripts
grand_parent: Code Details
nav_order: 1
---

## `environmental_justice_calcs.py` 
The `environmental_justice_calcs` script file contains a number of functions that help calculate exposure metrics for environmental justice analyses.

### `create_exposure_df`
Creates a dataframe ready for exposure calculations
1. Inputs:
   * `conc`: concentration object from `concentration.py`
   * `isrm_pop_alloc`: population object (from `population.py`) re-allocated to the ISRM grid cell geometry
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
   * `debug_mode`: a Boolean indicating whether or not to output debug statements
2. Outputs
   * `exposure_gdf`: a geodataframe with the exposure concentrations and allocated population by racial group
3. Methodology:
   1. Pulls the total concentration from the concentration object
   2. Grabs the population by racial/ethnic group from the population object
   3. Merges the concentration and population data based on the ISRM ID
   4. Adds the population weighted mean exposure as a column of the geodataframe using `add_pwm_col`

### `add_pwm_col`
Adds an intermediate column that multiplies population by exposure concentration
1. Inputs:
   * `exposure_gdf`: a geodataframe with the exposure concentrations and allocated population by racial group
   * `group`: the racial/ethnic group name
2. Outputs:
   * `exposure_gdf`: a geodataframe with the exposure concentrations and allocated population by racial group, now with PWM column
3. Methodology:
   1. Creates a column called `group`+'_PWM'.
   2. Multiplies exposure concentration by `group` population
   3. Returns the new dataframe
4. Important Notes:
   * The new column is not actually a population-weighted mean, it is just an intermediate for calculating PWM in the next step.

### `get_pwm`
Estimates the population-weighted mean exposure for a given group
1. Inputs:
   * `exposure_gdf`: a geodataframe with the exposure concentrations and allocated population by racial group
   * `group`: the racial/ethnic group name
2. Outputs:
   * `PWM_group`: the group-level population weighted mean exposure concentration (float)
3. Methodology:
   1. Creates a variable for the group PWM column (as created in `add_pwm_col`
   2. Estimates PWM by adding across the `group`_PWM column and dividing by the total `group` population

### `get_overall_disparity`
Returns a table of overall disparity metrics by racial/ethnic group
1. Inputs:
   * `exposure_gdf`: a geodataframe with the exposure concentrations and allocated population by racial group
2. Outputs:
   * `pwm_df`: a dataframe containing the PWM, absolute disparity, and relative disparity of each group
3. Methodology:
   1. Creates an empty dataframe with the groups as rows
   2. Estimates the group population weighted mean using the `get_pwm` function
   3. Estimates the absolute disparity as `Group_PWM` - `Total_PWM`
   4. Estimates the relative disparity as the `Absolute Disparity`/`Total_PWM`

### `estimate_exposure_percentile`
Creates a dataframe of exposure percentiles for plotting
1. Inputs:
   * `exposure_gdf`: a geodataframe with the exposure concentrations and allocated population by racial group
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
2. Outputs:
   * `df_pctl`: a dataframe of exposure concentrations by percentile of population exposed by group
3. Methodology:
   1. Creates a copy of the `exposure_gdf` dataframe to prevent writing over the original.
   2. Sorts the dataframe by PM2.5 concentration and resets the index.
   3. Iterates through each racial/ethnic group, performing the following:
      1. Creates a small slice of the dataframe that is only the exposure concentration and the `group`.
      2. Estimates the cumulative sum of population in the sorted dataframe.
      3. Estimates the total population of the `group`.
      4. Estimates percentile as the population in the grid cell divided by the total population of the `group`.
      5. Adds the percentile column into the main dataframe.

### `run_exposure_calcs`
Calls the other exposure justice functions in order
1. Inputs:
   * `conc`: concentration object from `concentration.py`
   * `isrm_pop_alloc`: population object (from `population.py`) re-allocated to the ISRM grid cell geometry
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
   * `debug_mode`: a Boolean indicating whether or not to output debug statements
2. Outputs:
   * `exposure_gdf`: a dataframe containing the exposure concentrations and population estimates for each group
   * `exposure_pctl`: a dataframe of exposure concentrations by percentile of population exposed by group
   * `exposure_disparity`: a dataframe containing the PWM, absolute disparity, and relative disparity of each group
3. Methodology:
   1. Calls the `create_exposure_df` function.
   2. Calls the `get_overall_disparity` function.
   3. Calls the `estimate_exposure_percentile` function.

### `export_exposure_gdf`
Exports the exposure concentrations and population estimates as a shapefile
1. Inputs: 
   * `exposure_gdf`: a dataframe containing the exposure concentrations and population estimates for each group
   * `shape_out`: a filepath string of the location of the shapefile output directory
   * `f_out`: the name of the file output category (will append additional information)
2. Outputs:
   * A shapefile will be output into the `shape_out` directory.
   * The function returns `fname` as a surrogate for completion (otherwise irrelevant)
3. Methodology:
   1. Creates a filename and path for the export.
   2. Updates the columns slightly for shapefile naming
   3. Exports the shapefile.

### `export_exposure_csv`
Exports the exposure concentrations and population estimates as a CSV file
1. Inputs: 
   * `exposure_gdf`: a dataframe containing the exposure concentrations and population estimates for each group
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information)
2. Outputs:
   * A CSV file will be output into the `output_dir`.
   * The function returns `fname` as a surrogate for completion (otherwise irrelevant)
3. Methodology:
   1. Creates a filename and path for the export.
   2. Updates the column names for more straightforward interpretation
   3. Exports the results as a comma-separated value (CSV) file.

### `export_exposure_disparity`
Exports the exposure concentrations and population estimates as a shapefile
1. Inputs: 
   * `exposure_disparity`: a dataframe containing the population-weighted mean exposure concentrations for each group
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information)
2. Outputs:
   * A shapefile will be output into the `output_dir`.
   * The function returns `fname` as a surrogate for completion (otherwise irrelevant)
3. Methodology:
   1. Creates a filename and path for the export.
   2. Updates the columns and values slightly for more straightforward interpretation
   3. Exports the results as a comma-separated value (CSV) file.

### `plot_percentile_exposure`
Creates a plot of exposure concentration by percentile of each group's population
1. Inputs: 
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information)
   * `exposure_pctl`: a dataframe of exposure concentrations by percentile of population exposed by group
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
   * `debug_mode`: a Boolean indicating whether or not to output debug statements
2. Outputs:
   * The function does not return anything, but a lineplot image (PNG) will be output into the `output_dir`.
3. Methodology:
   1. Creates a melted (un-pivoted) version of the percentiles dataframe.
   2. Multiplies the percentile by 100 to span 0-100 instead of 0-1.
   3. Maps the racial/ethnic group names to better formatted names (e.g., "HISLA" --> "Hispanic/Latino")
   4. Draws the figure using the `seaborn` library's `lineplot` function.
   5. Saves the file as `f_out` + '_PM25_Exposure_Percentiles.png' into the `out_dir`.

### `export_exposure`
Calls each of the exposure output functions in parallel
1. Inputs: 
   * `exposure_gdf`: a dataframe containing the exposure concentrations and population estimates for each group
   * `exposure_disparity`: a dataframe containing the population-weighted mean exposure concentrations for each group
   * `exposure_pctl`: a dataframe of exposure concentrations by percentile of population exposed by group
   * `shape_out`: a filepath string of the location of the shapefile output directory
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information)
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
   * `debug_mode`: a Boolean indicating whether or not to output debug statements
2. Outputs:
   * The function does not return anything, but a shapefile will be output into the `output_dir`.
3. Methodology:
   1. Creates a filename and path for the export.
   2. Updates the columns slightly for shapefile naming
   3. Exports the shapefile.

### `create_rename_dict`
Makes a global rename code dictionary for easier updating
1. Inputs: None
2. Outputs:
   * `logging_code`: a dictionary that maps endpoint names to log statement codes
3. Methodology:
   1. Defines a dictionary and returns it.
