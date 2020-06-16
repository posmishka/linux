special_characters
==================








## Deprecated special characters (recognized, but not recommended)

This group of characters will also be evaluated by Bash to have a non-literal meaning, but are generally included for backwards compatibility only. These are not recommended for use, but often appear in older or poorly written scripts.

| Char | Description |
| ---  | --- |
| \` ` | Command substitution - use $( ) instead. |
| [ ] | Test - an alias for the old test command. Commonly used in POSIX shell scripts. Lacks many features of [[ ]]. |
| \$[ ] | Arithmetic expression - use $(( )) instead. |
