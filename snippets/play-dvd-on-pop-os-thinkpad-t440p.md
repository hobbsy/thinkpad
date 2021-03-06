# How to set-up DVD player on Pop!_OS 19.10 and ThinkPad T440p

Here are some notes for my own benefit (to remind me) on how to set up the DVD player

**work in progress**

I'm testing this out with DVD disc 1 of King Of The Hill season 2 boxset, a Region 2 PAL disc (which I picked up from a charity shop for 50p)

This isn't working under a vanilla Pop!_OS install... I will try and figure out how to fix it.

## Playing a DVD

To play a DVD on the T440p DVD-Rom drive using the `Videos` in-built app (aka Totem) on Pop!_OS 19.10, you might need to install extra multimedia plugins - eg.  
`gstreamer1.0-plugins-ugly` (this one is pre-selected)  

which installs:  
`libopencore-amrnb0 (0.1.3-2.1build1)`  
`libopencore-amrwb0 (0.1.3-2.1build1)`  
`libsidplay1v5 (1.36.59-11)`  

another plugin listed:
`gstreamer-1.0-plugins-bad`  

which installs:  
`libgupnp-igd-1.0.4 (0.2.5-3ubuntu1)`  
`timgm6mb-soundfont (1.3-3)`  
`libnice10 (0.1.14-1)`  
plus another 19 ....

think it may also require `libdvdcss` to play a commercial DVD (PAL Region 2)

> An error occured
> The source seems encrypted and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

Maybe install Ubuntu Restricted Extras:
`sudo apt install ubuntu-restricted-extras`

Alternatively follow the advice on this blogpost:  

**Watch Videos and Play Music (MP3, DVD, etc.)**  
https://support.system76.com/articles/codecs/

Copy and paste the following line for Ubuntu/Pop 18.10 and up:  
`sudo apt install -y gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-plugins-good libavcodec-extra gstreamer1.0-libav chromium-codecs-ffmpeg-extra libdvd-pkg`  

after this, to set-up DVD playback:  
`sudo dpkg-reconfigure libdvd-pkg`  


Enable logging in VLC to see where we are going wrong

Go into :

Tools > Preferences 
under 'Show Settings' change to 'All
go into:

Advanced > Logger

tick the box for 'Log to file' and choose a filename for your logfile
change 'Verbosity' to 'Debug'
restart VLC


apparently the logs for vlc were being saved before this (maybe they still are) to the file:

/var/log/syslog

search for vlc within this


Searching through this file for 'vlc' I came across:

>Feb  2 14:38:19 pop-os vlc.desktop[1794]: libdvdread: Attempting to use device /dev/sr0 mounted on /media/thinkpad/KING_HILL_S1D1 for CSS authentication  
>Feb  2 14:38:19 pop-os vlc.desktop[1794]: libdvdnav: Can't read name block. Probably not a DVD-ROM device.  
>Feb  2 14:38:19 pop-os vlc.desktop[1794]: libdvdnav: vm: dvd_read_name failed  
>Feb  2 14:38:19 pop-os vlc.desktop[1794]: libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1  
>Feb  2 14:38:19 pop-os vlc.desktop[1794]: libdvdnav: Suspected RCE Region Protection!!!  
>Feb  2 14:38:20 pop-os vlc.desktop[1794]: libdvdnav: Suspected RCE Region Protection!!!  
>Feb  2 14:38:20 pop-os vlc.desktop[1794]: libdvdnav: Using dvdnav version 6.0.0  
>Feb  2 14:38:20 pop-os vlc.desktop[1794]: libdvdread: Encrypted DVD support unavailable.  
>Feb  2 14:38:20 pop-os vlc.desktop[1794]: ************************************************  
>Feb  2 14:38:20 pop-os vlc.desktop[1794]: **                                            **  
>Feb  2 14:38:20 pop-os vlc.desktop[1794]: **  No css library available. See             **  
>Feb  2 14:38:20 pop-os vlc.desktop[1794]: **  /usr/share/doc/libdvdread4/README.css     **  
>Feb  2 14:38:20 pop-os vlc.desktop[1794]: **  for more information.                     **  
>Feb  2 14:38:20 pop-os vlc.desktop[1794]: **                                            **  
>Feb  2 14:38:20 pop-os vlc.desktop[1794]: ************************************************  


maybe this isn't Region 2 (UK) but Region 1 (despite what it says on the box). Double-check shortly with a Region 2 DVD.


Following the README.css link gives

