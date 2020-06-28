registers
=========

### \* - system clipboard register
> *vim-gtk (or vim with +clipboard option) should be used*
 
`"*y` -  copy to system clipboard (middle mouse button to paste outside the vim)

`"*p` - paste from system clipboard

`"*yy` - copy the current line

`gg`, then `"*yG` - copy whole file / buffer

vmap <C-c> "*y - put to .vimrc to have Ctrl+c working with clipboard