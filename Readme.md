# Tips on Bash Scripting
> Following are my notes are from the course https://www.linkedin.com/learning/linux-bash-shell-and-scripts/

### How to count how many lines are present in a file?

`man bash | wc -l`

### How to measure time to process?
- Bash has a built in time command to report how much time a process consumed. `time find / -name core`

## Script File Basics

- The script file should start with `#!` (also known as Shebang)
- Followed by the path of Bash or env `#!/usr/bin/env bash` or `#!/bin/bash` is also acceptable.
- Scripts need execute permissions you will use `chmod U+X`
- With a read only permission to a script, to execute the script you must add the interpeter. So it needs to be become `bash thescript.sh`
- If current directory (.) is not in your path, then you must explicitly call it using `./thescript.sh`

### Variable in Bash
- Variables are given values with `=`
- Do not put spaces around `=`
- If the value has a special character in it, put quotes around the special characters.
- Created when you assign or declare using export command
- remove variables using `unset` command
- reference a variable using a `$` in front of the variables `echo myvar is $myvar`
- `echo ${myvar}iable` will substitute the {myvar} with the value of myvar and concatenate with the rest `iable`

### IO Redirection
- Shell not the command does the IO Redirection
- e.g. 
- ` ls -l myscript > lsout `
- Any command can have their I/O redirected.
- Error messages are going to output into the Error Out - which would be printed on screen
- stdout would go to the file and stderr will also go to the file if we do following
- `ls -l myscript not.here > lsout 2> lserr`
