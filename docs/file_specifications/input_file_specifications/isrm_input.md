---
layout: default
title: ISRM Input File
parent: Input Files
grand_parent: File Specifications
nav_order: 4
---

## ISRM Input

By default, the ECHO-AIR Model data set includes a sliced and reconfigured version of the [California ISRM](https://zenodo.org/record/7548607). To replace this with another ISRM, follow the steps below. Note: this has not been tested yet and it is recommended that this is done in Python.

1. Assign a unique numeric index to each grid cell of your ISRM.

2. Extract the ISRM geographic data and save as a feather file called `isrm_geo.feather`. It is recommended that you do this step in Python.

3. Slice the source-receptor layers from the ISRM (e.g., pNO3, pPrimaryPM25) into numpy arrays with dimensions (3, *n*, *n*), where *n* is the number of cells. These cells should be ordered in the same order as the numeric indices in step (a).

4. Export each of these into individual numpy files with the following names:
   * `ISRM_NH3_LA.npy`, `ISRM_NH3_LB.npy`, `ISRM_NH3_LC.npy`
   * `ISRM_NOX_LA.npy`, `ISRM_NOX_LB.npy`, `ISRM_NOX_LC.npy`
   * `ISRM_PM25_LA.npy`, `ISRM_PM25_LB.npy`, `ISRM_PM25_LC.npy`
   * `ISRM_SOX_LA.npy`, `ISRM_SOX_LB.npy`, `ISRM_SOX_LC.npy`
   * `ISRM_VOC_LA.npy`, `ISRM_VOC_LB.npy`, `ISRM_VOX_LC.npy`

5. Save the feather file and numpy files into one folder. This is the ISRM input.
