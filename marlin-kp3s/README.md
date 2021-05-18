# Marlin v2.0.7 for Kingroon KP3S

Original work from: https://github.com/olavgm/marlin-kp3s 

I've only changed the `configuration.h` and `configuration_adv.h` files.

* Support for *BLTouch* has been added
* Babystepping added (but babystepping automatically updates z offset, so make sure to save once you have your z offset the way you want it).  
* You'll need to turn your LCD sideways using [this](https://www.thingiverse.com/thing:4578390) print, or just turn your head sideways. I've chosen to do this since I use Octoprint and also have a magnetic camera mounted to where this LCD screen would overhang.  

## Building Releases
Follow the directions from [TH3D](https://support.th3dstudio.com/hc/downloads/unified-2-firmware/kingroon/kingroon-kp-3s-firmware-kingroon-v1-2-board/), but use this code. 

To install, copy Robin35_nano.bin to in the root of an FAT32-formatted SD card and rename it Robin_nano.bin

### KP3S w/ Stock Extruder, BL Touch mounted on left of extruder
1. Mount BL Touch here: [male](https://github.com/bdwilson/KP3S/blob/main/files/BLtouch_Mount-left-male.stl?raw=true) - should be printed with supports & [female](https://github.com/bdwilson/KP3S/blob/main/files/BLtouch_Mount-left-female.stl?raw=true) (original files from here: https://www.thingiverse.com/thing:4609134)
2. Configure configuration.h to match the following or use this binary. <b>You will set your z offset yourself via Marlin menu</b>
<pre>
#define DEFAULT_AXIS_STEPS_PER_UNIT   { 160, 160, 800, 185 }  // for stock extruder
#define NOZZLE_TO_PROBE_OFFSET { -27, 0, 0 }  // old extruder, mount on left
</pre>

### KP3S w/ Titan w/ metal enclosure, BL Touch mounted on right of extruder
1. Mount BL Touch using [this mount](https://www.thingiverse.com/thing:4816601)
2. Configure configuration.h to match the following or use this binary. <b>You will set your z offset yourself via Marlin menu</b>
<pre>
#define DEFAULT_AXIS_STEPS_PER_UNIT   { 160, 160, 3200, 555 } // for titan 
#define NOZZLE_TO_PROBE_OFFSET { 31, 0, 0 }  // titan extruder mount on right
</pre>

