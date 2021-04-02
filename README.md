# KP3S 3d Printer Notes

Below are my notes, upgrades, info on the [Kingroon KP3S 3d
Printer](https://www.amazon.com/Aluminum-Function-Assemble-Printing-180x180x180mm/dp/B08F51DPRX).
This device is very similar to the Prusa Mini. 

# Cura Configuration

<img src="https://bdwilson.github.io/images/kp3s-cura-printersettings.png" width=400px>
<img src="https://bdwilson.github.io/images/kp3s-cura-extrudersettings.png" width=400px>

<b>Start GCODE</b>
<pre>
; KP3S changes were Y200 -> Y100
G92 E0 ; Reset Extruder
G28 ; Home all axes
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
G1 X0.1 Y20 Z0.3 F5000.0 ; Move to start position
G1 X0.1 Y100.0 Z0.3 F1500.0 E15 ; Draw the first line
G1 X0.4 Y100.0 Z0.3 F5000.0 ; Move to side a little
G1 X0.4 Y20 Z0.3 F1500.0 E30 ; Draw the second line
G92 E0 ; Reset Extruder
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
G1 X5 Y20 Z0.3 F5000.0 ; Move over to prevent blob squish
</pre>

<b>Stop GCODE</b>
<pre>
; KP3S changes were Y150 (don't move up as much as Ender)
G91 ;Relative positioning
G1 E-2 F2700 ;Retract a bit
G1 E-2 Z0.2 F2400 ;Retract and raise Z
G1 X5 Y5 F3000 ;Wipe out
G1 Z10 ;Raise Z more
G90 ;Absolute positionning
G1 X0 Y150 ;Present print
M106 S0 ;Turn-off fan
M104 S0 ;Turn-off hotend
M140 S0 ;Turn-off bed
M84 X Y E ;Disable all steppers but Z
</pre>

# Octoprint Configuration

<img src="https://bdwilson.github.io/images/kingroon_octoprint1.png" width=400px>
<img src="https://bdwilson.github.io/images/kingroon_octoprint2.png" width=400px>
<img src="https://bdwilson.github.io/images/kingroon_octoprint3.png" width=400px>
<img src="https://bdwilson.github.io/images/kingroon_octoprint4.png" width=400px>

## GCODE Scripts
<b>After print job is cancelled</b>
<pre>
G91 ; set to Relative position
G1 E-1 F300 ; retract filament a bit before lifting nozzle
G0 Z15 ; move z axis up 15mm
G90 ; set to Absolute position
G1 Y190 F5000 ; move part out for inspection
G1 X190 F5000 ; move nozzle out of the way
M84 ; disable motors
;disable all heaters
{% snippet 'disable_hotends' %}
{% snippet 'disable_bed' %}
M106 S0 ; disable fan
</pre>

<b>After print job is paused</b>
<pre>
; Reference: https://www.yirco.me/octoprint-pause-change-filament/
{% if pause_position.x is not none %}
; relative XYZE
G91
M83
; retract filament of 0.8 mm up, move Z slightly upwards and 
G1 Z+5 E-0.8 F4500
; absolute XYZE
M82
G90
; move to a safe rest position, adjust as necessary
G1 X0 Y0
{% endif %}
</pre>

<b>Before print job is resumed</b>
<pre>
; Reference: https://www.yirco.me/octoprint-pause-change-filament/
{% if pause_position.x is not none %}
; relative extruder
M83

; prime nozzle
G1 E-0.8 F4500
G1 E0.8 F4500
G1 E0.8 F4500

; absolute E
M82

; absolute XYZ
G90

; reset E
G92 E{{ pause_position.e }}

; WARNING!!! - use M83 or M82(exruder absolute mode) according what your slicer generates
; If you use Cura, this will be M82, otherwise, likely its M83
; For more comments/info, see https://www.yirco.me/octoprint-pause-change-filament/
M82 ; extruder relative mode

; move back to pause position XYZ
G1 X{{ pause_position.x }} Y{{ pause_position.y }} Z{{ pause_position.z }} F4500

; reset to feed rate before pause if available
{% if pause_position.f is not none %}G1 F{{ pause_position.f }}{% endif %}
{% endif %}
</pre>

## Downloads

* [Latest Kingroon Official Firmware](https://www.kingroon.com/downloads/). To install, put contents (Robin_nano.bin, robin_nano_cfg.txt, mks_pic (directory & it's contents) and mks_font (directory & it's contents).

## Upgrades
* Power supply temperature-based fan. 
** [KSD9700 Normally Open Thermostat](https://www.amazon.com/gp/product/B07PGZL1LF). 
** <a href="https://bdwilson.github.io/images/kp3s-powersupply-mod2.png"><img src="https://bdwilson.github.io/images/kp3s-powersupply-mod2.png" width=400px></a>
** <a href="https://bdwilson.github.io/images/kp3s-powersupply-mod1.png"><img src="https://bdwilson.github.io/images/kp3s-powersupply-mod1.png" width=400px></a>


## Parts

* [Kingroon Flexible/magnetic build plate.](https://www.amazon.com/Kingroon-Magnetic-Sticker-Surface-180x180mm/dp/B08KXN8ZGD)
