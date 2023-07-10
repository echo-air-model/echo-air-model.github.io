---
layout: default
title: 2. Download Packages and Model
parent: Getting Started
nav_order: 3
---

## 2. Download Packages and Model

The following steps configure your system to have the correct Linux packages, download the model from Github, and set up your virtual environment. These steps are identical regardless of operating system.

1. Download necessary packages to the console.
   ```bash
sudo apt-get update 
sudo apt-get install git
sudo apt-get install build-essential
sudo apt-get install python3-venv
      ```

2. Download the ECHO-AIR Model and navigate to the directory created during cloning.
   ```bash
git clone https://github.com/lkoolik/isrm_health_calculations.git
cd isrm_health_calculations
ls
      ```

If this worked successfully, you should see the following. Note that the green text should say `[your_name]@[machine_name]`

![Screenshot of the directory once the repository is cloned](/assets/getting_started/mac_os/directory_setup_before_data.png)