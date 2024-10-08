---
layout: default
title: Emissions Output Files
parent: Output Files
grand_parent: File Specifications
nav_order: 2
---

## Emissions Output Files
If enabled with the `OUTPUT_EMIS` option in the control file, the tool will output a shapefile of emissions allocated to the ISRM grid. Details about this output are below.

### Allocated Emissions Shapefiles
After each run, a file named "shapes" will be generated, containing shapefiles. The allocated emissions shapefiles are labeled as "test_layer[run]_allocated_emis" with the following extensions: ".cpg", ".dbf", ".prj", ".shp", and ".shx". 

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
