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

# Project Overview

The objective of this project is to use a relatively old android device to serve as a home assistant server.

Due to its age the tablet was experiencing problems with it's battery including invalid battery percentage which then cause power offs even when showing the battery at 60%. 
By converting the tablet to act as home assistant server, the tablet will be functional again and constantly charging eliminating the risk of shutting down. 

Hardware and Software:

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
# QEMU Installation
Qemu stands for quick emulator and enables the device to function as a standalone emulator or work with a hypervisor like KVM.

Qemu has been used as it is an open source emulator and allows for the installation of Alpine Linux.

Installation
```bash
PKG install qemu-system-x86_64
```

Once qemu was installed, Alpine Linux iso was downloaded using wget and the disk image was created to be used for the creation of the Virtual Alpine Environment.

The Qemu VM was setup with the following parameters:
* Memory: 512M
* Cores: 5

The system was booted, Alpine Linux installation took place and and Alpine Linux was ready to be used.
# Home Assistant Setup
In order to setup home assistant server, the only lightweight option was via docker. 

Docker was installed and a container was created to host the home assistant server. 

Home Assistant inside the container was configured to use the local configuration file previously created and always restart unless explicitly terminated.
# Access Control
An account was created for each user in order to allow access to the members. Only one account was set to have administrator access and rights to ensure only authorized changes are made, maintaining system security and minimizing the risk of accidental or malicious modifications.

This approach aligns with the principles outlined in NIST Cyber security Framework such as the Least Privilege Principle, giving users minimum access to only perform their tasks and reduce attack surfaces.
# Future Improvements
* Home Assistant should be accessible from outside the local network. 
  - A future improvement would be to setup a secure VPN connection to the router enabling users to access Home Assistant from outside the network. In order to achieve this, the network provider would need to switch to IPv6 as its currently using CGNAT making it impossible to access the router using it's public IPv4 address.
* Ensure regular back ups and cloud back up automation for easy recovery in case of system failure.
* Ensure regular updates to address know vulnerabilities and allow compatibility with new integrations.
* Create customized dashboards for each user and device-specific views.

# Overcoming CGNAT

As previously mentioned, accessing Home Assistant outside the local network was impossible due to the internet provider using CGNAT which is a convenient way of handling multiple IP addresses grouping them together into 1 and minimizing the number of IPv4 addresses they need to buy or rent.
It's also worth mentioning that even though the home router had the ability to setup a secure virtual network for different users, it was impossible to access it outside of the local network. In order to test this, an account was created specifically for this purpose. The relevant information were entered into the android device including protocols used and pre-shared keys. Through testing, it was identified that locally activating the VPN shown the device being connected and the router indicating a new virtual IP for the user. However, when switching to 5G or external network, the VPN connection couldn't be established indicating once again the limitations of CGNAT.

In order to bypass CGNAT, research was conducted to identify alternatives that could be used in such cases while also maintaining network security. An application called Tailscale was found and explored. This application enabled the device inside the network running Home Assistant to make a connection with a public server. After creating an account, the android application was installed enabling the tablet to be listed as a device. On another device, Tailscale was activated and similarly to a VPN, a connection was established to the public server revealing the IPv4 address of the tablet hosting Home Assistant.

Now, using the Home Assistant application on a personal device, 2 IP addresses could be entered. One for accessing Home Assistant locally and an external IP address for accessing Home Assistant while being away from the home network. The external IP address was generated from Tailscale illustrating that in order to access Home Assistant the user needs to either be in the local network or enabling the VPN via the Tailscale application and then opening the app to access the Home Assistant.

All in all, connection to the Home Assistant was established and the CGNAT of the internet provider was bypassed, enabling access to Home Assistant wherever the user might be.
