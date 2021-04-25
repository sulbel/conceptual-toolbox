# Bash/Shell scripting
The shell will read each command from top to bottom, and execute them in order.  If a single command fails, the shell will continue on to the next command

## Basics

### Shebang
Include `#!/bin/bash` at the top of every shell script to indicate that the script is meant to be run by the bash interpreter

### Comments
Lines beginning with `#` serve as comments

### Printing output
Output can be printed with the echo command: `echo Hello World!`

### mkdir
If using the mkdir command to make a new directory, the `-p` switch can be used to avoid generating an error if the directory already exists

### Writing to a file
Write to a file using `>` such as:
`grep H6 shipments.csv > reports/H6.csv`

## Shell Variables
Variables are declared with an `=` and dereferenced with a `$`, e.g. `greeting="hello"` and then calling `echo $greeting` would print hello.
  * Variables are **case sensitive** and pre-defined variables are capitalized, e.g. `$USER` 
  * Variable assignments have to be a single word; use quotes to wrap multiple variables
    * e.g. `usergreeting="$greeting, $USER"`
  *  **DO NOT** put spaces around `=` for variable assignment
  * **FOR VALUES WITH SPACES** quotes *must* be used, e.g.
  ```
    directory="My directory"
    echo "directory"
  ```

  * Utility `shellcheck` can be used to check the script for double quote misses
  
Shell variables **have no data type**, they simply store strings

### Command line arguments
Command line arguments may be referenced in incremental order as such: `$1` `$2` etc
  * e.g. ./myScript.sh Hello - `echo $1` would print Hello

### Naming conventions
Only letters, numbers, and underscores are allowed 
  * First character of variable name must be a letter or underscore 
  * Case sensitive, but pre-defined variables use capital.  Best practice to only use lowercase

## Debugging
* Adding `-v` after the shebang (but on the same line) will cause the interpreter to print every line before trying to execute it
* Adding `-x` will do the same as `-v`, but also print the value of variables