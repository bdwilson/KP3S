# 3d Touch

This mod uses the Kingroon 3d Touch firmware ([Latest Official Firmware (w/ 3D Touch/BL Touch
feature)](https://www.kingroon.com/?do_action=action.download&DId=2) -  [Local Archive - 12/12/2020](https://github.com/bdwilson/KP3S/blob/main/files/KP3S-Firmware-3Dtouch.zip?raw=true)

# Parts
* [3D Touch auto-leveling sensor](https://www.amazon.com/gp/product/B0821314T9/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B0821314T9&linkCode=as2&tag=orgbubba-20&linkId=2d2d0fa5ed316abc4019de7644878363)
* Left Mount:
[male](https://github.com/bdwilson/KP3S/blob/main/files/BLtouch_Mount-left-male.stl?raw=true)
&
[female](https://github.com/bdwilson/KP3S/blob/main/files/BLtouch_Mount-left-female.stl?raw=true)
(original files from here: https://www.thingiverse.com/thing:4609134) pieces,
or the [Right
mount](https://github.com/bdwilson/KP3S/blob/main/files/BLtouch_Mount-right.stl?raw=true)
(From the Kingroon firmware zip)
* [M3 Button Head screws - for right
mount](https://www.amazon.com/gp/product/B07CYNKLT2/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B07CYNKLT2&linkCode=as2&tag=orgbubba-20&linkId=3762d1a6d467669c478e4468c2808d53)
- I used hex head but the clearance to the extruder mount is really tight.
Button cap would be best, but hex head will work. If you select the left mount
you'll need screws and bolts to mount the mount to the side of the extruder
carriage (you'll need to cut the zip ties there to do this).

# Warnings
Incorrectly configuring this may damage your heat bed sheet - if you have an
older magnetic sheet, it's best to try to get things dialed in using it before
using a "newer" bed. If you damaage it, you can always try to fill the bigger
holes with some rectorseal. 

# Installation
1. Print your parts - left
[male](https://github.com/bdwilson/KP3S/blob/main/files/BLtouch_Mount-left-male.stl?raw=true)
&
[female](https://github.com/bdwilson/KP3S/blob/main/files/BLtouch_Mount-left-female.stl?raw=true)
pieces, or the [right
mount](https://github.com/bdwilson/KP3S/blob/main/files/BLtouch_Mount-right.stl?raw=true)
piece. If you have a stock fan setup, right mount is likely the easiest way to
go but ___I have not tested the configuration file for right-side mount - this was the
file supplied by Kingroon in their bundle but they forgot to invert the extruder E0)___. <br>
<a href="https://bdwilson.github.io/images/IMG_1258-2.jpg"><img src="https://bdwilson.github.io/images/IMG_1258-2.jpg" width=400px></a>
2. Wire it up: If you got the above part from [Amazon](https://www.amazon.com/gp/product/B0821314T9/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B0821314T9&linkCode=as2&tag=orgbubba-20&linkId=2d2d0fa5ed316abc4019de7644878363), connect the ends of the 3d touch devіce to the extension so that (in the picture the 3d touch piece is on
the RIGHT, extension wires on the left):
  * Orange (3d Touch) -> Brown (extension)
  * Yellow (3d Touch) -> Red (extension)
  * Green (3d Touch) -> Yellow (extension)
  * Blue (3d Touch) -> Black (extension)
  * Black (3d Touch) -> White (extension)<br>
<a href="https://bdwilson.github.io/images/IMG_1256.jpg"><img src="https://bdwilson.github.io/images/IMG_1256.jpg" width=400px></a>
3. Wire this up to your mainboard per [KP3S Usage
doc](https://github.com/bdwilson/KP3S/blob/main/files/KP3S-3Dtouch-Usage.docx?raw=true) that comes in the zip file for
the 3d touch 3d touch 3d touch firmware. But for their picture their
___green___ wire is your ___brown___ wire, and their ___grey___ wire is your
___white___ wire. All other wires are the same.<br>
<a href="https://bdwilson.github.io/images/kp3s-bltouch-mod1.png"><img src="https://bdwilson.github.io/images/kp3s-bltouch-mod1.png" width=400px></a><br>
<a href="https://bdwilson.github.io/images/kp3s-bltouch-mod2.png"><img src="https://bdwilson.github.io/images/kp3s-bltouch-mod2.png" width=400px></a>
4. Format an SD card - if using the one that came with your device, it's
properly formatted (MBR boot, FAT32). Use this firmware ([Latest Official Firmware (w/ 3D Touch/BL Touch
feature)](https://www.kingroon.com/?do_action=action.download&DId=2) -  [Local Archive - 12/12/2020](https://github.com/bdwilson/KP3S/blob/main/files/KP3S-Firmware-3Dtouch.zip?raw=true). Put all the files in the root if your SD card. Copy over the proper configuration file depending on which side you mounted your 3d touch device
:
[left](https://github.com/bdwilson/KP3S/blob/main/files/robin_nano_cfg-left.txt?raw=true)
or
[right](https://github.com/bdwilson/KP3S/blob/main/files/robin_nano_cfg-right.txt?raw=true).
___Rename the files to remove "-left" or "-right" so you're left with
robin_nano_cfg.txt___. Put this in the root of your SD card too. 
5. Put the SD card into yourd evice. When you reboot your device, you should see it flashing the new firmware and
applying the settings. Once it does this, it renames both files to .CUR on your
SD card.  If you want to change just the settings, you can copy the .CUR
configuration file to robin_nano_cfg.txt and then reboot the device and it will
apply. ___I suggest starting with a higher z-offset than you think you need.
You can use calipers to attempt to get close, but you want to err on the side
of caution and make the number more positive than negative.___

# Notes
* Want to level before a print? Add <code>G29</code> after <code>G28</code> in
your GCODE start up scripts. 
* Not leveling for each print and instead want to retrieve stored EPROM settings and load them before your print? Add <code>M420 S1</code> after <code>G28</code> in your GCODE start up scripts.

## Commands 
I have my KP3S connected to Octoprint, so it makes it a bit more managable to
adjust the Z offset vs. adjusting it in the configuration file and
re-uploading.You can use these commands in the terminal to see/change your
z-offsets

* M851
  * Shows current z-offset
* M851 Z-1.2 ; set the offset to zero
  * Sets the Z offset to -1.2. 
* M500
  * Store current settings to EEPROM
* M501 
  * Restore settings from EEPROM 
