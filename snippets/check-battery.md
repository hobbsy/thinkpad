# How to check current battery capacity

To check the capacity (and current status) of your Lenovo ThinkPad battery you can use the following command:

(I'm testing this out initially on Pop!_OS distro (version 19.10) and a ThinkPad T440p, so will need to double-check it works on other set-ups)

`upower -d`

which gives lots of info on AC power, battery, display. Probably more than we require...

or more simply:

`upower -i /org/freedesktop/UPower/devices/battery_BAT0`

Which gives me the result:

```
  native-path:          BAT0
  vendor:               SANYO
  model:                45N1779
  serial:               1093
  power supply:         yes
  updated:              Sat 01 Feb 2020 23:43:05 GMT (29 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    warning-level:       none
    energy:              98.46 Wh
    energy-empty:        0 Wh
    energy-full:         98.46 Wh
    energy-full-design:  99.47 Wh
    energy-rate:         6.49 W
    voltage:             12.375 V
    percentage:          100%
    capacity:            98.9846%
    technology:          lithium-ion
    icon-name:          'battery-full-charged-symbolic'
```

This is an official Lenovo 57++ (9-cell battery) `SANYO 45N1779` that I picked up from eBay last week for ~£40.  

This battery when new is 99.47 Wh, and mine currently has a capacity of 98.46 Wh (98.9846% according to this report).  

It may also be of use to turn this info into a little script to save the results to a text file (and run it every hour from cron?)  

Maybe something like, 

`upower -i /org/freedesktop/UPower/devices/battery_BAT0 >> "$(date +"%Y%m%d-%H%M")-battery.log"`

I probably only need to grab a few of those figures like `energy`, `percentage`, `capacity`.  

This could maybe be hooked up to a Google Sheets spreadsheet and IFTTT.  

### Further Reading

Some helpful notes can be found on Pop!_OS's website  
https://support.system76.com/articles/battery/

>We recommend using TLP to quickly reduce overall power consumption and using powertop to check what software is consuming the battery

## TLP

`sudo apt install tlp tlp-rdw --no-install-recommends`

## PowerTop

`sudo apt install powertop`
