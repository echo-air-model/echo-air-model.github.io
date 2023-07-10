---
layout: default
title: Linux Cheat Sheet
parent: Other Information
nav_order: 1
---

## Linux Cheat Sheet

Instructions in the documentation assume some knowledge of Linux commands. Any Linux command needed for setting up or running the tool can be found in the table below.

In the **Command** column, characters that are enclosed in parentheses are buttons (e.g., (Esc) is the escape key). Characters that are enclosed in a single quote are the command that should be typed. 

### Linux Commands for Navigating Directories

Regardless of operating system, there are a few commands that you will need to use to navigate directories to set up and run the model.

<table cellspacing="0" cellpadding="0">
  <tr>
    <th>Command</th><th>Usage</th><th>Example</th>
  </tr>
  <tr>
    <td>`mkdir` [name]</td><td>creates a new child directory in the current directory</td><td>`mkdir data` will make a directory called data </td>
  </tr>
  <tr>
    <td>`cp [filename] [destination]` </td><td>makes a copy of your file </td><td>`cp control_file.txt stack_data_control.txt` will make a copy of the control_file.txt file and name it stack_data_control.txt </td>
  </tr>
  <tr>
    <td>`pwd` </td><td>shows which directory you are currently in </td><td>`pwd` returns /home/koolik/isrm_health_calculations </td>
  </tr>
  <tr>
    <td>`ls` </td><td>shows all of the files in the current directory </td><td>`ls` will report a list of file names </td>
  </tr>
  <tr>
    <td>`cd` </td><td>changes directory</td><td>`cd data` will move into a child directory called "data" </td>
  </tr>
  <tr>
    <td>`cd ..` </td><td>moves upwards a directory (i.e., to the parent) </td><td>`cd ..` when in the home/data folder will go back up to the parent folder (home) </td>
  </tr>
 </table>

### Linux Commands for Editing Documents
If you are running the model on a remote Linux terminal (e.g., Google Cloud console), you will need to be able to edit documents through the terminal. 

<table cellspacing="0" cellpadding="0">
  <tr>
    <th>Command</th><th>Usage</th><th>Example</th>
  </tr>
  <tr>
    <td>`vi` [filename]</td><td>opens a document</td><td>`vi control_file.txt` will open the control file</td>
  </tr>
  <tr>
    <td>`i` </td><td>switches you into edit mode</td><td>`i` then add your edits where appropriate </td>
  </tr>
  <tr>
    <td>(`Esc`) + `:q`</td><td>closes a document</td><td>`:q` will close a document without changes</td>
  </tr>
   <tr>
    <td>(`Esc`) + `:wq`</td><td>closes a document</td><td>`:wq` will close a document with changes</td>
  </tr>
 </table>

### Other Useful Commands
There are a few other useful commands that are used throughout the documentation.

<table cellspacing="0" cellpadding="0">
  <tr>
    <th>Command</th><th>Usage</th><th>Example</th>
  </tr>
  <tr>
    <td>`sudo` [function]</td><td>allows a user to execute commands with superuser privileges</td><td>`sudo apt-get update` will enable a non-administrator to run the update function from the apt-get command </td>
  </tr>
  <tr>
    <td>`git pull origin` </td><td>synchronizes your version of the code with the online repository </td><td>`git pull origin` will make your local copy (i.e., on your machine) match the remote version on Github. This makes sure you're never out of date. </td>
  </tr>
</table>
