# Bash/Shell scripting
The shell will read each command from top to bottom, and execute them in order.  If a single command fails, the shell will continue on to the next command

## Shebang
Include `#!/bin/bash` at the top of every shell script to indicate that the script is meant to be run by the bash interpreter

## Comments
Lines beginning with `#` serve as comments

## Printing output
Output can be printed with the echo command: `echo Hello World!`

## mkdir
If using the mkdir command to make a new directory, the `-p` switch can be used to avoid generating an error if the directory already exists

## Writing to a file
Write to a file using `>` such as:
`grep H6 shipments.csv > reports/H6.csv`