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
   * `population_columns`: a list of population columns to use from the population input file
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
   * `debug_mode`: a Boolean indicating whether or not to output debug statements
   * `dpm`: a Boolean indicating whether or not to include DPM in calculations
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
   * `dpm`: a Boolean indicating whether to add a DPM_PWM column as well
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
   * `dpm`: a Boolean indicating whether or not to estimate PWMs for DPM
2. Outputs:
   * `PWM_group`: the group-level population weighted mean exposure concentration (float)
   * `DPM_PWM_group`: the group-level population weighted mean exposure concentration (float)
3. Methodology:
   1. Creates a variable for the group PWM column (as created in `add_pwm_col`
   2. Estimates PWM by adding across the `group`_PWM column and dividing by the total `group` population

### `get_overall_disparity`
Returns a table of overall disparity metrics by racial/ethnic group
1. Inputs:
   * `exposure_gdf`: a geodataframe with the exposure concentrations and allocated population by racial group
   * `population_columns`: a list of population columns to use from the population input file
   * `dpm`: a Boolean indicating whether or not to include DPM in calculations
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
   * `population_columns`: a list of population columns to use from the population input file
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
   * `dpm`: a Boolean indicating whether or not to calculate percentiles for DPM
2. Outputs:
   * `df_pctl`: a dataframe of exposure concentrations by percentile of population exposed by group and pollutant
3. Methodology:
   1. Iterates through each pollutant
   2. Iterates through each racial/ethnic group, performing the following: 
       1. Creates a copy of the `exposure_gdf` dataframe to prevent writing over the original.
       2. Sorts by pollutant and calculates cumulative percentile
       3. Interpolate to get concentrations at exact percentile steps
   3. Merge all pollutant dataframes on the Percentile column 

### `run_exposure_calcs`
Calls the other exposure justice functions in order
1. Inputs:
   * `conc`: concentration object from `concentration.py`
   * `isrm_pop_alloc`: population object (from `population.py`) re-allocated to the ISRM grid cell geometry
   * `population_columns`: a list of population columns to use from the population input file
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
   * `debug_mode`: a Boolean indicating whether or not to output debug statements
   *  `dpm`: a Boolean indicating whether or not to include DPM calculations
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
   * `population_columns`: a list of population columns to use from the population input file
   * `exposure_gdf`: a dataframe containing the exposure concentrations and population estimates for each group
   * `shape_out`: a filepath string of the location of the shapefile output directory
   * `f_out`: the name of the file output category (will append additional information)
   * `dpm`: a Boolean indicating whether or not to include DPM calculations
3. Outputs:
   * A shapefile will be output into the `shape_out` directory.
   * The function returns `fname` as a surrogate for completion (otherwise irrelevant)
4. Methodology:
   1. Creates a filename and path for the export.
   2. Updates the columns slightly for shapefile naming
   3. Exports the shapefile.

### `export_exposure_csv`
Exports the exposure concentrations and population estimates as a CSV file
1. Inputs:
   * `population_columns`: a list of population columns to use from the population input file
   * `exposure_gdf`: a dataframe containing the exposure concentrations and population estimates for each group
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information)
   *  `dpm`: a Boolean indicating whether or not to include DPM calculations
3. Outputs:
   * A CSV file will be output into the `output_dir`.
   * The function returns `fname` as a surrogate for completion (otherwise irrelevant)
4. Methodology:
   1. Creates a filename and path for the export.
   2. Updates the column names for more straightforward interpretation
   3. Exports the results as a comma-separated value (CSV) file.

### `export_exposure_disparity`
Exports the exposure concentrations and population estimates as a shapefile
1. Inputs: 
   * `exposure_disparity`: a dataframe containing the population-weighted mean exposure concentrations for each group
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information)
   * `dpm`: a Boolean indicating whether or not to include DPM calculations
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
   * `population_columns`: a list of population columns to use from the population input file
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information)
   * `exposure_pctl`: a dataframe of exposure concentrations by percentile of population exposed by group
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
   * `debug_mode`: a Boolean indicating whether or not to output debug statements
   * `dpm`: a Boolean indicating whether or not to include DPM calculations
3. Outputs:
   * The function does not return anything, but a lineplot image (PNG) will be output into the `output_dir`.
