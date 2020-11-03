## Purpose
The purpose of this fork is to strip all button (pushbutton and rotary encoder) functionality from original Volumio-OledUI, retaining only display functionality.
Convenient for next level of DYIing of Volumio player.

## Hardware
* Raspberry Pi 2B/3B with Volumio2 image
* 256x64 Pixels 4-wire SPI OLED Display with SSD1322 controller IC (e.g. ER-OLEDM032-1W)


## Dependencies
* [socketIO-client](https://pypi.org/project/socketIO-client/)
* PIL
* [luma.oled](https://luma-oled.readthedocs.io/)

## Install
get [ssh access to Volumio](https://volumio.github.io/docs/User_Manual/SSH.html), login
and
enable SPI bus by adding
```
dtparam=spi=on
```
to /boot/userconfig.txt

### installation steps
```
sudo apt-get update
sudo apt-get install -y python-dev python-pip libfreetype6-dev libjpeg-dev build-essential python-rpi.gpio
sudo pip install --upgrade pip wheel
sudo pip install --upgrade setuptools
sudo pip install --upgrade socketIO-client luma.core==1.8.3 luma.oled==3.1.0
git clone https://github.com/isoniks/volui.git
chmod +x ~/volui/oledui.py
sudo cp ~/volui/oledui.service /lib/systemd/system/
sudo systemctl daemon-reload
sudo systemctl enable oledui.service
reboot
```

### how to check the logs
```
sudo journalctl -fu oledui.service
```
## Credits & Kudos
Thanks to following folks for their great projects:
[diehardsk](https://github.com/diehardsk/Volumio-OledUI)
[Maschine2501](https://github.com/Maschine2501/NR1-UI)
