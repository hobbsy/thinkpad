## TLP

Notes on installing and running TLP on ThinkPad T440p, following along with this YouTube tutorial by DorianDotSlash: https://www.youtube.com/watch?v=Ku0491LfhR4


Install TLP  
`sudo apt install tlp`

Check that it's running:  
`sudo systemctl status tlp`

By default it's not automatically running, so either reboot your machine or run the command:  
`sudo systemctl start tlp`

To get some stats outputted in the terminal:  
`sudo tlp-stat -s`

or save the result of that to a text/log file if you want  
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

to show all the power settings:

`sudo tlp-stat`

`sudo tlp-stat >> "$(date +"%Y%m%d-%H%M")-tlp-stat.log"`

to just show temperature:  

`sudo tlp-stat -t`

to just show processor info:  

`sudo tlp-stat -p`

to show battery info:

`sudo tlp-stat -b

`sensors`

doesn't work for me by default, so can be installed with:  

`sudo apt install lm-sensors`

`sensors >> "$(date +"%Y%m%d-%H%M")-sensors.log"`

`watch sensors`

show sensors output every 2 seconds

`watch sudo tlp-stat -b`

