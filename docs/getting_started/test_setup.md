---
layout: default
title: 4. Test Setup
parent: Getting Started
nav_order: 6
---

### Test Setup

Once the data are all imported, navigate back to the main directory and run the `--check-setup` function.

1. Ensure your working directory is open in your terminal.
   ```bash
   pwd
   ```
   
   * This should return `[your/file/path]/working-directory/echo_air`. If it does not, use `cd` to navigate up and down to get there.

2. Run the following code:
   ```bash
   python3 run_echo_air.py --check-setup
   ```
   * If everything is configured correctly, you should get a message that says so.

![Message that shows when configured correctly](https://github.com/echo-air-model/echo-air-model.github.io/blob/main/assets/getting_started/mac_os/copy_data_test_setup.png?raw=true)

[-- Next Step -->](https://echo-air-model.github.io/docs/running_model/running_model.html)
