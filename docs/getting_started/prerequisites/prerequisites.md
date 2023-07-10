---
layout: default
title: Prerequisites
parent: Getting Started
has_children: true
nav_order: 2
---

## Prerequisites

The tool was developed on MacOS Monterey on the Apple M1 with 16 GB Memory. The instructions below may need to be adapted for different processing capabilities. These instructions assume a base level of comfort navigating your file directories in the terminal. For more information on commands you need for following these instructions, see [this article](https://www.makeuseof.com/tag/mac-terminal-commands-cheat-sheet/) on basic Mac OS commands.

### Setting Up Python

#### Install Python
In order to run the ISRM Tool, the computer must have Python installed. I recommend following the guidance provided by [Anaconda](https://docs.anaconda.com/anaconda/install/mac-os/) for downloading Python on Mac. It is also recommended that you install Anaconda Navigator for ease setting up a virtual environment.

#### Virtual Environment
The next step is to create a virtual environment for storing the proper versions of libraries required to run this code pipeline. Details on the specific requirements for the ISRM Tool are specified in the Github Repository's [requirements.txt](https://github.com/lkoolik/isrm_health_calculations/blob/main/requirements.txt) file. To set this up, it is recommended that you download this text file and save it on your computer. There are two ways you can set up your virtual environment.

1. **Option 1: Anaconda GUI**. Within the Anaconda Navigoator, select the tab "Environments" on the left-hand side. At the bottom, select "Import" to create a new environment from a requirements file. Download the requirements.txt file from the Github repository, and import this file (note: you may need to manually switch your import GUI to search for "Pip requirement files" instead of "Conda environment files"). Set your virtual environment name to "isrm_calcs_env" to be consistent with the rest of this guide. Note: if you are running into Python errors when running the program and you performed your setup this way, you may need to re-try with Option 2 below.

2. **Option 2: Terminal**. Navigate to your directory of choice using `cd [directory]` in your Terminal. Follow the instructions from the official Python documentation [here](https://docs.python.org/3/tutorial/venv.html) to create your new virtual environment. Set your virtual environment name to "isrm_calcs_env" to be consistent with the rest of this guide. Next, activate that environment by running `source isrm_calcs_env/bin/activate`. Once the environment is created and activated, import the requirements document by running `python -m pip install -r requirements.txt`. 

You will test that your virtual environment is set up properly in the next section. If you find that it was not set up properly, you can manually update or install the missing libraries/packages using `pip` or the Anaconda Navigator GUI.

#### Clone Repository

It is highly recommended that you clone the repository to keep your code up to date. If you create a static copy, you may miss future changes to the code. You may consider creating a free Github account ([instructions](https://docs.github.com/en/get-started/signing-up-for-github/signing-up-for-a-new-github-account)) and set up your computer to connect with your account ([instructions](https://docs.github.com/en/get-started/getting-started-with-git)). However, it is not required to have your own Github account.

Navigate to the Github repository [here](https://github.com/echo-air-model/echo-air). To clone the repository:

1. Navigate to the directory where you want the code to be saved from within your Mac Terminal: `cd [path/for/code]`

2. On the Github interface, click the green "Code" button and copy the https url.

3. In your Terminal, type: `git clone [url]`

For consistency with this tutorial, name the parent directory "isrm_health_calculations". Your directory should match the screenshot below.
 
![Screenshot of the directory once the repository is cloned](/assets/getting_started/mac_os/directory_setup_before_data.png)


#### Download Data

Within the `isrm_health_calculations` folder, create a new folder called "data". Download the data stored in [this Google drive](https://drive.google.com/drive/folders/14j-yB43YgZgPSPvhjxjdEbhLe6tR0SEc?usp=sharing) into that folder. Note: you should preserve the structure sub-directory "CA_ISRM" if you intend to use the California ISRM. If you have a different ISRM file, mimic this structure with your ISRM file.

#### Test Code 

Once you have everything ready to go above, your directory should mirror the screenshot below.

![Screenshot of the directory when ready to run](/assets/getting_started/mac_os/directory_when_ready.png)

Now, you are ready to test the code. We will do this in two steps.

1. **Confirm Python Works**. In the terminal, navigate to the directory where this code is saved. Type the following command, which should return the built-in help statement for the ISRM Tool:

 `python isrm_calcs.py -h`

 This is successful if you get the following help message returned:

    usage: isrm_calcs.py [-h] [-i INPUTS]

    Runs the ISRM-based tool for estimating PM2.5 concentrations and associated health impacts.

    optional arguments:
      -h, --help            show this help message and exit
      -i INPUTS, --inputs INPUTS
                            control file path

2. **Create a Test File**. 

Within the "templates" folder of the isrm_health_calculations directory, there should be a text file called "control_file_template.txt". Copy this file to a directory of choice. For the purposes of this exercise, I will make a copy called "control_file_test.txt".
 
Open the text file with a text editor (e.g., TextEdit, Notepad++). Make the following changes. Note - in a future section, I will discuss how to update this control file.
 
        ╓─────────────────────────────────╖
        ║  HEALTH RUN CONTROLS            ║
        ║  These should be set to Y or N  ║
        ╙─────────────────────────────────╜
        - RUN_HEALTH: N
        - RACE_STRATIFIED_INCIDENCE: N
        
        ╓────────────────────────────────╖
        ║ RUN CONTROLS                   ║
        ║ These should be set to Y or N  ║
        ╙────────────────────────────────╜
        - CHECK_INPUTS: Y
        - VERBOSE: Y
        
        ╓──────────────────╖
        ║  OUTPUT OPTIONS  ║
        ╙──────────────────╜
        - REGION_OF_INTEREST: 
        - REGION_CATEGORY: 
        - OUTPUT_RESOLUTION: 
        - OUTPUT_EXPOSURE: N
    
Back in the terminal in the isrm_health_calcs directory with the isrm_calcs_env virtual environment activated, type the following prompt:

   `python isrm_calcs.py -i 'path/to/control/file/control_file_test.txt'`
   
If this worked properly, you should get a box pop up with the name of the tool and the version. Then, you should get a number of bulleted messages in simple English about problems running the code. An example is below. These messages are okay and mean that Python is set up properly! 
   
   `* Issue finding ISRM_NH3.npy in the provided ISRM directory`
   `<< ERROR: Control file was successfully imported but inputs are not correct >>`

