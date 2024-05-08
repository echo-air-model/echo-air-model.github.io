---
layout: default
title: Control File
parent: Output Files
grand_parent: File Specifications
nav_order: 4
---
## Exposure and Equity Output Files

### Exposure concentration png
An exposure concentration map is generated labeled "[batch]_[run]_PM25_Exposure_Percentiles.png". The map includes PM 2.5 exposure (µg/m³) against percentile among racial/ethnic groups (Total, Asian, Black, Hispanic/Latino, Native American, Pacific Islander, White, and Other). 

### Exposure concentration CSV
An exposure concentration CSV file is generated labeled "[batch]_[run]_exposure_concentrations.csv". Column names are bolded with descriptions following.
* **ISRM_ID**: ID of each ISRM run
* **PM 2.5(µg/m³) Concentration**: PM 2.5 Concentration associated with each ISRM run
* **Total (# People)**: Total number of people exposed with each ISRM run
* **Racial Groups**: The number of people exposed with each respective racial group


### Exposure disparity CSV
An exposure disparity CSV is generated labeled "[batch]_[run]_exposure_disparity.csv". This CSV file includes the group PWM (population weighted mean), absolute disparity, and relative disparity among racial groups. 

### Exposure concentration shapefile
After each run, a file named "shapes" will be generated, containing shapefiles labeled as "[batch]_[run]_exposure_concentrations" with the following extensions: ".cpg", ".dbf", ".prj", ".shp", and ".shx".

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
