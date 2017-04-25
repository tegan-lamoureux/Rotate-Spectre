# Rotate-Spectre  

This is a small python(2) script for linux that enables auto rotation of the touchscreen (as well as auto-rotatio of the touchscreen input mapping) on the newer Kaby Lake model of the HP Spectre x360.  

It's forked from a gist of a more robust script by [ei-grad](https://github.com/ei-grad), which, while functionally correct, wasn't auto-detecting my hardware. I explicitly added in the hardware names for the commands to work, and removed all of the auto-detecting features for simplicity. Therefore, this will work for any model with this same hardware, but no one else.  

### Usage  

Run as a script (after making executable) with `./rotate.py &`, or by using python directly with `python2.7 rotate.py &`. For persistance after reboot, ensure it runs on boot, however that's done with your distribution. For Ubuntu that's usually with `/etc/rc.local`, and for Arch that's in `~/.xinit` before you exec your xorg/wm/dm.  

### Troubleshooting  

If it's not working, check the names of your devices with `xinput --list`, and compare the names for your touchscreen and trackpad with the names on line 55 and 58 of this script (specifically, `ELAN0732:00 04F3:2493` and `SynPS/2 Synaptics TouchPad`). Replace those with yours if there's a mismatch.
