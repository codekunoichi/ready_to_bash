# Tips on Bash Scripting
> Following are my notes are from the course https://www.linkedin.com/learning/linux-bash-shell-and-scripts/

### How to count how many lines are present in a file?

`man bash | wc -l`

### Script File Basics

- The script file should start with `#!` (also known as Shebang)
- Followed by the path of Bash or env `#!/usr/bin/env bash` or `#!/bin/bash` is also acceptable.