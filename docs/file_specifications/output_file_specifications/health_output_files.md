---
layout: default
title: Control File
parent: Output Files
grand_parent: File Specifications
nav_order: 6
---

## Health Output Files 
When the model is run with RUN_HEALTH, there are three versions of health output files outputted: for all cause, ischemic heart disease, and lung cancer. This page applies to each of the three. 

### Individual health endpoint mortality map
With each run, there will be three pngs developed with the different endpoints all cause, ischemic heart disease, and lung cancel in the format [batch]_[run]total[endpoint]_excess_mortality.png. Each png would have 4 maps: one with total population density, one with total exposure, one with total endpoint excess mortality, and one with total endpoint mortality per 100K. An example is shown below.

![Individual Health Endpoint Mortality png](https://github.com/echo-air-model/echo-air-model.github.io/blob/output_file_pages/assets/getting_started/mac_os/demo_test_03_total_ischemic%20heart%20disease_excess_mortality.png?raw=true)

### Individual health endpoint CSV
Each run also generates 3 CSV spreadsheet files witht he format  Individual health endpoint CSV [batch]_[run]total[endpoint]_excess_mortality.csv for the three endpoints. The CSV file has the following columns: ISRM_ID, CONC_UG/M3 (concentration levles), Asian (# People), Black (# People),	Hispanic/Latino (# People), Native American (# People), White (# People), Total (# People), Other (# People), IHD_ASIAN, IHD_BLACK,	IHD_HISLA,	IHD_INDIG,	IHD_TOTAL,	IHD_WHITE,	IHD_OTHER, and gemoetry. 

### Individual health endpoint shapefiles
Each run developes 3 shapefiles with their  in the format: [batch]_[run]total[endpoint]_excess_mortality.shp)

After each run, a file named "shapes" will be generated, containing shapefiles associated with each endpoint with the following extensions: ".cpg", ".dbf", ".prj", ".shp", and ".shx".

Each extension serves a specific purpose:

.shp (Shapefile):

This file contains the spatial data's geometry (points, lines, or polygons).
.shx (Shape Index):

This file stores an index of the feature geometry for faster access.
.dbf (dBASE Table):

This file is a database that stores attribute data associated with the shapes.
.prj (Projection File):

This file holds information about the coordinate system and projection used.
.cpg (Code Page File):

This file specifies the character encoding used in the attribute data.
