URxvt Contextual Execution
--------------------------

Provides a right-click menu that is dynamically generated from the "table.txt"
content, combined with the selection in the termanal.

Requires:
========

* URXVT 

Usage:
=====

For testing (cause it don't work just yet) use the `r` script to run the urxvt
terminal from the current directory with current `table.txt`

The format for the `table.txt` is currently:

/regular expression/  "title for menu"  exec|send|menu cmd line args %s

* `exec` - execute a program, e.g. `firefox -url %s`
* `send` - send text to the terminal input, e.g. `nmap -sS -n -v %s`
* `menu` - construct a sub-menu for the popup w/ the content from somewhere

This is ... aspirational. Nothing works yet. 
