---
layout: default
title: 2. Make Control File
parent: Running the Model
nav_order: 4
---

## 2. Make Control File

The control file is the backbone of the entire model run. For more information about the control file, see the [Control File Specifications](https://echo-air-model.github.io/docs/running_model/input_file_specifications/control_file_input.html).

If you are running on Mac or WSL, you can make and edit the control file in your file explorer and text editor. If you are using a Linux terminal or Google Cloud, you must do it through the command line.

### Option 1: File Explorer and Text Editor

asdfsadf

### Option 2: Command Line

1. Create a copy of the control file from the templates folder. Rename the control file using the second line, if desired.
   ```bash
cp /home/[your_name]/[your/file/path]/echo-air/templates/control_file_template.txt .
mv control_file_template.txt [new_name].txt
      ```

2. Ensure you are working with the latest version of the ECHO-AIR Model by pulling from Github. **You should do this every time you want to run it.**
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

[-- Next Step -->](https://echo-air-model.github.io/docs/running_model/test_data.html)