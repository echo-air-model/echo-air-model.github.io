---
layout: default
title: Acknowledgments
nav_order: 5
---

## Additional Information
`create_population_files.py` serves as the counterpart to `run_echo_air.py` specifically designed for generating population files. A dedicated population control file is essential for this process, which you can create by either duplicating `pop_control_file_template.txt` located in the templates directory or executing `create_pop_control_file.py`.

For detailed instructions on completing the population control file, please consult the Population Control File Specifications](https://echo-air-model.github.io/docs/file_specifications/input_file_specifications/pop_control_file_input.html).

Once you have filled out the population control file, it can be utilized to execute create_population_files.py. For further guidance on using this script, please refer to [Create Population Files](https://echo-air-model.github.io/docs/code_details/create_population_files.html).

Aside from creating population files, the `create_population_files.py` and `pop_control_file.py` files are unused. During normal ECHO-AIR runs, the main control file should be used. 
