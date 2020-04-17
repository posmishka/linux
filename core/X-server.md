X-server
========

# VGA - setup
xrandr
xrandr --newmode  "1920x1080_60.00"  173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync

xrandr --addmode VGA-1 "1920x1080_60.00"

xrandr --output LVDS-1 --auto --rotate normal --pos 0x0 --output VGA-1 --mode "1920x1080_60.00" --right-of LVDS-1


xrandr --output VGA-1 --off   



xrandr --output LVDS-1 --auto --rotate normal --pos 0x0 --output DP-1 --mode "2560x1440" --rate 75 --right-of LVDS-1