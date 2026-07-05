# K2 Improvements

TL:DR : Updates Fluidd and Moonraker to more current versions, makes Camera work in Fluidd, implements SCREWS_TILT_CALCULATE, and more.
None of this is my work besides fixing "screws_tilt_adjust.cfg" for the K2-Pro.
I cut out alot of the "fluff" that either doesnt work with the Pro or stuff I wont use.

## Live Component Status vs Mainline

[![Fluidd](https://img.shields.io/badge/dynamic/json?url=https://api.github.com/repos/fluidd-core/fluidd/compare/develop...Jacob10383:fluidd:k2&query=$.behind_by&label=Fluidd&suffix=%20commits%20behind&color=blue&style=for-the-badge&logo=github)](https://github.com/Jacob10383/fluidd/tree/k2)  
![Fluidd Last Update](https://img.shields.io/badge/dynamic/json?url=https://gist.githubusercontent.com/Jacob10383/f94d1bab6f84f53cd0a88e33c528d196/raw/fluidd-last-update.json&query=$.date&label=Last%20Synced&style=flat-square&color=gray)

[![Moonraker](https://img.shields.io/badge/dynamic/json?url=https://api.github.com/repos/Arksine/moonraker/compare/master...jacob10383:moonraker:k2&query=$.behind_by&label=Moonraker&suffix=%20commits%20behind&color=blue&style=for-the-badge&logo=github)](https://github.com/jacob10383/moonraker/tree/k2)  
![Moonraker Last Update](https://img.shields.io/badge/dynamic/json?url=https://gist.githubusercontent.com/Jacob10383/f94d1bab6f84f53cd0a88e33c528d196/raw/moonraker-last-update.json&query=$.date&label=Last%20Synced&style=flat-square&color=gray)

*Tracks - [@Jacob10383](https://github.com/Jacob10383) forks vs upstream as updates happen there, not by [@Jacob10383](https://github.com/Jacob10383).*

## Firmware

**Firmware Tested: V1.1.6.3** 

## DISCLAIMER

Use at your own risk, I'm not responsible for fires or broken dreams.  But you do get to keep both halves if something breaks.

## Warning

As a *heads up* these improvements are not compatible with Creality's *auto-calibration*.  In our experience we get better results through manual tuning.

## Start Here at Bootstrap

The Bootstrap is a requirement for the improvements to install properly, so this must be accomplished first. Of note, it will install entware tools necessary to accomplish the installs. Additionally, root is enabled by default with the password: 'creality_2024'. At some point, we recommend running command 'passwd' in the terminal to change the defualt password to something secure.

It is recommend to perform a factory reset prior to install to avoid potential conflicts with previous modifications.  A factory reset can be achieved with the following command in a terminal on the K2:

```raw
echo "all" | /usr/bin/nc -U /var/run/wipe.sock
```

1. Enable root access on the K2 Plus by going to Settings, General tab and root on the physical screen. Take note of the password.
1. Download the latest bootstrap release from [https://github.com/kern2011/k2_pro-improvements/releases](https://github.com/kern2011/k2_pro-improvements/releases) and extract the folder.
1. To install the bootstrap, connect to your K2 Plus's Fluid interface via browser **<http://PrinterIP:4408>**
1. Unzip the downloaded bootstrap folder and upload the extracted bootstrap folder by going to Configuration **{...}**, **+**, **Upload Folder**, and selecting the extracted bootstrap folder.
    ![image](https://github.com/user-attachments/assets/3d242efc-4cf8-412d-b4b0-59507720f5ad)
1. SSH to the K2 Plus using any terminal tool (e.g. PuTTy) using the printers ip adress, port 22, user "root" and the password noted in step 1.
1. If you execute a wipe, you will need to go through setup on the K2 screen and complete all the way through creality cloud connection. This will give you the wifi/network connection that you will need and connect appropriately to creality cloud. Stop at the calibration, you can do this later.
1. To start the boostrap install paste into the terminal `sh /mnt/UDISK/printer_data/config/bootstrap/bootstrap.sh` and hit enter.
1. Once the setup completes, it will log you out of your terminal and you will need to log back in.

## Installers

For now each feature can be found under the [features](./features/) directory.  A `README.md` and installation script `install.sh` are provided for each option.

The unified installer will understand inter option dependencies and ensure they are met.

Recomended installation:   **Note this will take some time and seem to hang at times. Be patient as it is moving lots of files and creating venvs for klipper and moonraker full installs

    To run, use the terminal command `sh /mnt/UDISK/root/k2-improvements/recommended.sh`

You are still welcome to hand pick which features you want to install.

## Edit printer.cfg

printer.cfg needs: [include custom/main.cfg]

## Power cycle your Printer!

Some funny stuff and errors happened to me trying to home the printer before a power cycle... Restarting host, or just restarting services is not enough.

## Donations For - [@Jacob10383](https://github.com/Jacob10383)

Donations are definitely *not required*, they are appreciated.  If you'd like to donate you can do so [here](https://ko-fi.com/jacob10383).

## Features

- [better init](./features/better-init/README.md)
- [better root](./features/better-root/README.md) home directory
- installs [Entware](https://github.com/Entware/Entware)
- updated [Fluidd](./features/fluidd/README.md)
- updated [Moonraker](./features/moonraker/README.md)
- implements [SCREWS_TILT_CALCULATE](https://www.klipper3d.org/Manual_Level.html#adjusting-bed-leveling-screws-using-the-bed-probe)

## Credits

- [@Jacob10383](https://github.com/Jacob10383)
- [@Guilouz](https://github.com/Guilouz) - standing on the shoulders of giants
- [@stranula](https://github.com/stranula)
- [@juliosueiras](https://github.com/juliosueiras)

- Moonraker - [https://github.com/Arksine/moonraker](https://github.com/Arksine/moonraker)
- Klipper - [https://github.com/Klipper3d/klipper](https://github.com/Klipper3d/klipper)
- Fluidd - [https://github.com/fluidd-core/fluidd](https://github.com/fluidd-core/fluidd)
- Entware - [https://github.com/Entware/Entware](https://github.com/Entware/Entware)
- Obico - [https://www.obico.io/](https://www.obico.io/)
- SimplyPrint - [https://simplyprint.io/](https://simplyprint.io/)

## FAQ

See the [FAQ](./FAQ.md)
