## Programmes to install on Linux

Here's some ideas of interesting and useful utilities to install on new set-ups.

You should be able to install them all at once in one long command if you wish:

eg

``sudo apt install neofetch tlp keepassxc cmus mpv``


### Neofetch

Neofetch is a command-line system information tool.  
https://github.com/dylanaraps/neofetch  


### TLP

Command-line tool that saves and optimizes laptop battery power on Linux and allows ThinkPads to set battery charge threshold.  
https://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html  
https://wiki.archlinux.org/index.php/TLP  

### KeePassXC

KeePassXC is a cross-platform open-source password manager.  
https://keepassxc.org/  
https://wiki.archlinux.org/index.php/KeePass  
https://en.wikipedia.org/wiki/KeePassXC  

Install on Arch/Manjaro:

`sudo pacman -S keepassxc`


### Telegram

https://telegram.org/

Messenger



### Signal

https://www.signal.org/

Messenger

To install Signal on Debian-based Linux:

```
curl -s https://updates.signal.org/desktop/apt/keys.asc | sudo apt-key add -
echo "deb [arch=amd64] https://updates.signal.org/desktop/apt xenial main" | sudo tee -a /etc/apt/sources.list.d/signal-xenial.list
sudo apt update && sudo apt install signal-desktop
```


### Cmus

cmus is a small, fast and powerful console music player for Unix-like operating systems.  
https://github.com/cmus/cmus  
https://wiki.archlinux.org/index.php/Cmus  


### mpv

https://wiki.archlinux.org/index.php/Mpv

mpv is a media player based on MPlayer and the now unmaintained mplayer2. It supports a wide variety of video file formats, audio and video codecs, and subtitle types

### Handbrake
https://handbrake.fr/

### MakeMKV
https://www.makemkv.com/  
https://www.makemkv.com/forum/viewtopic.php?f=3&t=224


### Atom

Text editor

### SublimeText
https://www.sublimetext.com/

using pacman (Arch / Manjaro)

Install instructions found here:
https://www.sublimetext.com/docs/3/linux_repositories.html#pacman

Install the GPG key: 
 
`curl -O https://download.sublimetext.com/sublimehq-pub.gpg && sudo pacman-key --add sublimehq-pub.gpg && sudo pacman-key --lsign-key 8A8F901A && rm sublimehq-pub.gpg`

add Stable channel:

`echo -e "\n[sublime-text]\nServer = https://download.sublimetext.com/arch/stable/x86_64" | sudo tee -a /etc/pacman.conf`

Update pacman and install Sublime Text

`sudo pacman -Syu sublime-text`





Text editor

### Visual Studio Code
https://code.visualstudio.com/

Text editor



## Alternatives

### Bitwarden

An alternative free and open-source password manager to consider.  
https://bitwarden.com/  
https://en.wikipedia.org/wiki/Bitwarden  
https://github.com/bitwarden  


## Pre-installed Apps

These programmes ship with most Linux distros (eg. Pop!_OS)



### Firefox

#### Firefox extensions

- [Pocket](https://getpocket.com/firefox/) (pre-installed) save articles to read later
- [uBlock Origin](https://addons.mozilla.org/en-GB/firefox/addon/ublock-origin/) block adverts
- [OneTab](https://addons.mozilla.org/en-GB/firefox/addon/onetab/) easily save all open tabs 
- [The Camelizer](https://addons.mozilla.org/en-GB/firefox/addon/the-camelizer-price-history-ch/) Amazon price history from CamelCamelCamel
- [KeePassXC-Browser](https://addons.mozilla.org/en-GB/firefox/addon/keepassxc-browser/) auto-fill passwords from your KeePassXC database
- [DuckDuckGo](https://addons.mozilla.org/en-US/firefox/addon/duckduckgo-for-firefox/) switch default search engine from Google to DDG

### VLC

https://www.videolan.org/vlc/
https://wiki.archlinux.org/index.php/VLC_media_player

VLC Media Player will play pretty much all video and audio files you throw at it



## Other random things to maybe install

`sudo apt install mesa-utils`
to allow glxgears to run

`sudo apt install obs-studio`
OBS - to screen record and create YouTube tutorials

### GNOME Tweak Tool  
https://wiki.gnome.org/Apps/Tweaks  
`gnome-tweak-tool`

- Dash to Dock
https://support.system76.com/articles/dash-to-dock/


