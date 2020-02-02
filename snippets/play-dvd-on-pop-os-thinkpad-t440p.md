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

Alternatively follow the advice on this blogpost"

**Watch Videos and Play Music (MP3, DVD, etc.)**
https://support.system76.com/articles/codecs/

Copy and paste the following line for Ubuntu/Pop 18.10 and up:
`sudo apt install -y gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-plugins-good libavcodec-extra gstreamer1.0-libav chromium-codecs-ffmpeg-extra libdvd-pkg`

after this, to set-up DVD playback:
`sudo dpkg-reconfigure libdvd-pkg`
