---
layout: default
title: Administrative Output Files
parent: Output Files
grand_parent: File Specifications
nav_order: 1
--- 

## Administrative Output Files
With each run, the output files will be generated within a designated folder, each labeled as "out_batch_test_run", where "name" is replaced by the name of the text file used for the run.

### Control File
A copy of the control file used is located in the designated folder. The control file is a critical input for any model run. It should be a text file (with extension `.txt`) created in any text editor (e.g., TextEdit, Notepad++, Worded).

### Text Log File
A text file labeled "log_[batch]_[run].txt" is generated. This file contains all the log statements made during the run, providing useful reference when reviewing the process. These log statements mirror the printed statements in the terminal. 
