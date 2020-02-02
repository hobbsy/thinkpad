# How to check current battery capacity

To check the capacity (and current status) of your Lenovo ThinkPad battery you can use the following command:

(I'm testing this out initially on a Pop!_OS distro (version 19.10) and a ThinkPad T440p laptop, so will need to double-check it works on other set-ups)

`upower -d`

which gives lots of info on AC power, battery, display etc. Probably more than we require...

To narrow it down to just the battery info we can use:

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

This is an official Lenovo 57++ (9-cell battery) `SANYO 45N1779` that I picked up from eBay for around £40.  

The battery when new out of the factory should be 99.47 Wh - mine currently has a capacity of 98.46 Wh (almost 99% according to this report - hopefully this is accurate).  

It may also be of use to turn this info into a little script to save the results to a text file (and run it every hour from cron?)  

Maybe something like, 

`upower -i /org/freedesktop/UPower/devices/battery_BAT0 >> "$(date +"%Y%m%d-%H%M")-battery.log"`

I probably only need to grab a few of those figures like `energy`, `percentage`, `capacity`

This could potentially be hooked up with IFTTT and a Google Sheets spreadsheet.  

## Battery History

Under the directory  

`/var/lib/upower`  

the historical data for your battery is saved.  

eg. I have these 4 files:  

```
history-charge-45N1779-99-1093.dat
history-rate-45N1779-99-1093.dat
history-time-empty-45N1779-99-1093.dat
history-time-full-45N1779-99-1093.dat
```


## Further Reading

Some helpful notes can be found on Pop!_OS's website and the Arch Wiki  

https://support.system76.com/articles/battery/

>We recommend using TLP to quickly reduce overall power consumption and using powertop to check what software is consuming the battery  

### TLP

`sudo apt install tlp tlp-rdw --no-install-recommends`

https://wiki.archlinux.org/index.php/TLP

>TLP brings you the benefits of advanced power management for Linux without the need to understand every technical detail. TLP comes with a default configuration already optimized for battery life, so you may just install and forget it. Nevertheless TLP is highly customizable to fulfill your specific requirements.  


### PowerTop

`sudo apt install powertop`

https://wiki.archlinux.org/index.php/Powertop

>Powertop is a tool provided by Intel to enable various powersaving modes in userspace, kernel and hardware. It is possible to monitor processes and show which of them are utilizing the CPU and wake it from its Idle-States, allowing to identify applications with particular high power demands.  

