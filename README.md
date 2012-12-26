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

regular expression  "title for menu"  exec|send|menu "cmd line args"

/regular expression/ - (Not enclosed in `/`) either the word `MATCHALL`
or a regular expression. If a regular expression then the corresponding
option will only appear if it matches the selection.

"title" - a title line that'll appear in the menu, with an optional %s
that will be replaced by the selection text. NOTE: This line can be a
maximum of 40 chars long. **MUST BE QUOTED**

* `exec` - execute a program, e.g. `firefox -url $selection`
* `send` - send text to the terminal input, e.g. `nmap -sS -n -v $selection`
* `menu` - construct a sub-menu for the popup w/ the content from somewhere

"arguments for command" - The string to either execute, or to send to the
terminal. This string is evaluated in the current context, after the regex has
been parsed. The scalar variable `$selection` contains the selected text, and
any `$1` `$2` etc. variables from the regex are available.


Examples:
=========

    http|ftp  "wget $selection" send "wget --continue $selection"

This will match any string with http or ftp and sends the command `wget
--continue <the selected text>` to the terminal.


    (\d{1-3}\.\d{1-3}\.\d{1-3}\.\d{1-3}):(\d+) "nc $1 $2" send "nc -nvv $1 $2"

This will match an IP:PORT (maybe) and parse it into `$1` and `$2`, allowing
for a more nuanced command line composition.

