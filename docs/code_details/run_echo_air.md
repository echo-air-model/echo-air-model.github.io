---
layout: default
title: run_echo_air.py
parent: Code Details
nav_order: 1
---

## `run_echo_air.py`
The `run_echo_air.py` script is the main script file that drives the model. This script operates the command line functionality, defines the health impact calculation objects, calls each of the supporting functions, and outputs the desired files. The `run_echo_air.py` script is not split into functions or objects, instead, it is run through two sections: (1) Initialization and (2) Run Program.

### Initialization
In the initialization section of `run_echo_air.py`, the parser object is created in order to interface with the command line. The parser object is created using the `argparse` library. 

Currently, the only arguments accepted by the parser object are `-i` for input file, `-h` for help, and `--check-setup` to run a setup check. 

Once the parser is defined, the control file object is created using `control_file.py` class object. A number of metadata variables are defined from the control file. 

Next, a number of internally saved data file paths are saved.

Finally, the output_region is defined based on the `get_output_region` function defined in `tool_utils.py`. The output region is then stored for use in later functions.

### Run Program
The run program section of the code is split into two modes. If the CHECK_INPUTS flag is given, the tool will run in check mode, where it will check that each of the inputs is valid and then quit. If the CHECK_INPUTS flag is not given, the tool will run the full program. 

It will start by creating a log file using the `setup_logging` function. Once the logging is set up, an output directory is created using the `create_output_dir` function from `tool_utils.py`. It will also create a shapefile subdirectory within the output folder directory using `create_shape_out`. The tool will also create an `output_region` geodataframe from user inputs for use in future steps.

Then, the model will begin the concentration module. This starts by defining an emissions object and an isrm object using the `emissions.py` and `isrm.py` supporting class objects. The concentrations will be estimated using the `concentration.py` object, which relies on the `concentration_layer.py` object. The concentrations will then be output as a map of total exposure concentration and a shapefile with detailed exposure information. If emissions changes are enabled, two emissions objects with respective concentrations are created, one with changes in emissions and another showing the current emissions with the changes applied, creating two sets of data. The set of data with the change in emissions by itself is labeled with `emis_change_only` before each output. 

Next, the model will run environmental justice exposure calculations using the `create_exposure_df`, `get_overall_disparity`, and `estimate_exposure_percentile` functions from the `environmental_justice_calcs.py` file. The exposure percentiles will then be plotted and exported using the `plot_percentile_exposure` function. If the control file has indicated that exposure data should be output (using the 'OUTPUT_EXPOSURE' flag), a shapefile of exposure concentrations by population group will be output in the output directory.

Finally, if indicated by the user, the model will begin the health module. It will create the health input object using the `health_data.py` library and then estimate the three endpoints of excess mortality using `calculate_excess_mortality` from the `health_impact_calcs` file. Each endpoint will then be mapped and exported using `visualize_and_export_hia`.

If enabled, the model utilizes parallel computing to increase efficiency and reduce runtime. As such, many of these steps do not happen exactly in the order presented above. 

The program has completed when a box stating "Success! Run complete." shows on the screen.

### Check Module
If enabled in the control file, the program will run in `check` mode, which will run a number of checks built into the `emissions`, `isrm`, and `population` objects. Once it runs all checking functions, it will quit and inform the user of the result. 
