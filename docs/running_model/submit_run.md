---
layout: default
title: 3. Run the Model
parent: Running the Model
nav_order: 5
---

## 3. Run the Model

It's time to run the model!

1. On the terminal, navigate back to the model directory.
```bash
cd ../../echo-air
      ```

2. Activate the virtual environment.
```bash
source bin/activate
      ```

3. Run the model by calling the name of the program and your control file location.  Note that the control file path should be in single quotes (Unicode U+0027).
```bash
python3 run_echo_air.py -i '[/path/to/control/file]' 
      ```
   * The model has additional run options, as outlined on the Run Options page.

The model will now take a few minutes. You should see text printed on the console with status updates.

[-- Next Step -->](https://echo-air-model.github.io/docs/running_model/download_output_files.html)
