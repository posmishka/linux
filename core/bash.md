bash
====

Shortcut	Action
Navigation	
|---|---|---|
|Ctrl + a	| Go to the beginning of the line.| 
|Ctrl + e	| 	Go to the end of the line.| 
|Alt + f		| Move the cursor forward one word.| 
|Alt + b		| Move the cursor back one word.| 
|Ctrl + f		| Move the cursor forward one character.| 
|Ctrl + b		| Move the cursor back one character.| 
|Ctrl + x, x		| Toggle between the current cursor position and the beginning of the line.| 
|Ctrl + _		| Undo! (And, yes, that’s an underscore, so you’ll probably need to use Shift as well.)| 
|Ctrl + x, Ctrl + e		| Edit the current command in your $EDITOR.| 
|Alt + d		| Delete the word after the cursor.| 
|Alt + Delete		| Delete the word before the cursor.| 
|Ctrl + d	| Delete the character beneath the cursor.| 
|Ctrl + h	| Delete the character before the cursor (like backspace).| 
|Ctrl + k	| Cut the line after the cursor to the clipboard.| 
|Ctrl + u	| Cut the line before the cursor to the clipboard.| 
|Ctrl + d	| Cut the word after the cursor to the clipboard.| 
|Ctrl + w	| Cut the word before the cursor to the clipboard.| 
|Ctrl + y	| Paste the last item to be cut.| 
|Ctrl + l	| Clear the entire screen (like the clear command).| 
|Ctrl + z	| Place the currently running process into a suspended background process (and then use fg to restore it).| 
|Ctrl + c	| Kill the currently running process by sending the SIGINT signal.| 
|Ctrl + d	| Exit the current shell.| 
|Enter, ~, .	| Exit a stalled SSH session| 
|Ctrl + r	| Bring up the history search.| 
|Ctrl + g	| Exit the history search.| 
|Ctrl + p	| See the previous command in the history.| 
|Ctrl + n	| See the next command in the history.| 

All of these keyboard shortcuts are enabled by Emacs mode in Bash. If you’d like to use Vi shortcuts instead, you can enable that mode and use different shortcuts instead. In addition, most of these are compatible with Zsh as well, although you might find that a few don’t work or require slightly altered shortcuts.

As promised, let’s take a slightly longer dive into some of the more complex shortcuts, particularly the ones that could benefit from some visual reinforcement as to their function.
Ctrl + x + x

Technically, this command is activated by hitting Ctrl + x twice, but it also works to just hold down Ctrl and hit x twice.

This command is particularly useful if you want to quickly hop to the beginning of a lengthy command to fix something at the beginning, and then hop to the end.
Ctrl + _

The magical undo keystroke! If you accidentally delete a character or even a whole word via some of the shortcuts listed above, not all is lost. This even works after deleting a whole line with Ctrl + u, but doesn’t work after you’ve executed the command.
Ctrl + l

Clearing the terminal is less about productivity, perhaps, and more about aesthetics, or starting from a clean slate. Whatever your reason, this simple command will help you keep track of your prompt and put the past behind you.
Ctrl + c

The SIGINT shortcut is, truly, one of the most used shortcuts out there. It will attempt to interrupt the currently running process, and is used frequently to stop commands entered with a typo, or those that appear to have hung up.