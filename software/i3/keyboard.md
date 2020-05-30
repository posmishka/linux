keyboard
====
### sxhkd

sxhkd is an X daemon that reacts to input events by executing commands.

Its configuration file is a series of bindings that define the associations between the input events and the commands.

The format of the configuration file supports a simple notation for mapping multiple shortcuts to multiple commands in parallel.

https://github.com/baskerville/sxhkd

### xxkb

/etc/X11/app-defaults/XXkb
```
 XXkb.image.path: /usr/share/xxkb
 
 XXkb.group.base: 1
 XXkb.group.alt: 2
 
 XXkb.mainwindow.enable: yes 
 XXkb.mainwindow.geometry: 20x20
 XXkb.mainwindow.image.1: en15.xpm
 XXkb.mainwindow.image.2: ru15.xpm
 XXkb.mainwindow.image.3: ua15.xpm
 XXkb.mainwindow.image.4:
 XXkb.mainwindow.label.font: -misc-*-r-*-0-*
 
 XXkb.*.border.color: black
 XXkb.*.border.width: 0
 
 XXkb.*.label.foreground: white
 XXkb.*.label.background: blue4
 XXkb.*.label.enable: no
 
 XXkb.mainwindow.type: tray
 ! possible values - normal, top, tray, wmaker
 
 XXkb.button.enable: no
 XXkb.button.geometry: 15x15-60+7
 XXkb.button.image.1: en15.xpm
 XXkb.button.image.2: ru15.xpm
 XXkb.button.image.3: su15.xpm
 XXkb.button.image.4:
 XXkb.button.label.font: -misc-*-r-*-13-*
 
 XXkb.controls.add_when_start: yes
 XXkb.controls.add_when_create: yes
 XXkb.controls.add_when_change: no
 XXkb.controls.focusout: yes
 XXkb.controls.two_state: no
 XXkb.controls.button_delete: yes
 XXkb.controls.button_delete_and_forget: yes
 XXkb.controls.mainwindow_delete: yes
 
 XXkb.mousebutton.1.reverse: no
 XXkb.mousebutton.3.reverse: no
 
 XXkb.bell.enable: no
 XXkb.bell.percent: -50
 
 XXkb.ignore.reverse: no
 
 ! XXkb.app_list.<match>.<action>: <list>
 ! <match> is one of "wm_class_class", "wm_class_name", "wm_name", "property"
 ! <action> is one of "ignore", "start_alt", "alt_groupM" (M - 1..4) 
 ! For example:
 !   XXkb.app_list.wm_class_class.ignore: *clock Fvwm*
 !   XXkb.app_list.wm_class_name.start_alt: licq
 !
 !  ignore windows in KDE tray
 !  XXkb.app_list.property.ignore: _KDE_NET_WM_SYSTEM_TRAY_WINDOW_FOR

```
