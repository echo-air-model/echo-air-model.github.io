---
layout: default
title: WSL Prerequisites
parent: Prerequisites
grand_parent: Getting Started
nav_order: 3
---

## Windows Subsystem for Linux Prerequisites
The model was validated on a Windows 10 Enterprise machine. The instructions below may need to be adapted for other versions of Windows.

### Install Windows Subsystem for Linux
In order to run ECHO-AIR on a Windows machine, you must have a distribution for Windows Subsystem for Linux (WSL) installed. The model was validated on Ubuntu version 2204.2.29.0, so this is the recommended version.

1. Using the Microsoft Store, download Ubuntu version 2204.2.29.0.
2. Set up your Ubuntu password and account.
3. Ensure that you are using WSL version 2.
   1. You can check your version of WSL as follows:
      1. Open the command prompt on your Windows machine.
      2. Type the following: 
      ```bash
	 wsl --list --verbose
	 ```

      {:style="counter-reset:step-counter 2"}
         3. The setup is correct if you get the following output: **screenshot**

   {:style="counter-reset:step-counter 1"}
      2. If you are using WSL version 1, you can upgrade it using the following instructions:
         1. In your Ubuntu environment, use the following command:
         ```bash
	    wsl --set-version Ubuntu 2
	    ```

         {:style="counter-reset:step-counter 1"}
            2. If you get an error message like "Please enable Virtual Machine Platform Windows feature and ensure virtualization is enabled in the BIOS", you will need to update your system's settings. The following worked for a Windows 10 Pro AMD machine:

               1. Restart machine and press "F2" or "Del" to access BIOS during startup.
               2. In the "Advanced" Menu, enable SVM.
               3. Save and exit.
               4. Once the PC reboots, try to update the version using the command in the box above again.
               5. If you are still having issues, see further instructions [here](https://bce.berkeley.edu/enabling-virtualization-in-your-pc-bios.html).
