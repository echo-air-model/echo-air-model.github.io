---
layout: default
title: 1. Prepare Inputs and Terminal
parent: Running the Model
nav_order: 3
---

## 1. Prepare Inputs and Terminal

The first step is to prepare your input files (see [Input File Specifications](https://echo-air-model.github.io/docs/running_model/input_file_specifications/input_file_specifications.html) for more details) and launch your terminal. 

1. Start up your console (e.g., Mac Terminal, Windows Ubuntu, Linux terminal) following the same [process](https://echo-air-model.github.io/docs/getting_started/start_up_console.html) as described during setup. You do not need to reset the privileges if you have already set up the model.

2. Navigate to the directory where the model is saved (`[your/file/path]/echo-air`).
   ```bash
cd [your/file/path]/echo-air  
      ```

3. Ensure you are working with the latest version of the ECHO-AIR Model by pulling from Github. **You should do this every time you want to run it.**
   ```bash
git pull origin 
      ```
   * If you get a message that says "Already up to date", then nothing has updated.

4. If you have not already, create an inputs folder outside of the model directory. It should end up with the following path if you call `pwd` in this folder: `/home/[your_name]/[your/file/path]/inputs`
   ```bash
cd ..
mkdir inputs
      ```

   * If you are using Windows Subsystem for Linux (e.g., Ubuntu), this path may exist somewhere else. You can use your file explorer to find the path to your file, and then precede it with `/mnt/c/[your/file/path]`

5. Enter the inputs directory.
   ```bash
cd inputs  
      ```

6. Confirm that your input files are stored in this directory by using `pwd`.

[-- Next Step -->](https://echo-air-model.github.io/docs/running_model/make_control_file.html)