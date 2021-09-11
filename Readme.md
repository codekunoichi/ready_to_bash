# Tips on Bash Scripting
> Following are my notes are from the course https://www.linkedin.com/learning/linux-bash-shell-and-scripts/

### How to count how many lines are present in a file?

`man bash | wc -l`

### How to measure time to process?
- Bash has a built in time command to report how much time a process consumed. `time find / -name core`

### Script File Basics

- The script file should start with `#!` (also known as Shebang)
- Followed by the path of Bash or env `#!/usr/bin/env bash` or `#!/bin/bash` is also acceptable.
- Scripts need execute permissions you will use `chmod U+X`
- With a read only permission to a script, to execute the script you must add the interpeter. So it needs to be become `bash thescript.sh`
- If current directory (.) is not in your path, then you must explicitly call it using `./thescript.sh`

