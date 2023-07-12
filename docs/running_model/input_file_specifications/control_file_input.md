---
layout: default
title: Control File
parent: Input File Specifications
grand_parent: Running the Model
nav_order: 1
---

## Control File

The control file is a critical input for any model run. It should be a text file (with extension `.txt`) created in any text editor (e.g., TextEdit, Notepad++, Worded).

There is a template control file stored in the `templates` folder of the ECHO-AIR Model repository. This version will always be the most up-to-date. It is good practice to check the templates folder before starting a new run.

The tables below describe all of the fields of the control file. The “Required” column indicates if the input is required for the tool to run. If it is not required, ECHO-AIR will assume a default value. Additionally, the table below includes a suggestion for inputs for the [test data](https://echo-air-model.github.io/docs/running_model/test_data.html).

### Meta Data

This section provides the model with a naming structure for output files.


<table cellspacing="0" cellpadding="0">
  <tr>
    <th>Field</th><th>Required</th><th>Description</th><th>Test Data Input</th>
  </tr>
  <tr>
    <td> `BATCH_NAME` </td><td> No </td><td> Provides a name for the batch of runs </td><td> `test` </td>
  </tr>
  <tr>
    <td> `RUN_NAME` </td><td> No </td><td> Provides a run-specific name </td><td> `cy2000` </td>
  </tr>
</table>

### Emissions Data

<table cellspacing="0" cellpadding="0">
  <tr>
    <th>Field</th><th>Required</th><th>Description</th><th>Test Data Input</th>
  </tr>
  <tr>
    <td> `EMISIONS_FILENAME` </td><td> Yes </td><td> Provides the path to the emissions file. For shapefiles, use the .shp file. </td><td> `/home/[your_name]/inputs/[input_folder]/demo_2000_data.shp` </td>
  </tr>
  <tr>
    <td> `EMISSIONS_UNITS` </td><td> Yes </td><td> Provide the units for emissions </td><td> `ton/yr` </td>
  </tr>
</table>

### ISRM and Population Data

<table cellspacing="0" cellpadding="0">
  <tr>
    <th>Field</th><th>Required</th><th>Description</th><th>Test Data Input</th>
  </tr>
  <tr>
    <td> `ISRM_FOLDER` </td><td> Yes </td><td> Provides the path to the folder containing the ISRM files </td><td> `/home/[your_name]/[your/path/here]/echo_air/data/CA_ISRM` </td>
  </tr>
<tr>
    <td> `POPULATION_FILENAME` </td><td> Yes </td><td> Provides the path to the population file. For shapefiles, use the .shp file. </td><td> `/home/[your_name]/[your/path/here]/echo_air/data/ca2010.feather` </td>
  </tr>
</table>

### Health Run Controls

<table cellspacing="0" cellpadding="0">
  <tr>
    <th>Field</th><th>Required</th><th>Description</th><th>Test Data Input</th>
  </tr>
  <tr>
    <td> `RUN_HEALTH` </td><td> No </td><td> Indicates whether you want health results. If blank, will run only concentrations. </td><td> `Y` </td>
  </tr>
  <tr>
    <td> `RACE_STRATIFIED_INCIDENCE` </td><td> No </td><td> Future option, currently does not do anything. </td><td> `N` </td>
  </tr>
</table>

### Run Controls

<table cellspacing="0" cellpadding="0">
  <tr>
    <th>Field</th><th>Required</th><th>Description</th><th>Test Data Input</th>
  </tr>
  <tr>
    <td> `CHECK_INPUTS` </td><td> No </td><td> If enabled, will check all of your inputs and then exit. </td><td> `N` </td>
  </tr>
  <tr>
    <td> `VERBOSE` </td><td> No </td><td> If enabled, it will output more logging statements. </td><td> `Y` </td>
  </tr>
</table>

### Output Options

<table cellspacing="0" cellpadding="0">
  <tr>
    <th>Field</th><th>Required</th><th>Description</th><th>Test Data Input</th>
  </tr>
  <tr>
    <td> `REGION_OF_INTEREST` </td><td> No </td><td> If provided an input, will output results only for this region. </td><td> leave blank </td>
  </tr>
  <tr>
    <td> `REGION_CATEGORY` </td><td> No </td><td> If provided an region of input, provide the type of region (e.g., AD = Air District, AB = Air Basin, C = County). </td><td> leave blank </td>
  </tr>
  <tr>
    <td> `OUTPUT_RESOLUTION` </td><td> No </td><td> If provided, will aggregate results from ISRM grid cell to provided resolution. </td><td> leave blank </td>
  </tr>
  <tr>
    <td> `OUTPUT_EXPOSURE` </td><td> No </td><td> If enabled, will output population with concentration data. </td><td> leave blank </td>
  </tr>
  <tr>
    <td> `DETAILED_CONC` </td><td> No </td><td> If enabled, will output concentration data with additional columns for the precursor species </td><td> leave blank </td>
  </tr>
</table>