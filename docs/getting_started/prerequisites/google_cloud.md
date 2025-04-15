---
layout: default
title: Google Cloud Prerequisites
parent: Prerequisites
grand_parent: Getting Started
nav_order: 4
---

## Google Cloud Console Prerequisites
The model was validated on the Google Cloud console. 

### Set Up Google Cloud Console
In order to run ECHO-AIR on Google Cloud, you must have a Google Cloud Platform account. You can create one following the instructions [here](https://www.youtube.com/watch?v=m5hwU0jD0qc).

### Configure Your Project
To run ECHO-AIR, you will need to create a Project within the Cloud Platform.

1. Sign into your Google Cloud Platform account.
2. Follow the instructions [here](https://cloud.google.com/resource-manager/docs/creating-managing-projects) to create a new project.
   1. You may need to create a new organization following the instructions [here](https://cloud.google.com/resource-manager/docs/creating-managing-organization?_gl=1*u7wu4o*_ga*MTUwMDc5NTgyNy4xNjY3MzQzNzAx*_ga_WH2QY8WWF5*MTY3NjQ4NTMwMC4xMi4xLjE2NzY0ODU4NTMuMC4wLjA.&_ga=2.220114265.-1500795827.1667343701).
3. Ensure that billing is enabled for Compute Engine and Cloud Storage.
4. Navigate to the Compute Engine page and create an instance following the instructions [here](https://www.youtube.com/watch?v=mZsdm9mRc94).
   1. It is recommended that you set up a machine type of e2-standard-16 or higher.
   2. The Boot disk should have a minimum of 64 GB.
5. Navigate to the Cloud Storage Bucket page and create a Cloud Storage Bucket following the instructions [here](https://cloud.google.com/storage/docs/creating-buckets).

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/start_up_console.html)
