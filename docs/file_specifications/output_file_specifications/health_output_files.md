---
layout: default
title: Health Output Files
parent: Output Files
grand_parent: File Specifications
nav_order: 6
---

## Health Output Files 
When the model is run with RUN_HEALTH, the output files will be generated for three excess mortality endpoints: all cause mortality, ischemic heart disease, and lung cancer. This page applies to each of the three. 

### Individual Health Endpoint Mortality Maps
With each run, there will be three map figures (one per endpoint) in the format [batch]_[run]total[endpoint]_excess_mortality.png. Each map figure contains four maps: total population density, total exposure, total endpoint excess mortality, and total endpoint mortality per 100K people. An example is shown below.

![Individual Health Endpoint Mortality png](https://github.com/echo-air-model/echo-air-model.github.io/blob/main/assets/getting_started/mac_os/demo_test_03_total_ischemic%20heart%20disease_excess_mortality.png)

### Individual Health Endpoint Data
Each run also generates a CSV spreadsheet file with the format [batch]_[run]total[endpoint]_excess_mortality.csv for each of the three endpoints. The CSV file has the following columns: ISRM_ID, CONC_UG/M3 (concentration levles), Asian (# People), Black (# People),	Hispanic/Latino (# People), Native American (# People), White (# People), Total (# People), Other (# People), [endpoint]_ASIAN, [endpoint]_BLACK,	[endpoint]_HISLA,	[endpoint]_INDIG,	[endpoint]_TOTAL,	[endpoint]_WHITE,	and [endpoint]_OTHER. 

### Individual Health Endpoint Shapefiles
Each run generates three shapefiles with in the format: [batch]_[run]total[endpoint]_excess_mortality.shp.

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
