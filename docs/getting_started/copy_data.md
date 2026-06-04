---
layout: default
title: 4. Copy Data
parent: Getting Started
nav_order: 5
---

## 4. Copy Data

Now we will copy over the necessary data for running the pipeline. The required data files are stored in Amazon Web Services and linked on the [ECHO-AIR Data Files](https://echo-air-model.github.io/docs/getting_started/data_files.html) page. Note that the default data assumes you are trying to run the model for California. The model has not yet been validated for other ISRMs. 

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

3. Download those files and save them to the "data" folder that you created. Note that you should preserve the structured sub-directory "CA_ISRM" if you intend to use the California ISRM. Verify that there are fifteen NumPy files labeled with .npy extension in the 'CA_ISRM' directory, and ensure that each file is approximately 1.88 GB in size.

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/test_setup.md)

----

### WSL

1. Within the `echo_air` folder in your File Explorer, open the folder called "data".

2. On your internet browser, navigate to the Google Drive link above.

3. Download those files and save them to the "data" folder that you created. Note that you should preserve the structured sub-directory "CA_ISRM" if you intend to use the California ISRM. Verify that there are fifteen NumPy files labeled with .npy extension in the 'CA_ISRM' directory, and ensure that each file is approximately 1.88 GB in size.

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/test_setup.md)

----

### Google Cloud

1. On your internet browser, navigate to the Google Drive link above.

2. Download those files to your local machine. Note that you should preserve the structured sub-directory "CA_ISRM" if you intend to use the California ISRM. Verify that there are fifteen NumPy files labeled with .npy extension in the 'CA_ISRM' directory, and ensure that each file is approximately 1.88 GB in size.

3. On the Google Cloud Platform, navigate to the storage bucket that you are using for this project. 

4. Create a folder within the bucket called "data" and upload all of the files you just downloaded by clicking and dragging.

5. Go back to your SSH-in-browser window.

6. Make sure you are located in the `echo_air/data` folder.

7. Run the following command to authorize data transfers. Follow instructions as prompted.
   ```bash
   gcloud auth login
   ```

9. Run the following code using the name of the bucket you created as `[bucket_name]`:
   ```bash
   gsutil cp -r gs://[bucket_name]/data .
   ```

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/test_setup.md)

----

### Savio

...

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/test_setup.md)
