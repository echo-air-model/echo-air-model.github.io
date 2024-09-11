---
layout: default
title: Concentration Output Files
parent: Output Files
grand_parent: File Specifications
nav_order: 3
---

## Concentration Output Files
By default, ECHO-AIR will output a number of files related to the concentration calculations.

### Concentration Map
A concentration map is generated labeled "[batch]_[run]_all emissions_concentrations.png". An example of a map is shown below. 

[image]

### Concentration Shapefile
After each run, a file named "shapes" will be generated, containing shapefiles labeled as "batch_run_detailed_concentration" with the following extensions: ".cpg", ".dbf", ".prj", ".shp", and ".shx". If the user enables the `DETAILED_CONC` option, then the concentrations output will contain speciated concentration data.

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
