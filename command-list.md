# Linux Environment & Tooling: Command List

## Introduction to the Linux File System

Reference: https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/

| Folder | Purpose  |
|---|---|
| / | root directory |
| bin | essential user binaries |
| boot | static boot files |
| dev | device files |
| etc | configuration files |
| home | home folders |
| ~ | your user home directory |
| lib | essential shared libraries |
| lost+found| recovered files |
| media | removable media |
| mnt | temporary mount points |
| opt | optional packages |
| proc | kernel & process files|
| root | root home directory |
| run | application state files |
| sbin | system administration binaries |
| srv | service data |
| sys | system and kernel information |
| tmp | temporary files |
| usr | user binaries & read-only data |
| var | variable data files |

## Navigation

| Command| Action |
|---|---|
| pwd | prints current working directory| 
| ls | lists the files |
| ls -l or ll | long list of files |
| ls -la | long list of files including hidden |
| cd | changes current directory |
| mkdir | creates a directory |
| cp | copy files |
| cp -r | copy directories |
| rm | remove files |
| rmdir | remove (empty) directories |
| rm -r | remove directories |
| rm -f | force remove |
| touch | update timestamp, or create file if doesn't exist |
| ./ | relative path to current directory |
| ../ | relative path to parent directory |
| ln -s `<file/dir>` `<link>`| create a soft/symbolic link; `<link>` must not exist already |
| unlink | remove soft link |
 
## VIM: **Vi** i**M**proved

VIM cheat sheet: https://devhints.io/vim

| Left | Down | Up | Right |
|---|---|---|---|
| H | J | K | L |

Note: you can also use the arrow keys

| Command | Action |
|---|---|
| : | jump to line number |
| % | jumps to match paren |
| :noh | removes highlighting |
| i | insert at marker |
| I | insert at end of line |
| a | insert ahead of marker |
| A | insert at end of line |
| x | delete a character |
| d | to delete a line |
| #d | to delete # number of lines |
| y | cut |
| p | paste |
| u | undo |
| :q | quit |
| :w | write/save |
| :wq | save and quit |
| :x | save and quit |
| :q! | quit without saving |

## Input & Output

| Command | Action |
|---|---|
| cat | prints to the terminal; can also be used to combine files |
| more | view files in the terminal; `enter` to go down one line, `space bar` to go forward a page, `b` to go back one page |
| less | view files using `up` and `down`, `q` to exit |
| head | displays the first 10 lines of a file; can supply -`number` to show the first `number` lines |
| tail | displays the last 10 lines of a file; can supply -`number` to show the first `number` lines |
| (stdin) `<` and `<<` | overwrite & append stdin |
| (stdout) `>` and `<<` | overwrite and append stdout |
| (stderr) `2>` and `2>>` | overwrite and append stderr | 
| (pipes) `|` | used to redirect intup to another program 

## Folders, Files, and Permissions

Permissions 

Example: `-rwxr-xr-x`
<br>Left most column is the type: `-`
<br>Next column is the permissions for the owner: `wrx`
<br>Next column is the permissions for the users in the file's group: `r-x`
<br>Next column is the permissions for everyone else: `r-x`

| Command | Action |
|---|---|
| chmod | changes the permissions of a file |
| type | `-` -> file, `d` -> directory, `l` -> link |
| permissions | `r` -> read, `w` -> write, `x` -> execute |
| chown | changes the owner of a file |
| u | user (file owner) |
| g | group (members of the file's group) |
| o | others |
| a | all |
| + | adds the specified modes for the specified classes |
| - | removes the specified modes for the specified classes |
| = | specifies the exact modes for the specified classes |

e.g., `chmod g+w <file>` adds write permissions to the group

## General Bash Completion Shortcuts
| Shortcut | Action |
|---|---|
| Ctrl-k | delete anything after the cursor |
| Ctrl-u | delete anything before the cursor |
| Ctrl-y | paste back what was deleted |
| Ctrl-r | reverse search |
| Ctrl-l | clear the screen |
| Ctrl-c | cancels a line |
| Ctrl-a | moves to the start of a line |
| Ctrl-e | moves to the end of a line |
| Ctrl-b | moves the cursor backward |
| Ctrl-f | moves the cursor forward |
| !! | executes the last command |
| !abc | executes the last command with abc |
| !abc:p | prints that last command |
| !$ | last argument of that last command |
| Alt-. | inserts the result of the last command |
| && | will proceed with the next command if the first one succeeds |
| ; | will proceed in all cases |
| man `<command>` | will display the documentation belonging to the command |
| man -k | to search for a man page |

## GREP: **G**lobally search a **R**egular **E**xpression and **P**rint

Usage: `grep <term> <file>` or `grep <options> <regex> <file>`
| Flag | Action |
|---|---|
| -r | recursive search for a term in all files at this level and below |
| -i | case insensitive |
| -w | whole word search |
| -v | inverted search; print all lines except the search term |
| -B`#` | display `#` lines before the match |
| -A`#` | display `#` lines after the match |
| -C`#` | display `#` lines both before and after the match |
| -H | print the filename for each match |
| -q | quiet mode |

## Regular Expressions

Regex cheat sheet: https://media.cheatography.com/storage/thumb/davechild_regular-expressions.750.jpg

| Symbol | Purpose |
|---|---|
| ^ | start of a string |
| $ | end of a string |
| \s | white space |
| \d | digit |
| \w | word |
| . | any character except newline |
| `(a|b)` | a or b |
| [abc] | Range; a, b, or c |
| [^abc] | not (a or b or c) |
| [a-q] | lower case letter from a to q |
| [A-Q] | upper case letter from A to Q |
| * | 0 or more |
| + | 1 or more |
| ? | 0 or 1 |
| {`<num>`} | Exactly `<num>` |
| {`<num>`,} | `<num>` or more |
| {`<num1>`, `<num2>`} | matches numbers through num1 to num2 inclusive |

## Finding
Usage: `find <options> <starting path> <expression>`

| Flag | Action |
|---|---|
| -name `<name>` | search by name |
| -maxdepth `<number>` | limits the number of sublevels searched |
| -iname | case insensitive |
| -type f | specifies only files to be searched |
| -type d | specifies only directories to be searched |
| -exec | can execute a search for each result |

## Process Management
| Command | Action |
|---|---|
| ps -a | prints out all active processes |
| ps -x | prints out all processes owned by you |
| ps -f | shows full-format listing |
| ps aux| shows all processes on the system |
| ps -C `<name>` | shows processes by the executable name |
| ps -e --forest | shows a process tree |
| ps -eH | shows a simple tree format|
| kill `<pid>` | SIGTERMs the process |
| kill -9 `<pid>` | SIGKILLs the process |
| killall `<name>` | kills processes that match `<name>` |
| htop | interactive visual for viewing processes |

## Jobs
| Command | Action |
|---|---|
| Ctrl-z | Sleep a process |
| jobs | prints a list of the currently running jobs and their status |
| fg `%<num>` | move that job number to the foreground |
| bg `%<num>` | move that job number to the background |
| kill `%<num>` | kill that job number |

## Aliases
Aliases are shortcuts that you can create yourself.
| Command | Action  |
|---|---|
| alias <alias_name>=`"<command>"` | Creates a temporary alias |
| source ~/.bashrc | Source loads functions into the shell |
| unalias <alias_name> | Temporarily removes the alias |
