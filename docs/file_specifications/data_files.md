---
layout: default
title: ECHO-AIR Data Files
parent: File Specifications
has_children: false
nav_order: 0
---

## ECHO-AIR Data Files

All of the ECHO-AIR data files are saved in an Amazon Web Services bucket. Links to each data file are listed below.

### Necessary Data Files

The following files are required to run ECHO-AIR:

* [ISRM Data](https://echo-air.s3.us-gov-west-1.amazonaws.com/CA_ISRM_Data.zip)
* [California Border](https://echo-air.s3.us-gov-west-1.amazonaws.com/ca_border.feather)
* [California Air Basins](https://echo-air.s3.us-gov-west-1.amazonaws.com/air_basins.feather)
* [California Air Districts](https://echo-air.s3.us-gov-west-1.amazonaws.com/air_districts.feather)
* [California Counties](https://echo-air.s3.us-gov-west-1.amazonaws.com/counties.feather)
* [Baseline Incidence Data from BenMAP](https://echo-air.s3.us-gov-west-1.amazonaws.com/benmap_incidence.feather)

Note: you will need to unzip the ISRM data before running ECHO-AIR.

### Sample Input Data Files

The following files provide sample data that you can use in order to set up your ECHO-AIR runs.

* [2010 Population Data](https://echo-air.s3.us-gov-west-1.amazonaws.com/ca2010.feather)
* [Sample Emissions](https://echo-air.s3.us-gov-west-1.amazonaws.com/demo_2000_data.zip)

The sample emissions are 1-km gridded vehicle emissions from California's EMFAC model.

