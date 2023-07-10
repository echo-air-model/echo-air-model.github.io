---
layout: default
title: Concentration
parent: Supporting Code Objects
grand_parent: Code Details
nav_order: 2
---

## `concentration.py` 
The `concentration` object runs ISRM-based calculations for each of the vertical layer's of the ISRM grid by processing individual `concentration_layer` objects. The object inputs an emissions object (from `emissions.py`) and the ISRM object (from `isrm.py`). The object then estimates total concentrations at ground-level resulting from emissions.

### Inputs
* `emis_obj`: the emissions object, as defined by `emissions.py`
* `isrm_obj`: the ISRM object, as defined by `isrm.py`
* `detailed_conc_flag`: a Boolean indicating whether concentrations should be output at a detailed level or not

### Attributes
* `isrm_id`: a Series of all ISRM grid cell IDs
* `isrm_geom`: the geometry (geographic attributes) of the ISRM grid
* `crs`: the coordinate reference system associated with the ISRM grid
* `name`: a string representing the run name preferred by the user
* `run_calcs`: a Boolean indicating whether the program should run, or if it should just check the inputs (useful for debugging)
* `verbose`: a Boolean indicating whether the user wants to run in verbose mode

### Calculated Attributes
* `detailed_conc`: geodataframe of the detailed concentrations at ground-level combined from all three vertical layers
* `detailed_conc_clean`: simplified geodataframe of the detailed concentrations at ground-level combined from all three vertical layers
* `total_conc`: geodataframe with total ground-level PM<sub>2.5</sub> concentrations across the ISRM grid

### Internal Functions
* `run_layer`: estimates concentrations for a single layer by creating a `concentration_layer` object for that layer
* `combine_concentrations`: checks for each of the layer flags in the `emissions` object, and then calls the `run_layer` function for each layer that is flagged. Then, combines the concentrations from each layer flagged into the three concentration geodataframes described above

### External Functions
* `visualize_concentrations`: draws a map of concentrations for a variable (`var`) and exports it as a PNG into an output directory (`output_dir`) of choice
* `export_concentrations`: exports concentrations as a shapefile into an output directory (`output_dir`) of choice
