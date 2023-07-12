---
layout: default
title: Population Input File
parent: Input File Specifications
grand_parent: Running the Model
nav_order: 3
---

## Population Input

By default, the tool will try to run calculations using the 2010 US Census data for California. If you want to replace this input, see the notes below.

Population input files can be shapefiles (created using ArcGIS, QGIS, or coding languages like Python or R) or feather files (best created in Python).

The population file needs to have the following columns in order to run properly. Column names are bolded with descriptions following.
* **POP_ID**: ID column, just needs to be unique
* **YEAR**: year of data, will not be reported but is good practice to be included
* **START_AGE**: the starting age of the bin
* **END_AGE**:  the ending age of the bin
* **AGE_BIN**: the age bin for this population sample. It should be formatted as `START_AGE` TO `END_AGE` (e.g., `0TO0`, `20TO24`). Age bins should be non-overlapping (e.g., not `20TO25` and `25TO30`).
* Seven racial/ethnic group population columns (total people per geographic unit).
   * **ASIAN**: non-Hispanic Asian 
   * **BLACK**: non-Hispanic Black
   * **HISLA**: Hispanic of any race
   * **INDIG**: non-Hispanic Native American  
   * **PACIS**: non-Hispanic Pacific Islander
   * **WHITE**: non-Hispanic White
   * **OTHER**: non-Hispanic Other
* **TOTAL**: the total population for that age bin and geographic area