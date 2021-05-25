Intro
=====

Simple, low effort PAM module to use a bluetooth device to authenticate. No security implications have been considered. Tested on Fedora 34. 

The device needs to be paired for this module to work. The module will be ignored if the device is not found, and other authentication method can be used. 

Improvements are welcome.

Usage
-----
Enter the MAC address of the device within the double quotes on line 16 of pam_bluetooth.c

Build the module using the following commands.

`gcc -fPIC -fno-stack-protector -c pam_bluetooth.c`

`sudo ld -x --shared -o /lib64/security/pam_bluetooth.so pam_bluetooth.o`

Add the following line at the top of the relevant config files in /etc/pam.d to use the module to authenticate.

	auth sufficient pam_bluetooth.so

For eg. /etc/pam.d/gdm-password for gdm lockscreen, /etc/pam.d/sudo for sudo.
