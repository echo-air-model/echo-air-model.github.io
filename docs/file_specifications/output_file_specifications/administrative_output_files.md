---
layout: default
title: Control File
parent: Output File
grand_parent: File Specifications
nav_order: 1
--- 

## Administrative Output Files
With each run, the output files will be generated within a designated folder, each labeled as "out_batch_test_run", where "name" is replaced by the name of the text file used for the run.

### Control File (I'm assuming copy straight from input file)?? 
A copy of the control file used is located in the designated folder. The control file is a critical input for any model run. It should be a text file (with extension `.txt`) created in any text editor (e.g., TextEdit, Notepad++, Worded).

There is a template control file stored in the `templates` folder of the ECHO-AIR Model repository. This version will always be the most up-to-date. It is good practice to check the templates folder before starting a new run.

The tables below describe all of the fields of the control file. The “Required” column indicates if the input is required for the tool to run. If it is not required, ECHO-AIR will assume a default value. Additionally, the table below includes a suggestion for inputs for the [test data](https://echo-air-model.github.io/docs/running_model/test_data.html).

## Text Log File

A text file labeled "log_[batch]_[run].txt" is generated. This file contains all the log statements made during the run, providing useful reference when reviewing the process.
