# HomeTabX
Android Tablet Hosting Home Assistant

<p align="center">
  <img src="https://github.com/user-attachments/assets/1eb697df-cb51-44ba-8eb3-2bbbe36653b6" width="200" height="200" />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://github.com/user-attachments/assets/1c46d25d-d03f-431b-bf8c-819d35365dee" width="200" height="200" />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://github.com/user-attachments/assets/7d4b9c43-c835-45e0-b535-0671b3e19ab8" width="200" height="200" />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://github.com/user-attachments/assets/a4225b95-a9f2-436e-9546-c0fad85cc82e" width="200" height="200" />
</p>

# Background Details
Tablet Model: Xiaomi Pad 4

Operating System: Android 9

# Termux Installation
Termux terminal emulator and Linux environment app had to be installed in order to allow the project to begin, giving a blank slate for the home assistant server. Due to android version, Termux was not available to be installed traditionally using the PlayStore. The alternative was to install Termux from F-Droid store. Once everything was installed, Termux was launched.

The repositories were upgraded using:
```bash
pkg update && pgk upgrade
```

Then proot needed to be installed
```bash
pkg install proot
``` 
Proot is a virtual environment that allows Linux distros to be installed and launched without the need to have root privileges. 
