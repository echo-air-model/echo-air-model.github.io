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
To download the test data, you can download individual files from [Google Drive](https://drive.google.com/drive/folders/1ZVSBrdjzqTG2nKnZdYLEmAaPGk25Bcq9?usp=drive_link). 

If you need to copy the test data directly from Google Drive to your Linux terminal, you can use the following commands following the same procedure as was done when [copying data](https://echo-air-model.github.io/docs/getting_started/copy_data.html). 


```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=15_WlRZMyYqTExFcEBSYVdPx0RyFjvl89' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=15_WlRZMyYqTExFcEBSYVdPx0RyFjvl89" -O demo_2000_data.cpg && rm -rf /tmp/cookies.txt
   ```

```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1UsGlA0Xelvl9kM4Gq8Vc51pPJXLGtzbQ' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1UsGlA0Xelvl9kM4Gq8Vc51pPJXLGtzbQ" -O demo_2000_data.dbf && rm -rf /tmp/cookies.txt
   ```

```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1DgFLHEeIP43KGSRrF0PPkG4n8Itg6GOI' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1DgFLHEeIP43KGSRrF0PPkG4n8Itg6GOI" -O demo_2000_data.prj && rm -rf /tmp/cookies.txt
   ```

```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=18VBrp5Ou2fupZc2K0NlO0j87UPrbGBNn' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=18VBrp5Ou2fupZc2K0NlO0j87UPrbGBNn" -O demo_2000_data.shp && rm -rf /tmp/cookies.txt
   ```

```bash
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1GN82sDZdlOi4gLnbO63nIv9RTT6rzN75' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1GN82sDZdlOi4gLnbO63nIv9RTT6rzN75" -O demo_2000_data.shx && rm -rf /tmp/cookies.txt
   ```