4. Methodology:
   1. Creates a melted (un-pivoted) version of the percentiles dataframe.
   2. Multiplies the percentile by 100 to span 0-100 instead of 0-1.
   3. Maps the racial/ethnic group names to better formatted names (e.g., "HISLA" --> "Hispanic/Latino")
   4. Draws the figure using the `seaborn` library's `lineplot` function.
   5. Saves the file as `f_out` + `pollutant` + '_exposure_percentiles.png' into the `out_dir`.

### `export_exposure`
Calls each of the exposure output functions in parallel
1. Inputs:
   * `population_columns`: a list of population columns to use from the population input file
   * `exposure_gdf`: a dataframe containing the exposure concentrations and population estimates for each group
   * `exposure_disparity`: a dataframe containing the population-weighted mean exposure concentrations for each group
   * `exposure_pctl`: a dataframe of exposure concentrations by percentile of population exposed by group
   * `shape_out`: a filepath string of the location of the shapefile output directory
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information)
   * `verbose`: a Boolean indicating whether or not detailed logging statements should be printed
   * `debug_mode`: a Boolean indicating whether or not to output debug statements
   *  `output_png_flag`: a Boolean indicating whether or not to output png files
   *  `dpm`: a Boolean indicating whether or not to include DPM calculation
3. Outputs:
   * The function does not return anything, but a shapefile will be output into the `output_dir`.
4. Methodology:
   1. Creates a filename and path for the export.
   2. Updates the columns slightly for shapefile naming
   3. Exports the shapefile.

### `region_pwm_helper`
Estimates population-weighted mean for a subset of the full_dataset.
1. Inputs: None
   * `name`: the specific name of the region type (e.g., SF BAY AREA)
   * `group`: the racial/ethnic group of interest
   * `full_dataset`: a dataframe containing all of the concentraion and population intersection objects with regions assigned
   * `conc_col`: name of the column that the PWM should be calculated for
2. Outputs:
   * `pwm`: the population-weighted mean concentration of the given concentration column
3. Methodology:
   1. Slices a releevant part of the full dataset using the `NAME` column.
   2. Estimates the population-weighted mean for that geographic area only.

### `export_pwm_map`
Creates the exports for the population-weighted products requested when the user inputs an output resolution larger than the ISRM grid
1. Inputs:
   * `population_columns`: a list of population columns to use from the population input file
   * `pop_exp`: a dataframe containing the population information without age-resolution
   * `conc`: a concentration object
   * `output_dir`: a filepath string of the location of the output directory
   * `output_region`: the geometry of the desired output region
   * `f_out`: the name of the file output category (will append additional information)
   * `ca_shp_path`: a filepath string of the location of the California boundary shapefile
   * `shape_out`: a filepath string of the location of the shapefile output directory
   * `dpm`: a Boolean indicating whether or not to include dpm
3. Outputs: None
4. Methodology:
   1. Combines the concentration data, geographic areas data, and the population data by intersecting all three together.
   2. Estimates the population counts for each group in each of these intersected areas.
   3. Estimates the population-weighted mean concentration for each group for each geographic subarea.
   4. Plots this data on a chloropleth map using the `visualize_pwm_conc` function.
   5. Outputs this summary data as a shapefile and as a csv.

### `visualize_pwm_conc`
Creates map of PWM concentrations using simple chloropleth.
1. Inputs: 
   * `output_res_geo`: a dataframe containing the population-weighted mean concentrations for each output resolution
   * `output_region`: the geometry of the desired output region
   * `output_dir`: a filepath string of the location of the output directory
   * `f_out`: the name of the file output category (will append additional information)
   * `ca_shp_path`: a filepath string of the location of the California boundary shapefile
   * `pol_label`: the name of the pollutant
   * `data_col`: the specific column name to plot
2. Outputs: None
3. Methodology:
   1. Reads in the California boundary file and projects it to the matching coordinate reference system.
   2. Creates a matching map to the one created in `concentration.visualize_concentrations()`.

### `rename_for_shapefile`
Makes sure all columns are less than 10 characters in length, if not, truncates them or renames them
1. Inputs:
   * `df`: the dataframe object
2. Outputs:
   * `df`: the dataframe object with columns names less than 10
