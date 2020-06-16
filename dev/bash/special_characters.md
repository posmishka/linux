special_characters
==================


| Char | Description |
| --- | --- |
|{ }                                                                                                                                                                                                                                            |Inline group — commands inside the curly braces are treated as if they were one command. It is convenient to use these when Bash syntax requires only one command and a function doesn't feel warranted.                                       |
|( )                                                                                                                                                                                                                                            |Subshell group — similar to the above but where commands within are executed in a subshell (a new process). Used much like a sandbox, if a command causes side effects (like changing variables), it will have no effect on the current shell. |
|(( ))                                                                                                                                                                                                                                          |Arithmetic expression — with an arithmetic expression, characters such as +, -, *, and / are mathematical operators used for calculations. They can be used for variable assignments like (( a = 1 + 4 )) as well as tests like if (( a < b )) |
|$(( ))                                                                                                                                                                                                                                         |Arithmetic expansion — Comparable to the above, but the expression is replaced with the result of its arithmetic evaluation. Example: echo "The average is $(( (a+b)/2 ))".                                                                    |
| $#  	| Number of arguments to script| 
| $* 	| Arguments to script| 
| $@ 	| Original arguments to script| 
| $- 	    | Flags passed to shell| 
| $? 	| Status of previous command| 
| $$ 	| Process identification number| 
| $! 	| PID of last background job| 

|>ofile 	csh, sh 	Standard output
|>>ofile 	csh, sh 	Append to standard output
|<ifile 	csh, sh 	Standard Input
|<<word 	csh, sh 	Read until word, substitute variables
|<<\word 	csh, sh 	Read until word, no substitution
|<<-word 	sh 	Read until word, ignoring TABS
|>>!file 	csh 	Append to file, ignore error if not there
|>!file 	csh 	Output to new file, ignore error if not there
|>&file 	csh 	Send standard & error output to file
|<&digit 	sh 	Switch Standard Input to file
|<&- 	sh 	Close Standard Input
|>&digit 	sh 	Switch Standard Output to file
|>&- 	sh 	Close Standard Output
|digit1<&digit2 	sh 	Connect digit2 to digit1
|digit<&- 	sh 	Close file digit
|digit2>&digit1 |	Connect digit2 to digit1
|digit>&- 	|	Close file digit



## Deprecated special characters (recognized, but not recommended)

This group of characters will also be evaluated by Bash to have a non-literal meaning, but are generally included for backwards compatibility only. These are not recommended for use, but often appear in older or poorly written scripts.

| Char | Description |
| ---  | --- |
| \` ` | Command substitution - use $( ) instead. |
| [ ] | Test - an alias for the old test command. Commonly used in POSIX shell scripts. Lacks many features of [[ ]]. |
| \$[ ] | Arithmetic expression - use $(( )) instead. |
