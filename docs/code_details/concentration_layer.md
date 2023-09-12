---
layout: default
title: Concentration Layer
parent: Supporting Code Objects
grand_parent: Code Details
nav_order: 1
---

## `concentration_layer.py` 
The `concentration_layer` object runs ISRM-based calculations using a single vertical layer of the ISRM grid. The object inputs an emissions object (from `emissions.py`), the ISRM object (from `isrm.py`), and the layer number corresponding to the vertical layer of the ISRM grid. The object then estimates concentrations at ground-level resulting from emissions at that vertical layer release range.

### Inputs
* `emis_obj`: the emissions object, as defined by `emissions.py`
* `isrm_obj`: the ISRM object, as defined by `isrm.py`
* `layer`: the layer number (0, 1, or 2)
* `run_parallel`: a Boolean indicating whether or not to run in parallel
* `verbose`: a Boolean indicating whether the user wants to run in verbose mode
* `debug_mode`: a Boolean indicating whether or not to output debug statements

### Attributes
* `isrm_id`: a Series of all ISRM grid cell IDs
* `receptor_id`: a Series of all receptor IDs
* `isrm_geom`: the geometry (geographic attributes) of the ISRM grid
* `crs`: the coordinate reference system associated with the ISRM grid
* `name`: a string representing the run name preferred by the user
* `check`: a Boolean indicating whether the program should run, or if it should just check the inputs (useful for debugging)

### Calculated Attributes
* `PM25e`, `NH3e`, `VOCe`, `NOXe`, `SOXe`: geodataframes of the emissions (for each pollutant) from that layer re-allocated onto the ISRM grid
* `pPM25`, `pNH4`, `pVOC`, `pNO3`, `pSO4`: geodataframes of the concentrations from each primary pollutant from the emissions of that pollutant in that `layer`
* `detailed_conc`: geodataframe containing columns for each primary pollutant's contribution to the total ground-level PM<sub>2.5</sub> concentrations

### Simple Functions
* `allocate_emissions`: inputs the emissions layer and the ISRM geography, and re-allocates the emissions to the ISRM geography using an area-based allocation procedure
* `cut_emissions`: inputs the pollutant geodataframe from the emissions object and slices it based on the minimum and maximum release heights (minimum inclusive, maximum exclusive) associated with the ISRM vertical layer
* `process_emissions`: for each of the five primary pollutants, runs `cut_emissions` and then `allocate_emissions` to return the geodataframes of emissions of each primary pollutant released in the `layer` allocated to the ISRM grid
* `get_concentration`: for a pollutant's emission layer (`POLe`), the ISRM matrix for that pollutant, and the `layer` ID, estimates the concentration at ground-level for the primary pollutant (`pPOL`)
* `combine_concentrations`: merges together all five of the primary pollutant concentration geodataframes (`pPOL`) and adds them together to get total ground-level concentrations resulting from emissions released in that `layer`

