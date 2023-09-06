---
layout: default
title: 2. Make Control File
parent: Running the Model
nav_order: 4
---

## 2. Make Control File

The control file is the backbone of the entire model run. For more information about the control file, see the [Control File Specifications](https://echo-air-model.github.io/docs/file_specifications/input_file_specifications/control_file_input.html).

If you are running on Mac or WSL, you can make and edit the control file in your [file explorer and text editor](https://echo-air-model.github.io/docs/running_model/make_control_file.html#option-1-file-explorer-and-text-editor). If you are using a Linux terminal or Google Cloud, you must do it through the [command line](https://echo-air-model.github.io/docs/running_model/make_control_file.html#option-2-command-line).

### Option 1: File Explorer and Text Editor

1. Using your file explorer, navigate to the `templates` folder of the ECHO-AIR model.

2. Copy that text file and paste it in the `inputs` directory you have created with your input files.

3. Open the control file using a text editor (e.g., Notepad++, TextEdit, Wordpad and edit the control file following the [specifications](https://echo-air-model.github.io/docs/file_specifications/input_file_specifications/control_file_input.html).

4. Save and close.

5. As a final step, write down the current path so you have it on hand.

[-- Next Step -->](https://echo-air-model.github.io/docs/running_model/submit_run.html)

----

### Option 2: Command Line

1. Create a copy of the control file from the templates folder. Rename the control file using the second line, if desired.
   ```bash
cp /home/[your_name]/[your/file/path]/echo-air/templates/control_file_template.txt .
mv control_file_template.txt [new_name].txt
      ```

2. Edit the control file. If you are struggling to edit the file using the command line, you can download a copy of the control file from the Github repository online, make edits, and upload using the same process as you have previously uploaded files.

   1. Open the control file.
      ```bash
vi [control_file_name].txt 
         ```

   2. Switch to insert mode by hitting `i`.

   3. Edit the control file, following the [specifications](https://echo-air-model.github.io/docs/file_specifications/input_file_specifications/control_file_input.html).

   4. When you are done editing, hit `esc` and then type `:wq` and hit `enter`.

3. As a final step, write down the current path so you have it on hand (use `pwd`).

[-- Next Step -->](https://echo-air-model.github.io/docs/running_model/submit_run.html)
