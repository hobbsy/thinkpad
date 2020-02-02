## TLP

Notes on installing and running TLP on ThinkPad T440p

Check out this YouTube tutorial:
https://www.youtube.com/watch?v=Ku0491LfhR4


`sudo apt install tlp`

`sudo systemctl status tlp`

not automatically running so either reboot or run:

`sudo systemctl start tlp`

`sudo tlp-stat -s`

or save the result of that to a text/log file

`sudo tlp-stat -s >> "$(date +"%Y%m%d-%H%M")-tlp.log"`


`tlp-pcilist`

show all PCI devices, and whether control is 'on' or 'auto'

`tlp-usblist`

show all USB devices

`sudo tlp-stat -c`

shows entire configuration
default location for config file in Pop!_OS is  `/etc/default/tlp`

`sudo nano /etc/default/tlp`
to edit the config file

change from 1 to 0 for `SOUND_POWER_SAVE_ON_BATT` value. When on (1), this setting turns your sound card on and off, it apparently creates a pop noise when you start Firefox etc. YouTube tutorial recommends to turn it off (0). Maybe check to see if this is necesarry on Pop!_OS and T440p.

defaults were:
`SOUND_POWER_SAVE_ON_AC=0`
`SOUND_POWER_SAVE_ON_BAT=1`

save config file then restart

`sudo systemctl restart tlp`



