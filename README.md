# HomeTabX
Android Tablet Hosting Home Assistant

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
