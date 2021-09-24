# cheap-chinese-bluetooth-dongles-on-ubuntu-18.04
- a repo where I make notes to myself. i didnt code a driver xd xd

### introduction
- Ubuntu 18.04 officially not supports all realtek bluetooth chips.
- We need a driver for support.

- this manifacturer from china, created linux drivers for all realtek chips with bh456a.
- Links : https://www.xmpow.com/products/mpow-bh456a-bluetooth-5-0-usb-adapter-for-pc, https://www.xmpow.com/pages/download
- follow readme instructions.
- it wont work on the first try.(18.04, 5.4.101)
- need to install pulseaudio-module-bluetooth package.

### fix pulse
```
sudo apt-get purge --autoremove alsa-base pulseaudio
sudo apt-get install alsa-base bluetooth bluedevil pulseaudio plasma-pa module-bluetooth-discover
sudo systemctl enable bluetooth
sudo systemctl start bluetooth
sudo systemctl status bluetooth
bluetoothctl scan on
pair XXXX(mac)
connect XXXX(mac)
```
### get device inf, errors
```
lspci -nnk | grep -iA2 net; lsusb; dmesg | egrep -i 'blue|firm'; lsmod | grep blue
hciconfig -a
modinfo btrtl
dmesg | grep -i blue
```
