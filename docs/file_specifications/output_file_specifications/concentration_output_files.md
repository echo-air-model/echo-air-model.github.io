---
layout: default
title: Concentration Output Files
parent: Output Files
grand_parent: File Specifications
nav_order: 3
---

## Concentration Output Files
By default, ECHO-AIR will output a number of files related to the concentration calculations.

### Concentration Maps
Concentration maps are generated labeled "[batch]_[run]_pm2.5_concentrations.png" and (when DPM is calculated) "[batch]_[run]_dpm_concentrations.png" 

### Concentration Shapefile
After each run, a folder named "shapes" will be generated, containing shapefiles labeled as "batch_run_detailed_concentration" with the following extensions: ".cpg", ".dbf", ".prj", ".shp", and ".shx". If the user enables the `DETAILED_CONC` option, then the concentrations output will contain speciated concentration data. Concentration shapefiles will include columns for PM<sub>2.5</sub> and DPM (when enabled).

Each extension serves a specific purpose:

- **.shp** (Shapefile): 
  - This file contains the spatial data's geometry (points, lines, or polygons).

- **.shx** (Shape Index):
  - This file stores an index of the feature geometry for faster access.

- **.dbf** (dBASE Table):
  - This file is a database that stores attribute data associated with the shapes.

- **.prj** (Projection File):
  - This file holds information about the coordinate system and projection used.

- **.cpg** (Code Page File):
  - This file specifies the character encoding used in the attribute data.

These files collectively comprise a shapefile, storing both spatial and attribute data, and providing necessary information for spatial analysis and visualization.
