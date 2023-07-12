---
layout: default
title: 4. Download Outputs
parent: Running the Model
nav_order: 6
---

## 4. Download Outputs

ECHO-AIR will generate a number of output files. A description of all of the output files can be found in Output File Specifications.

ECHO-AIR saves output files in a folder inside the model directory called `outputs`. If you are running on Mac or WSL, you can make and edit the control file in your [file explorer](...). If you are using Google Cloud, you must do it through the [Google Cloud Console](...).

### Option 1: File Explorer

1. Using your file explorer, navigate to the `outputs` folder of the ECHO-AIR model.

2. You should see a number of output files and sub-directories. Confirm that all files are present, and then share, edit, and download as appropriate.

### Option 2: Google Cloud Console 

1. When the model is done running, navigate to the `outputs` folder and check to confirm that a directory has been generated for your outputs. 
   ```bash
cd outputs
ls -l
      ```

2. Enter that directory (`output_directory_name`) and confirm that output files have been properly generated.
   ```bash
cd [output_directory_name]
ls -l
      ```

3. Once you confirm all of your outputs are stored, copy your files over to the bucket to download them to your computer. You should first move back up to your main `outputs` folder. It is recommended to have a folder on the bucket for your output files (e.g., “outputs” as shown below).
   ```bash
cd ..
gsutil cp -r [output_directory_name] gs://[bucket]/outputs
      ```
   * Note: the first time that you do this on a VM, you may encounter an `AccessDenied` error. To fix this error, follow these steps:
      1. Initiate the Google Cloud authorization for VMs
         ```bash
gcloud auth login
            ```

      2. You will be prompted to continue. Type `Y` to continue.
      3. Copy the link provided into the web browser that you are using. You will then be prompted to log in with your Google account. Follow instructions to copy the authorization code.
      4. Paste the authorization code in the SSH-in-browser window and hit enter. Retry the copy statement above to confirm that it worked.