>Content Scramble System (CSS)
>-----------------------------
>
>Many DVDs use CSS[0] as a form of a Digital Rights Management (DRM) to encrypt
>the content of Video DVDs. To play such discs a special library is needed to
>decode them, libdvdcss.
>
>Due to the legal limbo of libdvdcss in some particular juristictions, some
>distributions including Debian do not distribute libdvdcss.
>
>If it is legal for you to use CSS in your juristiction, you can:
>
>  * Manually download and compile the source code from
>   <http://www.videolan.org/developers/libdvdcss.html>.
>
>  * Use packages from derivatives that include libdvdcss.
>
> [0] <http://en.wikipedia.org/wiki/Content_Scramble_System>
>
> -- Daniel Baumann <mail@daniel-baumann.ch>  Fri, 02 Oct 2009 16:10:06 +0200


I double-checked and it does say 'PAL 2' on the disc, so I do think it's Region 2. 
I tried a complete different DVD that is also PAL 2 and got the same error on 'Videos' about `libdvdcss'

The error in my logfile was referring to season 1 disc 1 that is indeed NTSC Region 1. Disc 1 of Season 2 should be PAL 2.

I suppose the DVD-ROM drive itself could be faulty in this ThinkPad ?

Maybe I will install Handbrake and see if that installs the right codecs/plugins ?

`sudo add-apt-repository ppa:stebbins/handbrake-releases`
`sudo apt-get update`
`apt-get install handbrake-gtk`
`apt-get install handbrake-cli`

`sudo apt install handbrake-gtk`
`sudo apt install handbrake-cli`

At this point I am using a Roadrunner DVD disc that is PAL Region 2

looking at the Handbrake logs I see

>Cannot load libnvidia-encode.so.1

maybe relevant?

>>[17:54:49] hb_scan: path=/media/thinkpad/ROAD_RUNNER_AND_FRIENDS_L1/VIDEO_TS, title_index=0
>>disc.c:424: error opening file BDMV/index.bdmv
>>disc.c:424: error opening file BDMV/BACKUP/index.bdmv
>>bluray.c:2585: nav_get_title_list(/media/thinkpad/ROAD_RUNNER_AND_FRIENDS_L1/VIDEO_TS/) failed
>>[17:54:49] bd: not a bd - trying as a stream/file instead
>>libdvdnav: Using dvdnav version 6.0.1
>>libdvdread: Attempting to use device /dev/sr0 mounted on /media/thinkpad/ROAD_RUNNER_AND_FRIENDS_L1 for CSS authentication
>>libdvdnav: Can't read name block. Probably not a DVD-ROM device.
>>libdvdnav: vm: dvd_read_name failed
>>libdvdnav: DVD disk reports itself with Region mask 0x00e50000. Regions: 2 4 5

don't seem to be getting anywhere here.

Looking at Ubuntu website for a solution...

**RestrictedFormats/PlayingDVDs**
https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs

`sudo apt install libdvd-pkg && sudo dpkg-reconfigure libdvd-pkg`

>Reading package lists... Done
>Building dependency tree       
>Reading state information... Done
>libdvd-pkg is already the newest version (1.4.2-1-1).
>0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
>libdvd-pkg: guest package [libdvdcss2/1.4.2-1~local] is already installed.

maybe a reboot will help?

I installed **MakeMKV** in case it installed some special plugin/codec that would allow my internal DVD drive to read the commercial DVD

https://www.makemkv.com/  
https://www.makemkv.com/forum/viewtopic.php?f=3&t=224

>Download both binary and source packages:  
https://www.makemkv.com/download/makemkv-bin-1.14.7.tar.gz
https://www.makemkv.com/download/makemkv-oss-1.14.7.tar.gz

unzip these files

then run this command:  

`sudo apt-get install build-essential pkg-config libc6-dev libssl-dev libexpat1-dev libavcodec-dev libgl1-mesa-dev libqt4-dev zlib1g-dev`

For makemkv-oss package:  

`./configure`  
`make`  
`sudo make install`

For makemkv-bin package:  

`make`  
`sudo make install`

The application will be installed as "/usr/bin/makemkv".

End result for me:- doesn't seem to work - DVDs are still not reading...

>>MakeMKV v1.14.7 linux(x64-release) started
>>Automatic checking for updates is enabled, you may disable it in preferences if you don't want MakeMKV to contact web server.
>>Downloading latest SDF to /home/thinkpad/.MakeMKV ...
>>Error 'Scsi error - ILLEGAL REQUEST:READ OF SCRAMBLED SECTOR WITHOUT AUTHENTICATION' occurred while reading 'DVD+R-DL MATSHITA DVD-RAM UJ8G2 1.00' at offset '1048576'

At this point I am going to try an external USB DVD drive and see if I get similar errors.

I might just get rid of the DVD bay and use it to house a SSD instead

Update:
I was able to successfully rip (with Handbrake and MakeMKV) the Roadrunner DVD using an USB external DVD drive. It didn't however seem to want to play the disc smoothly when direct playing via VLC/Videos/mpv. The ripped m4v and mkv files played fine.

Giving up on this for now. Possibly chalking it up as a defective internal DVD drive. Might see if it can play CDs at some point.
