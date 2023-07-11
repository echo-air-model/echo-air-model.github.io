---
layout: default
title: Emissions Input File
parent: Input File Specifications
grand_parent: Running the Model
nav_order: 1
---

## Emissions Input

The emissions input file is the only required input for runs done in California using 2010 Census data. As such, this is the most important input file!

Emissions input files can be shapefiles (created using ArcGIS, QGIS, or coding languages like Python or R), feather files (best created in Python), or CSV files if all sources are point sources (created in Microsoft Excel or similar).

Emissions can be in any of the following mass units and time units. 
* Mass units: 
   * `ug` (micrograms)
   * `g` (grams)
   * `lb` (pounds)
   * `ton` (short tons)
   * `mt` (metric tons)
   * `kg` (kilograms)
* Time units: 
   * `s` (seconds)
   * `min` (minutes)
   * `hr` (hours)
   * `day` (days)
   * `yr` (year)

In the control file, you will indicate units using the abbreviated versions above (e.g., `ug/hr`)

The emissions file needs to have the following columns in order to run properly. Column names are bolded with descriptions following.
* **I_CELL**: ID column, just needs to be unique
* **J_CELL**: ID column, just needs to be unique
* Five emissions columns. These can have any units of mass per time, so long as they are all the same.
   * **PM25**
   * **NH3**
   * **VOC**
   * **NOX**
   * **SOX**
* **HEIGHT_M**: source release height in meters. This can be slightly imprecise, since things are binned into the three layers of the ISRM (0-57 m, 57-140 m, > 760 m)
