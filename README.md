# Rotate-Spectre  

This is a small python(2) script for linux that enables auto rotation of the touchscreen (as well as auto-rotation of the touchscreen input mapping) on the newer Kaby Lake model of the HP Spectre x360.  

It's forked from a gist of a more robust script by [ei-grad](https://github.com/ei-grad), which, while functionally correct, wasn't auto-detecting my hardware. I explicitly added in the hardware names for the commands to work, and removed all of the auto-detecting features for simplicity. 

As of January 2018, it seems there's quite a few different touchscreens out there, as well as some pen-enabled spectres. For this script to work, you'll have to change device names yourself. The PEN line will only be used if pen support is found, so don't worry about it if yours doesn't have that. 

I'm aware that I could have programatically scanned and found the touchscreen name with check_output(), but that was where the first version of this script was failing me, and I don't have access to enough hardware to reliably write that. So manual it is.


### Requirements 

 - Python 2.7
 - HP Spectre x360 (But honestly, it might work with others if the correct devices are passed. Give it a shot.)
 
### Usage  

Find the names of your devices with `xinput --list`, and compare the names for your touchscreen, trackpad, and pen with the variables `TOUCHSCREEN`, `TOUCHPAD`, and `PEN` (if applicable) at the top of the script. Replace if necessary. 

Run as a script (after making executable) with `./rotate.py &`, or by using python directly with `python2.7 rotate.py &`. For persistence after reboot, ensure it runs on boot, however that's done with your distribution. <s>For Ubuntu that's usually with `/etc/rc.local`</s> for Arch that's in `~/.xinit` before you exec your xorg/wm/dm.  

<b><u>Note:</u></b> Using rc.local may not actually work though. It needs to run after you already have an X session running, or the calls to xrandr, and xinput will fail. I don't have an ubuntu/debian system to test this on, but I'd suggest having it auto run somehow after your x session comes up. Probably with your WM/DE's provided system for running programs on startup.

### Troubleshooting 

Double check your names, make sure you're updated to the latest version of whatever kernel your distro runs, and make sure you're using Python 2. If it's still giving you an error, feel free to email or open an issue!
