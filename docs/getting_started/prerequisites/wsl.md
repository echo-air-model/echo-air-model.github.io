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
   {:style="counter-reset:step-counter 3"}
      3. The setup is correct if you get the following output:
      [screenshot will go here]

{:style="counter-reset:step-counter 2"}
   2. If you are using WSL version 1, you can upgrade it using the following instructions:
      1. In your Ubuntu environment, use the following command:
      ```bash
	wsl --set-version Ubuntu 2
	```
