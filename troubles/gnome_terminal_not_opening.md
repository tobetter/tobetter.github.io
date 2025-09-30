# 'Gnome Terminal' does not open

## Problem
> This error is reported by several users that 'Gnome Terminal' does not open when the icon is clicked or the command is executed after updating.

## Workaround
By rebooting after adding a line to **/etc/default/locale** resolves the problem.
```
LC_ALL="en_US.UTF-8
```
