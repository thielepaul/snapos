# SnapOS
Snapcast OS is a [Buildroot](https://buildroot.org) based embedded [Linux](https://www.kernel.org) OS for [Snapcast](https://github.com/badaix/snapcast).
There will be configurations for some boards, e.g. the Raspberry Pi 3 with WiFi and audio enabled, as well as packages for Snapcast and its dependencies.

## How-to
 1. [Download](https://buildroot.org/download.html) or [clone](https://github.com/buildroot/buildroot) [Buildroot](https://buildroot.org) 
 2. Clone SnapOS to some directory
 3. Navigate into Buildroot's root directory and define SnapOS as an [external](https://buildroot.org/downloads/manual/manual.html#outside-br-custom):
```
buildroot-2017.11.2 $ make BR2_EXTERNAL=/PATH/TO/snapos/buildroot-external/ snapos_rpi3_defconfig
```
 4. Now you will find the pre-selected `Snapclient` package under `External options  --->` in `make menuconfig`
```
    *** Snapcast OS (in /PATH/TO/snapos/buildroot-external) ***
[*] Snapcast
[*]   Snapclient
[ ]   Snapserver
-*- aixlog
-*- jsonrpc++
-*- popl
-*- asio
-*- libavahi-client
```
 5. Run `make`, wait, and find the image in `output/image/sdcard.img`
 6. Write the image to an sd card, e.g. (with `sdX` = your sd card's device name):
 ```
 buildroot-2017.11.2 $ sudo dd bs=4M if=output/images/sdcard.img of=/dev/sdX conv=fsync status=progress
 ```
 7. Boot your device. Snapclient will start automatically
 8. Ethernet is configured to use DHCP. Login with user `root` and password `snapcast`
 
