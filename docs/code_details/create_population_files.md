---
layout: default
title: create_population_files.py
parent: Other Information
nav_order: 2
---

## Creating Population Files
The `create_population_files.py` script is the main script file used to create population data that can be used for the model. This script operates the command line functionality and outputs the desired population file. The `create_population_files.py` script is not split into functions or objects, instead, it runs through intializing and calling other supporting code files.

### Initialization and Run Program
In the initialization section of `create_population_files.py`, the parser object is created in order to interface with the command line. The parser object is created using the `argparse` library. 

Once the parser is defined, the population control file object is created using `pop_control_file.py` class object. A number of metadata variables are defined from the control file. 

Next, a number of internally saved data file paths are saved. A census object is then created using `census.py`, where the census object is used to preprocess census data and output usable population data. 

After the population data is saved to the output directory, the program outputs, "ECHO-AIR has created and exported all control files indicated."
