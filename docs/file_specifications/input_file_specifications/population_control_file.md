---
layout: default
title: Population Control File
parent: Input Files
grand_parent: File Specifications
nav_order: 5
---

## Population Control File

The population control file is required to create population data. It should be a text file (with extension `.txt`) created in any text editor (e.g., TextEdit, Notepad++, Worded).

There is a template control file stored in the `templates` folder of the ECHO-AIR Model repository called `pop_control_file_template.txt`. This version will always be the most up-to-date. It is good practice to check the templates folder before starting a new run.

The tables below describe all of the fields of the control file. The “Required” column indicates if the input is required for the tool to run. If it is not required, ECHO-AIR will assume a default value.

## Downloading Census Data
Census data can be downloaded from IPUMS NGHIS and processed through running the `create_population_files.py`. This outputs a useable population data file which can then be used to run the model.

The necessary file paths needed after downloading are the codebook file path which ends in codebook.txt, the tract data file path which ends in tract.csv, and the tract shapefile which ends in tract.shp.

### Meta Data

This section provides the model with a naming structure for output files.


<table cellspacing="0" cellpadding="0">
  <tr>
    <th>Field</th><th>Required</th><th>Description</th><th>Test Data Input</th>
  </tr>
  <tr>
    <td> OUTPUT_FILE_NAME </td><td> Yes </td><td> Provides a name for the output file </td><td> california_population </td>
  </tr>
</table>

### Health Run Controls

<table cellspacing="0" cellpadding="0">
  <tr>
    <th>Field</th><th>Required</th><th>Description</th><th>Example Test Data Input</th>
  </tr>
  <tr>
    <td> CODEBOOK_FP</td><td> Yes </td><td> File path for the codebook data. </td><td> /home/[your_name]/inputs/[input_folder]/nhgis0005_ds173_2010_tract_codebook.txt </td>
  </tr>
  <tr>
    <td> TRACT_DATA_FP </td><td> Yes </td><td> File path for tract data. </td><td> /home/[your_name]/inputs/[input_folder]/nhgis0005_ds173_2010_tract.csv </td>
  </tr>
  <tr>
    <td> IPUMS_SHP_FP </td><td> Yes </td><td> File path for shapefile. </td><td> /home/[your_name]/inputs/[input_folder]/US_tract_2010.shp </td>
  </tr>
</table>

### Run Controls

<table cellspacing="0" cellpadding="0">
  <tr>
    <th>Field</th><th>Required</th><th>Description</th><th>Test Data Input</th>
  </tr>
    <td> VERBOSE </td><td> No </td><td> If enabled, it will output more logging statements. </td><td> Y </td>
  </tr>
</table>
