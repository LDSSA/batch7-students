# Set-up instructions for Windows 10/11

Welcome to **Windows 10/11 set up** guide!

Your first step in this journey is to **carefully read** the steps in this tutorial. You'll learn how to set up your computer. This section deals with setting up `Windows Subsystem for Linux` (WSL) on Windows 10/11. `Windows Subsystem for Linux (WSL)` enables you to run Linux command line inside Windows.

**Step 1:** Follow **[this guide](Windows_Subsystem_for_Linux_Installation_Guide_for_Windows_10.md)** to setup `WSL` on Windows 10/11.

**Step 2:** Open a terminal (remember **[this](Windows_Subsystem_for_Linux_Installation_Guide_for_Windows_10.md#5-opening-the-wsl-terminal)**!!) and run the following command. It will install `git`. `Git` is a version control software that facilitates collaboration of people working together on the same code and keeps track of the versions as the code changes. You will learn more about `git` in Week 02 of this course.

```bash
sudo apt update && sudo apt upgrade && sudo apt install git
```

**Step 3:** Open a terminal (remember **[this](Windows_Subsystem_for_Linux_Installation_Guide_for_Windows_10.md#Opening-the-WSL-terminal)**!!) and confirm that you have `python3.10` with the command:

```bash
python3.10 --version
```

then install libraries necessary for the installation of the virtual environment: 

```bash
sudo apt install libpython3-dev

```

**Step 4** Run the following command to get `pip` and `venv`. `pip` is a package manager - it will help you easily install software. `venv` is a software for creating virtual environments (we will come back to what this means in the next set up step):

```bash
sudo apt update && sudo apt upgrade && sudo apt install python3-pip python3.10-venv -y
```
And you're done! Go back to the main menu and continue with setting up Git and GitHub in step 3.
