# surface autorotate2

A tweaked rotate script based on the various autorotate scripts on github.

This script best works with the xorg wacom configuration for the surface pro 3, that is the various xorg input configuration directives (in /usr/share/X11/xorg.conf.d) are set as follows:

1. The evdev config file has the whole InputClass section with MatchIsTablet commented out
2. The libinput config file has again the MatchIsTablet section commented out (multiple sections in my case)
3. The N-Trig section in the wacom config file is ammended/configured as follows:
```
# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001|N-Trig Pen|N-Trig DuoSense|1B96:1B05 Pen"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "Button2" "3"
        Option "Button3" "2"
EndSection
```

Edit the beginning of the autorotate2 script to have the correct configuration:

```python
#####CONFIGURATION#####
sensorname="accel_3d"
displayname="eDP1" # On some kernels/drivers this may be eDP-1

inputnames=[
        "NTRG0001:01 1B96:1B05"
        ]

pennames=[
        "NTRG0001:01 1B96:1B05 Pen stylus",
        "NTRG0001:01 1B96:1B05 Pen pad",
        "NTRG0001:01 1B96:1B05 Pen eraser"
        ]
```

You can confirm the device names by running `xinput` and `xrandr`

