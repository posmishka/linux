rxvt
====

```
! fix ssh 
!URxvt*termName: xterm-256color

URxvt.iso14755: false
URxvt.iso14755_52: false

! scrollbar style - rxvt (default),
! plain (compact), NeXT, or xtermn
URxvt.scrollstyle: plain
URxvt.scrollBar_right: True

URxvt.perl-ext-common: default,tabbed,font-size,keyboard-select,vtewheel

! TAB EXTENSION
URxvt.tabbed.tabbar-fg: 2
URxvt.tabbed.tabbar-bg: 0
URxvt.tabbed.tab-fg: 3
URxvt.tabbed.tab-bg: 0
URxvt.tabbed.no-tabbedex-keys: true

!for tabbedx
!URxvt.keysym.Control-t: perl:tabbedex:new_tab
!URxvt.keysym.Control-Tab: perl:tabbedex:next_tab
!URxvt.keysym.Control-Shift-Tab: perl:tabbedex:prev_tab
!URxvt.keysym.Control-Shift-Left: perl:tabbedex:move_tab_left
!URxvt.keysym.Control-Shift-Right: perl:tabbedex:move_tab_right
!URxvt.keysym.Control-Shift-R: perl:tabbedex:rename_tab

URxvt.tabbed.autohide: true
URxvt.tabbed.new-button: false
URxvt.tabbed.tab-numbers: false
!URxvt.tabbed.disable-shift-down: true

URxvt.tabbed.tabcmds.1: N|shell
URxvt.tabbed.tabcmds.2: R|root|su -
URxvt.tabbed.tabcmds.3: M|mc|mc
URxvt.tabbed.tabcmds.4: F|ranger|ranger

!URxvt*background: [70]#777777
!URxvt*depth: 32
URxvt*foreground: #dddddd

!urxvt*depth: 32
!urxvt*background: rgba:0000/0000/0200/c800

!- For fake transparency:

!urxvt*transparent: true
!urxvt*shading: 20

URxvt*inheritPixmap: true
URxvt*transparent: true
! URxvt*shading: 0 to 99 darkens, 101 to 200 lightens
URxvt*shading: 20
! solarized theme
! foreground/background
! black
URxvt.color0  : #000000
URxvt.color8  : #555555
! red
URxvt.color1  : #AA0000
URxvt.color9  : #FF5555
! green
URxvt.color2  : #00AA00
URxvt.color10 : #55FF55
! yellow
URxvt.color3  : #AB4400
URxvt.color11 : #FFFF44
! blue
URxvt.color4  : #0000AA
URxvt.color12 : #5555FF
! magenta
URxvt.color5  : #AA00AA
URxvt.color13 : #FF55FF
! cyan
URxvt.color6  : #00AAAA
URxvt.color14 : #55FFFF
! white
URxvt.color7  : #AAAAAA
URxvt.color15 : #FFFFFF

!-- Xft settings -- !
Xft.dpi:        96
Xft.antialias:  true
Xft.rgba:       rgb
Xft.hinting:    true
Xft.hintstyle:  hintfull

! -- Fonts -- !
URxvt.font:xft:Monospace:pixelsize=15
URxvt.boldfont:xft:Monospace-Bold:pixelsize=15


URxvt.keysym.Home: \033[1~
URxvt.keysym.End: \033[4~
URxvt.keysym.KP_Home: \033[1~
URxvt.keysym.KP_End:  \033[4~

XTerm*termName: xterm-256color
URxvt*termName: rxvt-unicode

URxvt.secondaryScreen: 1
URxvt.secondaryScroll: 0
URxvt.secondaryWheel: 1

URxvt.keysym.Control-Meta-c: builtin-string:
URxvt.keysym.Control-Meta-v: builtin-string:

URxvt.keysym.Shift-Control-V: eval:paste_clipboard
U
```

plugin:

- resize-font
- https://github.com/gryf/tabbed
- https://funloop.org/post/2015-06-25-urxvt-plugins.html

Background different ways
```
!URxvt*background: [70]#777777
!URxvt*depth: 32
URxvt*foreground: #dddddd

!urxvt*depth: 32
!urxvt*background: rgba:0000/0000/0200/c800

!- For fake transparency:

!urxvt*transparent: true
!urxvt*shading: 20
```

https://wiki.archlinux.org/index.php/Rxvt-unicode


