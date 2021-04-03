# Octoprint Configuration for Kingroon KP3S

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
; try locking motors for a filament swap
; M17 XY M84
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
