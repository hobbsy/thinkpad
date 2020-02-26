## Get MakeMKV to recognize external DVD drive

My external DVD-ROM drive (an LG DVD-RAM GSA-E40L) wasn't being recognized by MakeMKV on my ThinkPad T440p running Manjaro.

I found a solution on the Manjaro forums here:
https://forum.manjaro.org/t/solved-makemkv-complains-no-dvd-drive/41894

Simply type in the command-line

`sudo modprobe sg`

This sort of worked for me. Error I now see:

`MakeMKV v1.14.7 linux(x64-release) started
Profile parsing error: default profile missing, using builtin default
Failed to get full access to drive "MATSHITA DVD-RAM UJ8G2". Make sure that you either have write access to device "/dev/sr0", are member of "cdrom" group or have CAP_SYS_RAWIO enabled.
Failed to get full access to drive "HL-DT-ST DVDRAM GSA-E40L". Make sure that you either have write access to device "/dev/sr1", are member of "cdrom" group or have CAP_SYS_RAWIO enabled.
`

Think I need to chmod 666 these 2 drives...

eg.

`sudo chmod 666 /dev/sr0`
`sudo chmod 666 /dev/sr1`

edit - nope, that didn't work

`Failed to get full access to drive "MATSHITA DVD-RAM UJ8G2". Make sure that you either have write access to device "/dev/sr0", are member of "cdrom" group or have CAP_SYS_RAWIO enabled.
Failed to get full access to drive "HL-DT-ST DVDRAM GSA-E40L". Make sure that you either have write access to device "/dev/sr1", are member of "cdrom" group or have CAP_SYS_RAWIO enabled.`


found this thread on reddit by Googling the error
https://www.reddit.com/r/Ubuntu/comments/egugsh/wits_end_dvd_mounting_in_1804/

tried these commands

`sudo mkdir -p /mnt/cdrom`
`sudo mount /dev/sr1 /mnt/cdrom`

Got this feedback message:

`mount: /mnt/cdrom: WARNING: device write-protected, mounted read-only.`

(NB: my external drive is sr1, the internal DVD drive is sr0)

`ls /mnt/cdrom`

shows:

`AUDIO_TS  VIDEO_TS`

MakeMKV still giving me the same error message.

