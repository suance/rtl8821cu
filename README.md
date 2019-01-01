# rtl8821cu
Wifi driver for rtl8811cu/rtl8821cu with monitor mode

### DKMS
Automatically install a kernel module when a new kernel gets installed
```
sudo apt install dkms
```
### Install
```
sudo ./dkms-install.sh
```
### Remove
```
sudo ./dkms-remove.sh
```
### Modeswitch
Just modify the file */lib/udev/rules.d/40-usb_modeswitch.rules* appending before the line *LABEL="modeswitch_rules_end"* with:
```
# Realtek 8811CU/8821CU Wifi AC USB
ATTR{idVendor}=="0bda", ATTR{idProduct}=="1a2b", RUN+="/usr/sbin/usb_modeswitch -K -v 0bda -p 1a2b"
```
### Monitor mode
Use the tool 'iw', please don't use other tools like 'airmon-ng'
```
iw dev wlan0 set monitor none
```
