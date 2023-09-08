---
layout: default
title: create_control_files.py
parent: Code Details
nav_order: 4
---

## `create_control_files.py`
The `create_control_files.py` script is a helpful script file for generating control files for ECHO-AIR model runs. This script is not necessary for running ECHO-AIR, but may be helpful, especially in the case of batch running. The script will generate control files and a batch run script based on a CSV file input.

### Using `create_control_files.py`
To use `create_control_files.py`, follow these steps.

1. Create a copy of the batch_control_file_input_template.csv file that is saved in the echo-air directory under "templates".
2. Open the copy of the file in a CSV-editor (e.g., Microsoft Excel, Google Sheets, notepad).
3. Add a column for each of the control files you want to create, following the instructions for the [Control File Specifications](https://echo-air-model.github.io/docs/file_specifications/input_file_specifications/control_file_input.html).

### Code Details
The run program section of the code is split into two modes. If the CHECK_INPUTS flag is given, the tool will run in check mode, where it will check that each of the inputs is valid and then quit. If the CHECK_INPUTS flag is not given, the tool will run the full program. 

It will start by creating a log file using the `setup_logging` function. Once the logging is set up, an output directory is created using the `create_output_dir` function from `tool_utils.py`. It will also create a shapefile subdirectory within the output folder directory using `create_shape_out`. The tool will also create an `output_region` geodataframe from user inputs for use in future steps.

Then, the model will begin the concentration module. This starts by defining an emissions object and an isrm object using the `emissions.py` and `isrm.py` supporting class objects. The concentrations will be estimated using the `concentration.py` object, which relies on the `concentration_layer.py` object. The concentrations will then be output as a map of total exposure concentration and a shapefile with detailed exposure information. 

Next, the model will run environmental justice exposure calculations using the `create_exposure_df`, `get_overall_disparity`, and `estimate_exposure_percentile` functions from the `environmental_justice_calcs.py` file. The exposure percentiles will then be plotted and exported using the `plot_percentile_exposure` function. If the control file has indicated that exposure data should be output (using the 'OUTPUT_EXPOSURE' flag), a shapefile of exposure concentrations by population group will be output in the output directory.

Finally, if indicated by the user, the model will begin the health module. It will create the health input object using the `health_data.py` library and then estimate the three endpoints of excess mortality using `calculate_excess_mortality` from the `health_impact_calcs` file. Each endpoint will then be mapped and exported using `visualize_and_export_hia`.

If enabled, the model utilizes parallel computing to increase efficiency and reduce runtime. As such, many of these steps do not happen exactly in the order presented above. 

The program has completed when a box stating "Success! Run complete." shows on the screen.
