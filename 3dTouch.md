# 3d Touch 

[\<\< Back to Main KP3S site](README.md)

The Kingroon 3d Touch firmware does not work. You will need to use the [marlin
firmware here](https://github.com/bdwilson/KP3S/tree/main/marlin-kp3s) to use
your 3d touch/BL touch. 

# Parts
* [3D Touch auto-leveling sensor](https://www.amazon.com/gp/product/B0821314T9/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B0821314T9&linkCode=as2&tag=orgbubba-20&linkId=2d2d0fa5ed316abc4019de7644878363) - I'm almost certain an official BL Touch device would work, but this was less and had good reviews, so I gave it a shot. 
* Mount it (see [Marlin page for mount options where there are pre-compiled versions](https://github.com/bdwilson/KP3S/tree/main/marlin-kp3s).

# Warnings
Incorrectly configuring this may damage your heat bed sheet - if you have an
older magnetic sheet, it's best to try to get things dialed in using it before
using a "newer" bed. If you damage it, you can always try to fill the bigger
holes with some rectorseal. 

# Installation
1. Wire it up: If you got the above part from [Amazon](https://www.amazon.com/gp/product/B0821314T9/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B0821314T9&linkCode=as2&tag=orgbubba-20&linkId=2d2d0fa5ed316abc4019de7644878363), connect the ends of the 3d touch devіce to the extension so that (in the picture the 3d touch piece is on
the RIGHT, extension wires on the left):
  * Orange (3d Touch) -> Brown (extension)
  * Yellow (3d Touch) -> Red (extension)
  * Green (3d Touch) -> Yellow (extension)
  * Blue (3d Touch) -> Black (extension)
  * Black (3d Touch) -> White (extension)<br>
<a href="https://bdwilson.github.io/images/IMG_1256.jpg"><img src="https://bdwilson.github.io/images/IMG_1256.jpg" width=400px></a>
3. Wire this up to your mainboard. <b>Do NOT use the ZMAX (green) connector.
Instead, disconnect your ZMIN connector and connect your BL touch here.</b> 
___green___ wire is your ___brown___ wire, and their ___grey___ wire is your
___white___ wire. All other wires are the same.<br>
<a href="https://bdwilson.github.io/images/kp3s-bltouch-mod1.png"><img src="https://bdwilson.github.io/images/kp3s-bltouch-mod1.png" width=400px></a><br>
<a href="https://bdwilson.github.io/images/kp3s-bltouch-mod2.png"><img src="https://bdwilson.github.io/images/kp3s-bltouch-mod2.png" width=400px></a>
4. Get the firmware from [here]((https://github.com/bdwilson/KP3S/tree/main/marlin-kp3s).

# Notes
* Want to level before a print? Add <code>G29</code> after <code>G28</code> in
your GCODE start up scripts. 
* Not leveling for each print and instead want to retrieve stored EPROM settings and load them before your print? Add <code>M420 S1</code> after <code>G28</code> in your GCODE start up scripts.
* Adjusting your Z offset?  
  * Start printing then go to the Settings -> Tune -> Z-offset menu.  You can adjust this during a print and it will adjust while the print is printing. When done with adjustments, make sure you go back to save eeprom. 

## Commands 
I have my KP3S connected to Octoprint, so it makes it a bit more managable to
adjust the Z offset vs. adjusting it in the configuration file and
re-uploading.You can use these commands in the terminal to see/change your
z-offsets

* <code>M851</code>
  * Shows current z-offset
* <code>M851 Z-1.2</code> ; set the offset to -1.2
  * Sets the Z offset to -1.2. 
* <code>M500</code>
  * Store current settings to EEPROM
* <code>M501</code>
  * Restore settings from EEPROM 

[\<\< Back to Main KP3S site](README.md)
