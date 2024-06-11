---
layout: default
title: Tool Utilities
parent: Model Scripts
grand_parent: Code Details
nav_order: 3
---

## `tool_utils.py` 
The `tool_utils` library contains a handful of scripts that are useful for code execution.

### `check_setup`
Checks that the isrm_health_calculations local clone is set up properly
1. Inputs: None
2. Outputs:
   * `valid_setup`: a Boolean indicating if the setup is valid or 
3. Methodology:
   1. Gets the programs current working directory.
   2. Checks that all the script and supporting files exist where they are supposed to.
   3. Checks that all key data files are saved where they should (not including ISRM)
   4. Checks that the CA_ISRM is located in the data folder with all necessary objects, but does not consider this an improper setup, as the user may have their own ISRM.
   5. Reports any missing files or directories.

### `setup_logging`
Sets up the log file capability using the `logging` library
1. Inputs:
   * `debug_mode`: a Boolean indicating if log statements should be returned in debug mode or not
2. Outputs:
   * `tmp_logger`: a filepath string associated with a temporary log file that will be moved as soon as the output directory is created
3. Methodology:
   1. Defines useful variables for the `logging` library.
   2. Creates a temporary log file path (`tmp_logger`) that allows the file to be created before the output directory.
   3. Suppresses all other library warnings and information.
   4. Sets the formatting system for log statements.

### `verboseprint`
Sets up the verbose printing mechanism for global usage
1. Inputs:
   * `verbose`: a Boolean indicating if it is in verbose mode or not
   * `text`: a string to be returned if the program is in verbose mode
   * `debug_mode`: a Boolean indicating whether or not to output debug statements
   * `frameinfo`: inspect object that provides information about the line making the function call
2. Outputs: None
3. Methodology:
   1. Checks if verbose is True.
   2. If True:
      1. Checks for debug mode. If it is running in debug, it will add the script name and line number that made the function call to `verboseprint` to the log statement text.
      2. Creates a log statement.
   3. If False, does nothing. 

### `report_version` 
Reports the current working version of the tool
1. Inputs: None
2. Outputs: None
3. Methodology: adds statements to the log file about the tool version

### `create_output_dir`
Creates the output directory for saving files
1. Inputs:
   * `batch`: the batch name 
   * `name`: the run name
2. Outputs:
   * `output_dir`: a filepath string for the output directory
   * `f_out`: a string containing the filename pattern to be used in output files
3. Methodology:
   1. Grabs the current working directory of the tool and defines 'outputs' as the sub-directory to use.
   2. Checks to see if the directory already exists. If it does exists, automatically increments by 1 to create a unique directory.
   3. Creates `f_out` by removing the 'out' before the `output_dir`.
   4. Creates the output directory.

### `create_shape_out`
Creates the output directory for saving shapefiles
1. Inputs:
   * `output_dir`: a filepath string for the output directory
2. Outputs:
   * `shape_out`: a filepath string for the shapefile output directory
3. Methodology:
   1. Creates a directory within the `output_dir` called 'shapes'.
   2. Stores this name as `shape_out`.

### `get_output_region`
Creates the output region geodataframe
1. Inputs:
   * `region_of_interest`:  the name of the region to be contained in the `output_region`
   * `region_category`: a string containing the region category for the output region, must be one of 'AB','AD', or 'C' for Air Basins, Air Districts, and Counties
   * `output_geometry_fps`: a dictionary containing a mapping between `region_category` and the filepaths
   * `ca_fps`: a filepath string containing the link to the California border shapefile
2. Outputs
   * `output_region`: a geodataframe containing only the region of interest
3. Methodology:
   1. Checks if the `region_of_interest` is California, in which case, it just reads in the California shapefile.
   2. If California is not the `region_of_interest`:
      1. Gets the filepath of the output region based on the `region_category` from the `output_geometry_fps` dictionary.
      2. Reads in the file as a geodataframe.
      3. Clips the geodataframe to the `region_of_interest`.

### `calculate_true_north_angle`
Calculates the angle between the positive y-axis and true north.
1. Inputs:
* `center_lon`: Longitude of the center point of the map.
* `center_lat`: Latitude of the center point of the map.
* `crs`: The coordinate reference system of the map.
2. Outputs:
* `angle`: The angle in degrees.
3. Methodology:
  1. Creates a transformer to convert from WGS84 to the given CRS.
  2. Transforms the center point and a point slightly north.
  3. Calculates the angle between these points to determine the direction of true north.

### `add_north_arrow`
Adds a simple north arrow to the plot with a specified rotation angle.
1. Inputs:
* `ax`: The axis to add the north arrow to.
* `angle`: The angle to rotate the north arrow.
* `x`: The x-coordinate of the arrow's tip (in axis coordinates).
* `y`: The y-coordinate of the arrow's tip (in axis coordinates).
* `arrow_length`: The length of the arrow.
2. Outputs:
* None
3. Methodology:
  1. Ensures the angle is a float.
  2. Creates a rotation transformation.
  3. Defines coordinates for the arrow.
  4. Adds the arrow and 'N' annotation to the plot.
