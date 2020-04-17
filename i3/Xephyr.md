Xephyr
======

Nested X server - fullscreen video or game inside the i3 window

to I just have 2 separate Firefox windows, one inside the Xephyr window, and the other one normally on a different workspace for actual full screen.

The name of the Xephyr package varies from distro to distro.  xserver-xephyr, otherwise just google it.

So, to get everything running, first open a spare terminal. From there, run

Xephyr -ac -resizeable -br -reset -terminate 2> /dev/null :1 &

This should open a new, black window, which you can move around and resize like any other window in i3.

Then, run

DISPLAY=:1.0

to make sure subsequent x windows started from this terminal open in the Xephyr window.

Finally, just run

firefox
