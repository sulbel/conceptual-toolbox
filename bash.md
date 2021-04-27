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
* Adding -- after options indicates that this is the end of options. e.g. `mkdir -p -- $directory` 

### Braces
Use curly braces to contain a variable name within a command
* e.g. `grep -- "$container" shipments.csv > "$directory/${container}_report.csv"` would write results of grep command to file with name $container_report.csv
  * without surrounding container variable with curly braces, bash would treat $container_report as a variable

### Export
We can define a variable in the shell, and then run the `export` command in the shell before calling the script to make the variable available to child processes (like the shell script)

## Best Practices
1. Quote your variables
2. Use braces to indicate where the variable name ends
3. Take arguments, and save them as variables inside the script e.g. `directory="$1"`
4. Use end of options `--` to handle cases where input may lead with -
5. Add -x option to shebang line to assist with debugging

## Conditional Execution

### If/Else statements
Syntax is `if ... then ... else ...` and `if` blocks are denoted as ending with the `fi` statement. e.g. to exit a script if no input arguments are supplied:

```
if [[ ! $1 ]]; then
    echo "Error: missing input parameter"
    exit 1
fi
```
  * A successful script execution will exit with return value 0
  * Keywords `if` `then` `else` `fi` **must** be first on a newline, or preceded by a semicolon

* Test if a variable holds a specific string, i.e. `==`, by `[[ $variable = "stringName" ]]
* Negate with `!`
* And with `&&`
* Or with `||`