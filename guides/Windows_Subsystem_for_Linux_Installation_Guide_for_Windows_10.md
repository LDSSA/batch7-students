# Windows Subsystem for Linux Installation Guide for Windows 10 and 11

## 1. Make sure that Windows is up to date

You must be running Windows 10 version 2004 and higher (Build 19041 and higher) or Windows 11 to use the commands below. If you are on Windows 10, follow this procedure to update your system:

1. Type `update` in your Windows search bar:

![start](../media/start.png)

then click `Check for Updates`:

![start](../media/open_update.png)

then download and install any updates that appear in the Windows Update menu (shown below):

![start](../media/windows_update.png)

After you're done installing those updates, please [check which OS build of Windows 10 you are running](https://support.microsoft.com/en-us/help/13443/windows-which-version-am-i-running). If your OS build number is smaller that `19041.XXX`, then please keep coming back to Windows Update and installing updates until you have at least OS build `19041.XXX`. Then you may proceed with this guide.

![start](../media/os_build.png)

## 2. Prepare Windows for WSL installation

Before installing any Linux distributions for WSL, you must ensure that the `Windows Subsystem for Linux` optional feature is enabled:

1. Open the `PowerShell` as Administrator by typing `PowerShell` in your Windows search bar...

![start](../media/start.png)

... and select `Run as Administrator`:

![start](../media/open_powershell.png)

2. Then paste the following command in `PowerShell`:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

![start](../media/paste_powershell.png)

and run it by pressing <kbd>Enter</kbd>:

3. Restart your computer if asked to.

## 3. Install WSL with Ubuntu 22.04

1. We are installing the latest Ubuntu version with preinstalled Python 3.10. Open the Power shell and run this: `wsl --install -d Ubuntu-22.04` or go to the [Microsoft Store](https://apps.microsoft.com/store/detail/ubuntu-22042-lts/9PN20MSR04DW) and select `Get` to install `Ubuntu 22.04`.

1. If you get the x80370102 error when installing WSL, go to [https://support.microsoft.com/en-us/windows/enable-virtualization-on-windows-11-pcs-c5578302-6e43-4b4b-a449-8ced115f58e1] and follow the steps, then try installing again.

## 4. Launch Ubuntu 22.04
To complete the initialization of your newly installed `Ubuntu 22.04`, launch a new instance. You can do this by typing `ubuntu` in your Windows search bar:

![start](../media/start.png)

![start](../media/open_ubuntu.png)

The first time the newly installed `Ubuntu 22.04` runs, a `Console` window will open, and you'll be asked to wait for a minute or two for the installation to complete.

> During this final stage of installation, `Ubuntu`'s files are de-compressed and stored on your PC, ready for use. This may take around a minute or more depending on the performance of your PC's storage devices. This initial installation phase is only required on the first launch - all future launches should take less than a second.

## 5. Setting up a new Linux user account

Once the installation is complete, you will be prompted to create a new user account (and its password).

![Ubuntu unpacking in the Windows console](../media/UbuntuInstall.png)

This user account is for the normal non-admin user that you'll be logged-in by default when launching `Ubuntu`.

> You can choose any username and password you wish - they have no bearing on your Windows username. Beware that when you type passwords in the terminal, you will not see what you are typing. This is a normal behaviour in Linux. Just type the password and hit <kbd>Enter</kbd>.

When you open a new `Ubuntu` instance, you won't be prompted for your password, but **if you elevate a process using `sudo`, you will need to enter your password**, so make sure you choose a password you can easily remember! On `Ubuntu`, every user can do admin tasks such as installing software, but they have to use the magic `sudo` word and input the password. This tells `Ubuntu` that you will be acting as admin in the next moments. 

## 5. Opening the WSL terminal

>⚠️ **Important**: From now on, every time we ask you to open a terminal, this is what you need to do. We'll refer to it just as `terminal` instead of `WSL terminal` or `Ubuntu terminal`.

Whenever you want to use WSL, just type `ubuntu` in your Windows search bar.

![start](../media/start.png)

Open it:

![start](../media/open_ubuntu.png)

Then a `terminal` window will open that allows you to interact with `Ubuntu`.

![Ubuntu unpacking in the Windows console](../media/orange_circle.png)

## 6. Enable copy and paste keyboard shortcuts

By default, the terminal does not allow the usual shortcuts for copying and pasting - you have to enable them first. In the upper left corner of the WSL terminal, click the orange circle:

![Ubuntu unpacking in the Windows console](../media/orange_circle.png)

then click `Properties`:

![Ubuntu unpacking in the Windows console](../media/orange_circle_properties.png)

Then under the `Options` tab, in the `Edit Options` section, make sure that `Use Ctrl+Shift+C/V as Copy/Paste` in enabled and click `OK`:

![Ubuntu unpacking in the Windows console](../media/copy_paste_properties.png)

## 7. Update & upgrade Ubuntu's software packages

Most Linux distributions ship with an empty/minimal software package catalog. We strongly recommend regularly updating your package catalog, and upgrading your installed packages using the appropriate package manager. On `Ubuntu`, you use the `apt` package manager. The following command will check for software updates and install them:

```bash
sudo apt update && sudo apt upgrade
```

> Windows does not automatically update or upgrade your Linux distribution. This is a task that the Linux users prefer to control themselves.

## 8. How to open Windows File Explorer to manipulate files inside WSL

If you’d like to use `Windows File Explorer` to manipulate the files in WSL, just type this in the `terminal`. **(Don't forget to include the dot! The dot means "current directory")**:

```console
explorer.exe .
```

The `Windows Explorer` should pop up:

![start](../media/windows_explorer.png)

Keep in mind that you should manipulate files and create directories inside your `Ubuntu-22.04/home/<your name>` folder.

You're all set with WSL! Now go back to the initial setup for Windows and continue with step 2.
