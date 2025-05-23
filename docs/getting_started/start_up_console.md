---
layout: default
title: 1. Start Up Console
parent: Getting Started
nav_order: 2
---

## 1. Start Up Console

To begin the set-up, start up the console on [Mac](https://echo-air-model.github.io/docs/getting_started/start_up_console.html#mac), [WSL](https://echo-air-model.github.io/docs/getting_started/start_up_console.html#wsl), [Google Cloud](https://echo-air-model.github.io/docs/getting_started/start_up_console.html#google-cloud), or [Savio](https://echo-air-model.github.io/docs/getting_started/start_up_console.html#savio).


### Mac
The following instructions start up the Terminal and navigate to a working directory (`[working-directory]`) that is assumed to exist on your machine  at the path `[your/file/path]`. You can create the file path using your typical Mac file navigation.

1. Open a Terminal window by searching for it in the Finder.
2. Navigate to your working directory by typing:
```bash
cd [your/file/path]  
```

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/download_packages_and_model.html)

----

### WSL
The following instructions start up the Ubuntu console and navigate to a working directory (`[working-directory]`) path that is assumed to exist on your machine at the path `[your/file/path]`. You can create the file path using your typical windows file navigation.

1. Launch Ubuntu and log in, if needed.

2. Ubuntu will use your native Windows file system, but it may be blocked at first. First try:
```bash
cd ../../mnt/c/users/[your_name]/[your/file/path] 
```
If this works, skip to step 5.

3. If the native Windows file system is blocked, run the following commands in your home directory:
```bash
sudo umount /mnt/c 
sudo mount -t drives C: /mnt/c -o metadata
 ``` 

4. Navigate to your C-drive and to the file path you have created as your working directory:
```bash
cd ../../mnt/c/users/[your_name]/[your/file/path] 
``` 

5. Update the privileges of the working directory.
```bash
cd ..
chmod 777 [working-directory]
cd [working-directory]
``` 

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/download_packages_and_model.html)

----

### Google Cloud
The following instructions assume that the model should be copied into your home folder on your Google Cloud Console.

1. On the Compute Engine tab of the Google Cloud console, click the “SSH” button on your VM instance. This should pop up an SSH-in-browser window.

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/download_packages_and_model.html)

----

### Savio
...

[-- Next Step -->](https://echo-air-model.github.io/docs/getting_started/download_packages_and_model.html)
