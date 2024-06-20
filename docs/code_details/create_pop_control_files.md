---
layout: default
title: create_control_files.py
parent: Code Details
nav_order: 4
---

# THIS NEEDS TO BE EDITED STILL!!! NOT DONE!!

## `create_pop_control_files.py`
The `create_pop_control_files.py` script is a helpful script file for generating the population control file for ECHO-AIR model runs. The script will generate control files.

### Creating Control Files
To use `create_pop_control_files.py`, follow these steps.

1. Create a copy of the batch_control_file_input_template.csv file that is saved in the echo-air directory under "templates".
2. Open the copy of the file in a CSV-editor (e.g., Microsoft Excel, Google Sheets, notepad).
3. Add a column for each of the control files you want to create, following the instructions for the [Control File Specifications](https://echo-air-model.github.io/docs/file_specifications/input_file_specifications/control_file_input.html). Save this file as a CSV.
4. Start up your console (e.g., Mac Terminal, Windows Ubuntu, Linux terminal) following the same [process](https://echo-air-model.github.io/docs/getting_started/start_up_console.html) as described during setup. Navigate to the echo-air directory.
```bash
cd [your/file/path]/echo-air
   ```

5. Call the `create_control_files.py` script through the terminal, substituting in the following inputs: where the snippet below says \[path/to/batch_control_file_input\], use the path to the file you edited as part of step 3; where the snippet below says \[path/to/outputs\], put the file path for where you want the control files to be saved.
```bash
python3 create_control_files.py -i '[path/to/batc_control_file_input]' -o '[path/to/outputs]'
   ```

### Code Details
The control file creation program is relatively simple in design. 

It will start by reading in the template control file that is stored within echo-air. That way, you will always start with the most up-to-date version of the control file. 

The program will then read the CSV file provided by the user to determine how many control files are desired by the user. 

Next, the program will iterate through the columns of the provided csv file to create a control file for each column based on a copy of the template control file. It will also store the filepath of each generated control file to create a text file that has the batch commands you need to copy in order to run ECHO-AIR with your control files.

The program has completed when a box stating "Success! Script complete." shows on the screen.
