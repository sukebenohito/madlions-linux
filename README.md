#credit to DGTR 
(codeberg.org/DGTR/mad60he-linux/)(https://codeberg.org/DGTR/mad60he-linux/raw/branch/main/README.md)

# Device Access for Madlions Web Driver under Linux

## Overview of udev Rules

udev rules are Linux settings that control how devices, like keyboards or USB drives, are managed when connected. They define permissions and actions, ensuring only authorized users can access specific hardware.

## udev Rules for Madlions MAD60HE

To configure the Madlions MAD60HE keyboard, create a file named `70-madlions.rules` in the `/etc/udev/rules.d/` directory with the following content:

```
# Madlions udev rule

SUBSYSTEM=="hidraw", ATTRS{idVendor}=="373b", TAG+="uaccess"
SUBSYSTEM=="usb", ATTRS{idVendor}=="373b", TAG+="uaccess"
```

This must be done with root access since the `/etc/udev/` folder is write protected. The number in the `70-madlions.rules` decides the order of precedence of execution. So rules that are supposed to executed earlier will be named with a number less than 70. 



## Applying the udev rule

To apply the udev rule you can either : 

- Restart your PC
- Run a command to reload the udev rules


If you do not want to restart your PC for whatever reason then running this command will reload the rules. 

`` 
sudo udevadm control --reload-rules && sudo udevadm trigger
``
