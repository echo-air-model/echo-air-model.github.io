---
layout: default
title: 4. Copy Data
parent: Getting Started
nav_order: 5
---

## 4. Copy Data

Now we will copy over the necessary data for running the pipeline. The required data files are located on [Google Drive](https://drive.google.com/drive/folders/1UOONQ0aQ6y0vasRL47lDaJNZ9IJv-w5A?usp=sharing). Note that the default data assumes you are trying to run the model for California. The model has not yet been validated for other ISRMs. 

The recommended method for copying the data files varies by operating system. Follow the link below to view your specific instructions.

* [Mac](https://echo-air-model.github.io/docs/getting_started/copy_data.html#mac)
* [WSL](https://echo-air-model.github.io/docs/getting_started/copy_data.html#wsl)
* [Google Cloud](https://echo-air-model.github.io/docs/getting_started/copy_data.html#google-cloud)
* [Savio](https://echo-air-model.github.io/docs/getting_started/copy_data.html#savio). 
* [Direct to Terminal](https://echo-air-model.github.io/docs/getting_started/copy_data.html#direct-to-terminal): Use this method to copy files directly from Google Drive, regardless of operating system

----

### Mac

1. Within the `echo_air` folder in your Finder, open the folder called "data".

2. On your internet browser, navigate to the Google Drive link above.

3. Download those files and save them to the "data" folder that you created. Note that you should preserve the structured sub-directory "CA_ISRM" if you intend to use the California ISRM. Verify that there are five NumPy files labeled with .npy extension in the 'CA_ISRM' directory, and ensure that each file is approximately 5.65 GB in size.

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/copy_data.html#test-setup)

----

### WSL

1. Within the `echo_air` folder in your File Explorer, open the folder called "data".

2. On your internet browser, navigate to the Google Drive link above.

3. Download those files and save them to the "data" folder that you created. Note that you should preserve the structured sub-directory "CA_ISRM" if you intend to use the California ISRM. Verify that there are five NumPy files labeled with .npy extension in the 'CA_ISRM' directory, and ensure that each file is approximately 5.65 GB in size.

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/copy_data.html#test-setup)

----

### Google Cloud

1. On your internet browser, navigate to the Google Drive link above.

2. Download those files to your local machine. Note that you should preserve the structured sub-directory "CA_ISRM" if you intend to use the California ISRM. Verify that there are five NumPy files labeled with .npy extension in the 'CA_ISRM' directory, and ensure that each file is approximately 5.65 GB in size.

3. On the Google Cloud Platform, navigate to the storage bucket that you are using for this project. 

4. Create a folder within the bucket called "data" and upload all of the files you just downloaded by clicking and dragging.

5. Go back to your SSH-in-browser window.

6. Make sure you are located in the `echo_air/data` folder.

7. Run the following command to authorize data transfers. Follow instructions as prompted.
   ```bash
gcloud auth login
      ```

8. Run the following code using the name of the bucket you created as `[bucket_name]`:
   ```bash
gsutil cp -r gs://[bucket_name]/data .
      ```

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/copy_data.html#test-setup)

----

### Savio

...

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/copy_data.html#test-setup)

----

### Direct to Terminal

The following code will copy the data directly from Google Drive to the ECHO-AIR model directory.

1. In your terminal, create a directory inside the `echo_air` directory called data and navigate to it:
   ```bash
mkdir data
cd data
      ```

2. Install the `wget` function.
   ```bash
sudo apt-get install wget
      ```

3. Copy the following commands and run them in your terminal.
   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1DqUqxafrIG8GAkWhELOQ5fyQzU9FW5_G' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1DqUqxafrIG8GAkWhELOQ5fyQzU9FW5_G" -O air_basins.feather && rm -rf /tmp/cookies.txt
      ```
   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=14pfebDkTwvjchByUEleBEIln0GWU8D3h' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=14pfebDkTwvjchByUEleBEIln0GWU8D3h" -O air_districts.feather && rm -rf /tmp/cookies.txt
      ```
   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1OEW230YjqlP4RTmEy7PojWdAssPe2mWZ' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1OEW230YjqlP4RTmEy7PojWdAssPe2mWZ" -O benmap_incidence.feather && rm -rf /tmp/cookies.txt
      ```
   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1wi010o5Wr98W0M4IQrhChJjEEvpnwmR2' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1wi010o5Wr98W0M4IQrhChJjEEvpnwmR2" -O ca_border.feather && rm -rf /tmp/cookies.txt
      ```
   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1m-C6EnQ_esdATLwU_vTMll5s5Wv5RJ6M' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1m-C6EnQ_esdATLwU_vTMll5s5Wv5RJ6M" -O ca2010.feather && rm -rf /tmp/cookies.txt
      ```
   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1NJsByx_YgMZtl2BdwJW6ULsjtE2Tnlco' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1NJsByx_YgMZtl2BdwJW6ULsjtE2Tnlco" -O counties.feather && rm -rf /tmp/cookies.txt
      ```

4. Create a sub-directory called "CA_ISRM" and navigate to it.
   ```bash
mkdir CA_ISRM
cd CA_ISRM
      ```

5. Copy the following commands to copy the data directly from Google Drive. Note: these may take a few minutes each, as these are very large files.
   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1fzYgvojGrkWpeDg09smNzCGuV8-P0xzz' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1fzYgvojGrkWpeDg09smNzCGuV8-P0xzz" -O isrm_geo.feather && rm -rf /tmp/cookies.txt
      ```
   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1I4CC88ykpE_WzdjUEry35pqsBE6Aaaex' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1I4CC88ykpE_WzdjUEry35pqsBE6Aaaex" -O ISRM_NH3.npy && rm -rf /tmp/cookies.txt
      ```
   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1mneFJEfsGKLIz4xzGEcVVLFW_C7y7ynd' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1mneFJEfsGKLIz4xzGEcVVLFW_C7y7ynd" -O ISRM_NOX.npy && rm -rf /tmp/cookies.txt
      ```
   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1O6GPVjLuTnJUmdWM2lt3p4w9UCoRBiB3' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1O6GPVjLuTnJUmdWM2lt3p4w9UCoRBiB3" -O ISRM_PM25.npy && rm -rf /tmp/cookies.txt
      ```
   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1NkWjYPaB7JJMGzUKckG_LI1UWeZaEZza' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1NkWjYPaB7JJMGzUKckG_LI1UWeZaEZza" -O ISRM_SOX.npy && rm -rf /tmp/cookies.txt
      ```
   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1_owK9FszVIgQ2QICfLRCjIraJCf_hmb2' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1_owK9FszVIgQ2QICfLRCjIraJCf_hmb2" -O ISRM_VOC.npy && rm -rf /tmp/cookies.txt
      ```

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/copy_data.html#test-setup)

----

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



