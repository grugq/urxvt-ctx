URxvt Contextual Execution
--------------------------

Provides a right-click menu that is dynamically generated from the "table.txt"
content, combined with the selection in the terminal.

Requires:
========

* URXVT 

Usage:
=====

For testing (cause it don't work just yet) use the `r` script to run the urxvt
terminal from the current directory with current `table.txt`

The format for the `table.txt` is currently:

regular expression  "title for menu"  exec|send|menu cmd line args %s

/regular expression/ - (Not enclosed in `/`) either the word `MATCHALL`
or a regular expression. If a regular expression then the corresponding
option will only appear if it matches the selection.

"title" - a title line that'll appear in the menu, with an optional %s
that will be replaced by the selection text. NOTE: This line can be a
maximum of 40 chars long. 

* `exec` - execute a program, e.g. `firefox -url %s`
* `send` - send text to the terminal input, e.g. `nmap -sS -n -v %s`
* `menu` - construct a sub-menu for the popup w/ the content from somewhere

This is ... aspirational. Little works yet. 
