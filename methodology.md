---
layout: default
title: Methodology
nav_order: 2
---

## Methodology ##
The ISRM Health Calculation model works by a series of two modules. First, the model estimates annual average change in PM<sub>2.5</sub> concentrations as part of the **Concentration Module**. Second, the excess mortality resulting from the concentration change is calculated in the **Health Module**.

### Concentration Module Methodology ###
The InMAP Source Receptor Matrix (ISRM) links emissions sources to changes in receptor concentrations. There is a matrix layer for each of the five precursor species: primary PM<sub>2.5</sub>, ammonia (NH<sub>3</sub>), oxides of nitrogen (NOx), oxides of sulfur (SOx), and volatile organic compounds (VOC). By default, the tool uses the California ISRM. For each of these species in the California ISRM, the ISRM matrix dimensions are: 3 elevations by 21,705 sources by 21,705 receptors. The three elevations of release height within the ISRM are:
* Less than 57 meters
* Between 57 and 140 meters
* Greater than 760 meters.

The tool is capable of reading in a different ISRM, if specified by the user. 

The units of each cell within the ISRM are micrograms per meter cubed per microgram per second, or concentration per emissions. 

The concentration module has the following steps. Details about the code handling each step are described in the Code Details section.

1. **Preprocessing**: the tool will load the emissions shapefile and perform a series of formatting checks and adjustments. Any updates will be reported through the command line. Additionally, the ISRM layers will be imported as an object. The tool will also identify how many of the ISRM layers are required for concentration calculations.

For each layer triggered in the preprocessing step: 

2. **Emissions Re-Allocation**: the tool will re-grid emissions to the ISRM grid.
   1. The emissions shape and the ISRM shape are intersected.
   2. Emissions for the intersection object are allocated from the original emissions shape by the percent of the original emissions area that is contained within the intersection.
   3. Emissions are summed by ISRM grid cell.
   4. Note: for point source emissions, a small buffer is added to each point to allocate to ISRM grid cells.
3. **Matrix Multiplication**: Once the emissions are re-gridded to the ISRM grid, they are multiplied by the ISRM grid level for the corresponding layer. 

Once all layers are done:

4. **Sum all Concentrations**: concentrations of PM<sub>2.5</sub> are summed by ISRM grid cell.

### Health Module Methodology ###
The ISRM Tool calculations health module follows US EPA BenMAP CE methodology and CARB guidance. 

Currently, the tool is only built out to use the Krewski et al. (2009), endpoint parameters and functions.[^1] The Krewski function is as follows:

$$ \Delta M = 1 - ( \frac{1}{\exp(\beta_{d} \times C_{i})} ) \times I_{i,d,g} \times P_{i,g} $$

where $\beta$ is the endpoint parameter from Krewski et al. (2009), $d$ is the disease endpoint, $C$ is the concentration of PM<sub>2.5</sub>, $i$ is the grid cell, $I$ is the baseline incidence, $g$ is the group, and $P$ is the population estimate. The tool takes the following steps to estimate these concentrations.

1. **Preprocessing**: the tool will merge the population and incidence data based on geographic intersections using the `health_data.py` object type. 

2. **Estimation by Endpoint**: the tool will then calculate excess mortality by endpoint:
   1. The population-incidence data are spatially merged with the exposure concentrations estimated in the Concentration Module.
   2. For each row of the intersection, the excess mortality is estimated based on the function of choice (currently, only Krewski).
   3. Excess mortality is summed across age ranges by ISRM grid cell and racial/ethnic group.

Once all endpoints are done:

3. **Export and Visualize**: excess mortality is exported as a shapefile and as a plot.

### Other Features ###
The ISRM Tool has a command called `check-setup` that allows the user to make sure that all of the code and data files are properly saved and named in order to make sure that the program will run.

----
## References
[^1]: [Krewski et al., (2009) Extended Follow-Up and Spatial Analysis of the American Cancer Society Study Linking Particulate Air Pollution and Mortality. HEI Research Report 140.](https://www.healtheffects.org/publication/extended-follow-and-spatial-analysis-american-cancer-society-study-linking-particulate)
