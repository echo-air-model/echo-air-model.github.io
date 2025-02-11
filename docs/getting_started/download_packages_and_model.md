---
layout: default
title: 2. Download Packages and Model
parent: Getting Started
nav_order: 3
---

## 2. Download Packages and Model

The following steps configure your system to have the correct Linux packages, download the model from Github, and set up your virtual environment. 

### Linux and WSL

1. Download necessary packages to the console.
   ```bash
sudo apt-get update 
sudo apt-get install git
sudo apt-get install build-essential
sudo apt-get install python3-venv
      ```

### Mac
1. Download necessary packages to the console
   ```bash
brew update 
brew install git
brew install build-essential
brew install python3-venv
      ```

### All Operating Systems
2. Download the ECHO-AIR Model and navigate to the directory created during cloning.
   ```bash
git clone https://github.com/echo-air-model/echo-air.git
cd echo-air
ls
      ```

If this worked successfully, you should see the following. Note that the green text should say `[your_name]@[machine_name]`

![**Screenshot**](https://echo-air-model.github.io/assets/getting_started/mac_os/github_clone_success_scripts.png)



[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/create_virtual_environment.html)
