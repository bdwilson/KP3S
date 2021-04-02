# Kingroon KP3S 3D Printer Notes

Below are my notes, upgrades, info on the [Kingroon KP3S 3D
Printer](https://www.amazon.com/gp/product/B08F51DPRX/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B08F51DPRX&linkCode=as2&tag=orgbubba-20&linkId=775b118605389899af8b4b9708d69a68).
If you need to be convinced that this is the printer for you, please [see the
following review](https://3dprintbeginner.com/kingroon-kp3s-review/). I was in
need of a smaller printer that I could fit on a shelf, and this fit the bill.
It's very the Prusa Mini, but you can get this in 2 days vs. 2 months.  

## Cura Configuration
* Select Creality -> Ender 3 as your device and make [these changes](Cura.md)

## Octoprint Configuration
* [Setup/Install Octoprint](https://octoprint.org/download/)
* Create new device and configure following [these guidelines](Octoprint.md)

## Downloads
* [KP3S Manual](https://www.kingroon.com/?do_action=action.download&DId=6) - [Local Archive - 12/28/2020](https://github.com/bdwilson/KP3S/blob/main/files/KP3S%20User%20Manual%202020.12.28.pdf)
* [Latest Official
Firmware](https://www.kingroon.com/?do_action=action.download&DId=3). To
install, put contents (Robin_nano.bin, robin_nano_cfg.txt, mks_pic (directory &
it's contents) and mks_font (directory & it's contents). - [Local Archive - 12/12/2020](https://github.com/bdwilson/KP3S/blob/main/files/KP3S-Firmware-201022.zip?raw=true)
* [Latest Official Firmware (w/ 3D Touch/BL Touch feature)](https://www.kingroon.com/?do_action=action.download&DId=2). To install, put contents (Robin_nano.bin, robin_nano_cfg.txt, mks_pic (directory & it's contents) and mks_font (directory & it's contents). - [Local Archive - 12/12/2020](https://github.com/bdwilson/KP3S/blob/main/files/KP3S-Firmware-3Dtouch.zip?raw=true)

## Printable Parts
* [X-Carriage Cable Support](https://www.thingiverse.com/thing:4679515), [Z-Carriage Cable Support](https://www.thingiverse.com/thing:4689252)
* [Marlin LCD Mount](https://www.thingiverse.com/thing:4578390) (Marlin firmware requires display be in landscape orientation)
* [BL Touch Mount](https://www.thingiverse.com/thing:4692042) for use with [3D Touch auto-leveling Sensor](https://www.amazon.com/gp/product/B0821314T9/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B0821314T9&linkCode=as2&tag=orgbubba-20&linkId=2d2d0fa5ed316abc4019de7644878363)
* [Modular Hotend fan mount for 5015 and 3D Touch](https://www.thingiverse.com/thing:4609134) and [5015 fans](https://www.amazon.com/gp/product/B0885XR31J/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B0885XR31J&linkCode=as2&tag=orgbubba-20&linkId=ad2dc28ae56eb2a70f9331ef4ead53b6) 
* [Powersupply Stand](https://www.thingiverse.com/thing:4740318)
* [Fan Silencer] (https://www.thingiverse.com/thing:3612639) use this with the [temperature-sensor mod](Powersupply.md) to really quiet your device down.

## Upgrades
* [Temperature-based fan controller for KP3S power supply](Powersupply.md)

## Parts
* [Kingroon Flexible/magnetic build
plate.](https://www.amazon.com/gp/product/B08KXN8ZGD/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B08KXN8ZGD&linkCode=as2&tag=orgbubba-20&linkId=06e9ed49fc5541940522d04fa697c856)
* [5015 24v Blower Fans](https://www.amazon.com/gp/product/B0885XR31J/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B0885XR31J&linkCode=as2&tag=orgbubba-20&linkId=ad2dc28ae56eb2a70f9331ef4ead53b6)
* [3D Touch auto-leveling sensor](https://www.amazon.com/gp/product/B0821314T9/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B0821314T9&linkCode=as2&tag=orgbubba-20&linkId=2d2d0fa5ed316abc4019de7644878363) - for use with 3D Touch firmware above - see installation instructions, printable parts inside firmware zip.
