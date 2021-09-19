# Tips on Bash Scripting
> Following are my notes are from the course https://www.linkedin.com/learning/linux-bash-shell-and-scripts/ and https://learning.oreilly.com/videos/great-bash/

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
- Out and error can be redirected separately to different output file or together to the same file
- Putting both of them at once would look like
- `ls -l myscript not.here &> lsboth`
- The order of redirection is important
- `ls -l myscript not.here > lsout 2&> 1`
- `ls -l myscript not.here >  2&> 1 > lsout`
- Use pipe to stream output of one program to the input of another. e.g.
- `ls | wc`
- `ls not.here 2>&1 | wc`

### Running Job without locking command prompt
- To continue working on the command prompt and not wait for the job to finish use `&` at the end
- `./somework &` We will get  back the command prompt.

### Setting permission on script file
- `chmod 755 myscript`
- `chmod a+x myscript`
- Now you can run the script with `./myscript` no `bash` necessary in front.

### bash tips for the script to run
- `bash -n myscript` - Bash minus n reads the script but does not execute any of the statements. It runs through the script and checks the syntax only. 
- `bash -v myscript` - minus v is going to echo every line that it reads from the script. Comments will be included in the output.
- `bash -x myscript` - it's similar to minus v. But rather than echoing out the command when it reads it up, it echoes it out just before it executes the command. Also *No* comments would be included in the output.
- In the script file usually the first line looks like `#! /bin/bash` - The comments sign, then an exclamation mark, then a path name to the shell, in this case, bin/bash. This is syntax that the operating system recognizes so that when you execute the script, it knows which interpreter it should use.

### making decisions in bash
- if our script file looks like the following
``` 
cd /temp
rm *
```
- And we do not have `temp` folder to begin with, we just obliterated our current directory files.
- So to avoid this we should use the `&&` , `||` for combining the success of the previous command to the execution of the later command like the following
- `cd /temp && rm *`


