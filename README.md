# Kingroon KP3S 

<b>For general documentation/upgrades, please go here: https://bubba.org/kp3s</b>

# Marlin v2.0.7 for Kingroon KP3S
Thanks to @olavgm for his work on this: https://github.com/olavgm/marlin-kp3s 

I've only changed the `configuration.h` and `configuration_adv.h` files.

* Support for *BLTouch* has been added
* Babystepping added (but babystepping automatically updates z offset, so make sure to save once you have your z offset the way you want it).  
* You'll need to turn your LCD sideways using [this](https://www.thingiverse.com/thing:4578390) print, or just turn your head sideways. I've chosen to do this since I use Octoprint and also have a magnetic camera mounted to where this LCD screen would overhang.  

## Building Releases
Follow the directions from [TH3D](https://support.th3dstudio.com/hc/downloads/unified-2-firmware/kingroon/kingroon-kp-3s-firmware-kingroon-v1-2-board/), but use this code. 

## Installation
1. Follow the guidance here on installing and connecting: https://bubba.org/kp3s/3dTouch/
2. To install, copy Robin35_nano.bin to in the root of an FAT32-formatted SD card and rename it Robin_nano.bin. 

### KP3S w/ Stock Extruder, BL Touch mounted on left of extruder
1. Mount BL Touch here: [male](https://github.com/bdwilson/KP3S/blob/main/files/BLtouch_Mount-left-male.stl?raw=true) - should be printed with supports & [female](https://github.com/bdwilson/KP3S/blob/main/files/BLtouch_Mount-left-female.stl?raw=true) (original files from here: https://www.thingiverse.com/thing:4609134)
2. Configure configuration.h to match the following or use [this binary](https://github.com/bdwilson/KP3S/blob/main/releases/Stock/Robin_nano.bin?raw=true).
<b>You will set your z offset yourself via Marlin menu. If you don't use
the mount above, your offsets WILL be different and you'll need to compile your
own version.</b>
<pre>
#define DEFAULT_AXIS_STEPS_PER_UNIT   { 160, 160, 800, 185 }  // for stock extruder
#define NOZZLE_TO_PROBE_OFFSET { -27, 0, 0 }  // old extruder, mount on left
</pre>
or, you can do this via [Repetier](https://www.repetier.com/download-now/) or
Octoprint via termina:
<pre>
M92 X160 Y160 Z800 E185
M851 X-27 Y0 Z0
</pre>

### KP3S w/ Stock Extruder, BL Touch mounted on left of extruder 
1. Mount for BL Touch is [here](https://www.thingiverse.com/thing:4704668)
2. Configure configuration.h to match the following or use [this binary](https://github.com/bdwilson/KP3S/blob/main/releases/Stock2/Robin_nano.bin?raw=true).
<b>You will set your z offset yourself via Marlin menu. If you don't use
the mount above, your offsets WILL be different and you'll need to compile your
own version.</b>
<pre>
#define DEFAULT_AXIS_STEPS_PER_UNIT   { 160, 160, 800, 185 }  // for stock extruder
#define NOZZLE_TO_PROBE_OFFSET { -27, -1, 0 }  // old extruder, mount on left
</pre>
or, you can do this via [Repetier](https://www.repetier.com/download-now/) or
Octoprint via termina:
<pre>
M92 X160 Y160 Z800 E185
M851 X-27 Y0 Z0
</pre>

### KP3S w/ Titan w/ metal enclosure, BL Touch mounted on right of extruder
1. Mount BL Touch using [this mount](https://www.thingiverse.com/thing:4816601)
2. Configure configuration.h to match the following or use [this
binary](https://github.com/bdwilson/KP3S/blob/main/releases/Titan/Robin_nano.bin?raw=true).
<b>You will set your z offset yourself via Marlin menu. If you don't use
the mount above, your offsets WILL be different and you'll need to compile your
own version.</b>
<pre>
#define DEFAULT_AXIS_STEPS_PER_UNIT   { 160, 160, 3200, 555 } // for titan 
#define NOZZLE_TO_PROBE_OFFSET { 31, 0, 0 }  // titan extruder mount on right
</pre>
or, you can do this via [Repetier](https://www.repetier.com/download-now/) or
Octoprint via termina:
<pre>
M92 X160 Y160 Z3200 E555
M851 X31 Y0 Z0
</pre>

[\<\< Back to Main KP3S site](https://bubba.org/kp3s)
