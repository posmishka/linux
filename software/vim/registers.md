registers
=========

Generally on Linux, + and * are different: + corresponds to the desktop clipboard (XA_SECONDARY) that is accessed using CTRL-C, CTRL-X, and CTRL-V, while * corresponds to the X11 primary selection (XA_PRIMARY), which stores the mouse selection and is pasted using the middle mouse button in most applications.

### \* - XA_PRIMARY
> *vim-gtk (or vim with +clipboard option) should be used*
 
`"*y` -  copy to system clipboard (middle mouse button to paste outside the vim)

`"*p` - paste from system clipboard

`"*yy` - copy the current line

`"*dd` – cut the current line into *

`gg`, then `"*yG` - copy whole file / buffer

### \+ - XA_SECONDARY
:inoremap <C-v> <ESC>"+pa
:vnoremap <C-c> "+y
:vnoremap <C-x> "+d