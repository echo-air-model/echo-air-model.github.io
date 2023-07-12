---
layout: default
title: Sample Test Data
parent: Running the Model
nav_order: 2
---

## Sample Test Data

To practice running ECHO-AIR, we have developed a set of test data to practice with. The test data represent on-road mobile emissions from calendar year 2000 from the California Air Resource Board EMFAC2017 model.

It is recommended that you do not save the test data to the same data folder inside the tool repository.

### Accessing the Test Data
To download the test data, you can download individual files from [Google Drive](https://drive.google.com/drive/folders/1V0H_JLPpnWvqUfcADPi0JI_kd71Shbxm). 

If you need to copy the test data directly from Google Drive to your Linux terminal, you can use the following commands following the same procedure as was done when [copying data](https://echo-air-model.github.io/docs/getting_started/copy_data.html). 


```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1A42rTIzwXr31RoUlD_lABC6qjcMctf8_' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1A42rTIzwXr31RoUlD_lABC6qjcMctf8_" -O demo_2000_data.cpg && rm -rf /tmp/cookies.txt
   ```

   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1qNZEuG1JsgbtBNOQB7zNuIsQ3IH1WCeW' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1qNZEuG1JsgbtBNOQB7zNuIsQ3IH1WCeW" -O demo_2000_data.dbf && rm -rf /tmp/cookies.txt
      ```

   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1a1X2WCASnHPXtkjWwi5aVtERR_0jZT18' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1a1X2WCASnHPXtkjWwi5aVtERR_0jZT18" -O demo_2000_data.prj && rm -rf /tmp/cookies.txt
      ```

   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1FyPWQXGK5vhegx0kf_Eu_KBAMnzqZCWR' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1FyPWQXGK5vhegx0kf_Eu_KBAMnzqZCWR" -O demo_2000_data.shp && rm -rf /tmp/cookies.txt
      ```

   ```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1EzWn8Ozb8ka5T0YniVjMGZEUKuLGmsWn' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1EzWn8Ozb8ka5T0YniVjMGZEUKuLGmsWn" -O demo_2000_data.shx && rm -rf /tmp/cookies.txt
      ```