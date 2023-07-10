---
layout: default
title: 1. Start Up Console
parent: Getting Started
nav_order: 2
---

## 1. Start Up Console

To begin the set-up, start up the console on Mac, WSL, Google Cloud, or Savio.


### Mac
The following instructions start up the Terminal and navigate to a working directory ([working-directory]) that is assumed to exist on your machine  at the path [your/file/path]. You can create the file path using your typical Mac file navigation.

1. Open a Terminal window by searching for it in the Finder.
2. Navigate to your working directory by typing:
   ```bash
      cd [your/file/path]  
      ```

----

### WSL
The following instructions start up the Ubuntu console and navigate to a working directory ([working-directory]) path that is assumed to exist on your machine at the path [your/file/path]. You can create the file path using your typical windows file navigation.

1. Launch Ubuntu and log in, if needed.
2. Ubuntu will use your native Windows file system, but it may be blocked at first. Run the following commands in your home directory:
   ```bash
      sudo umount /mnt/c 
      sudo mount -t drives C: /mnt/c -o metadata
      ``` 
{:style="counter-reset:step-counter 2"}
   3. Navigate to your C-drive and to the file path you have created as your working directory:
      ```bash
         cd ../../mnt/c/users/[your_name]/[your/file/path] 
      ``` 
   {:style="counter-reset:step-counter 3"}
      4. Update the privileges of the working directory.
         ```bash
            cd ..
            chmod 777 [working-directory]
            cd [working-directory]
         ``` 

----

### Google Cloud
On the Compute Engine tab of the Google Cloud console, click the “SSH” button on your VM instance. This should pop up an SSH-in-browser window.

----

### Savio
...
