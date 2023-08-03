---
layout: default
title: 3. Create Virtual Environment
parent: Getting Started
nav_order: 4
---

## 3. Create Virtual Environment

The following steps create a virtual Python environment to ensure the model is run with the correct Python libraries. These steps are identical regardless of operating system.

1. Create a virtual Python environment.

    ```bash
python3 -m venv .
       ```

2. Activate the virtual environment.
    ```bash
source bin/activate 
       ```

   * If this worked successfully, you should see the directory name in parentheses before your terminal input.

**screenshot**

{:style="counter-reset:step-counter 2"}
   3. Add Python libraries to the new virtual environment using the requirements file that was downloaded when the Github was cloned.
   ```bash
python3 -m pip install -r requirements.txt
      ```

      * You may be prompted to say `Y` or `N`. Respond `Y` to all prompts.

{:style="counter-reset:step-counter 3"}
   4. To confirm that the libraries are installed properly, run the following code. If you get a help message, the installation has worked properly.
   ```bash
python3 run_echo_air.py -h
      ```

      * An example of the help message is below.

**screenshot**

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/copy_data.html)
