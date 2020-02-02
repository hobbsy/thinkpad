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


