xxkb
====


/etc/X11/app-defaults/XXkb

 1 XXkb.image.path: /usr/share/xxkb$
 2 $
 3 XXkb.group.base: 1$
 4 XXkb.group.alt: 2$
 5 $
 6 XXkb.mainwindow.enable: yes $
 7 XXkb.mainwindow.geometry: 20x20$
 8 XXkb.mainwindow.image.1: en15.xpm$
 9 XXkb.mainwindow.image.2: ru15.xpm$
10 XXkb.mainwindow.image.3: ua15.xpm$
11 XXkb.mainwindow.image.4:$
12 XXkb.mainwindow.label.font: -misc-*-r-*-0-*$
13 $
14 XXkb.*.border.color: black$
15 XXkb.*.border.width: 0$
16 $
17 XXkb.*.label.foreground: white$
18 XXkb.*.label.background: blue4$
19 XXkb.*.label.enable: no$
20 $
21 XXkb.mainwindow.type: tray$
22 ! possible values - normal, top, tray, wmaker$
23 $
24 XXkb.button.enable: no$
25 XXkb.button.geometry: 15x15-60+7$
26 XXkb.button.image.1: en15.xpm$
27 XXkb.button.image.2: ru15.xpm$
28 XXkb.button.image.3: su15.xpm$
29 XXkb.button.image.4:$
30 XXkb.button.label.font: -misc-*-r-*-13-*$
31 $
32 XXkb.controls.add_when_start: yes$
33 XXkb.controls.add_when_create: yes$
34 XXkb.controls.add_when_change: no$
35 XXkb.controls.focusout: yes$
36 XXkb.controls.two_state: no$
37 XXkb.controls.button_delete: yes$
38 XXkb.controls.button_delete_and_forget: yes$
39 XXkb.controls.mainwindow_delete: yes$
40 $
41 XXkb.mousebutton.1.reverse: no$
42 XXkb.mousebutton.3.reverse: no$
43 $
44 XXkb.bell.enable: no$
45 XXkb.bell.percent: -50$
46 $
47 XXkb.ignore.reverse: no$
48 $
49 ! XXkb.app_list.<match>.<action>: <list>$
50 ! <match> is one of "wm_class_class", "wm_class_name", "wm_name", "property"$
51 ! <action> is one of "ignore", "start_alt", "alt_groupM" (M - 1..4) $
52 ! For example:$
53 !   XXkb.app_list.wm_class_class.ignore: *clock Fvwm*$
54 !   XXkb.app_list.wm_class_name.start_alt: licq$
55 !$
56 !  ignore windows in KDE tray$
57 !  XXkb.app_list.property.ignore: _KDE_NET_WM_SYSTEM_TRAY_WINDOW_FOR$


