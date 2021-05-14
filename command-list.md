# Linux Environment & Tooling: Command List

## Navigation and File Utilities

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

VIM cheat sheet: https://rumorscity.com/wp-content/uploads/2014/08/10-Best-VIM-Cheat-Sheet-01.jpg

| Left | Down | Up | Right |
|---|---|---|---|
| H | J | K | L |

Note: you can also use the arrow keys

| Command | Action |
|---|---|
| ESC | enter command mode | 
| :`<number>` | jump to line number |
| /`<text>` or ?`<text>` | search for text in the document |
| n | (search) find next |
| N | (search) find previous |
| :noh | removes highlighting |
| i | insert at marker |
| I | insert at beginning of line |
| a | insert ahead of marker |
| A | insert at end of line |
| x | delete a character |
| d | to (cut) delete a line |
| #d | to delete # number of lines |
| y | yank (copy) |
| p | paste |
| u | undo |
| :q | quit |
| :w | write/save |
| :wq | save and quit |
| :x | save and quit |
| :q! | quit without saving |

Exercise: open the supplied grepfile with VIM and practice navigating the file and making adjustments in both command and input mode. Practice exiting and saving.

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

## Permissions

Permissions 

Example: `-rwxr-xr-x`
<br>Left most column is the type: `-`
<br>Next column is the permissions for the owner: `rwx`
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

<b>Also,</b> number notation:

Usage: `chmod <value> <files>`

4 = r (Read)<br>
2 = w (Write)<br>
1 = x (execute)<br>

e.g.,<br>
"142" is --x/r--/-w-<br>
"724" is rwx/-w-/r--<br>
"777" is rwx/rwx/rwx

## Bash shortcuts, and useful other useful shell commands
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
| && | will proceed with the next command if the first one succeeds (short-circuit) |
| ; | will proceed in all cases |
| man `<command>` | will display the documentation belonging to the command |
| man -k | to search for a man page |

## GREP: **G**lobally search a **R**egular **E**xpression and **P**rint

Usage: `grep <term> <file>` or `grep <options> <regex> <file>`
| Flag | Action | Example |
|---|---|---|
| -i | case insensitive | `grep -i "abcd" grepfile` |
| -w | whole word search | `grep -w "test" grepfile` |
| -r | recursive search for a term in all files at this level and below | `grep -r "abcd" ~` |
| -v | inverted search; print all lines except the search term | `grep -v "test" grepfile` |
| -B`#` | display `#` lines before the match | `grep -B3 "test" grepfile` |
| -A`#` | display `#` lines after the match | `grep -A3 "test" grepfile` |
| -C`#` | display `#` lines both before and after the match | `grep -C3 "test" grepfile` |
| -c | display the number of times the match was found | `grep -c "test" grepfile` |

## Regular Expressions Primer

Regex cheat sheet: https://media.cheatography.com/storage/thumb/davechild_regular-expressions.750.jpg

| Symbol | Purpose |
|---|---|
| ^ | start of a string |
| $ | end of a string |
| \s | white space |
| \d | digit |
| \w | word |
| . | any character except newline |
| (a\|b) | a or b |
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

Using the following commands with grep, what would you expect grep to find?

`grep "^ABC" grepfile`<br>
`grep "[abc]\{2,\}" grepfile`<br>
`grep "[A-P][a-d]?" grepfile`<br>
`grep "\s(L|w)\w" grepfile`

## Finding Files
Usage: `find <starting path> <options>  <expression>`

| Flag | Action |
|---|---|
| -name `<name>` | search by name |
| -maxdepth `<number>` | limits the number of sublevels searched |
| -iname | case insensitive |
| -type f | specifies only files to be searched |
| -type d | specifies only directories to be searched |
| -exec | can execute a search for each result |

## Aliases
Aliases are shortcuts that you can create yourself.
| Command | Action  |
|---|---|
| alias <alias_name>=`"<command>"` | Creates a temporary alias |
| source ~/.bashrc | Source loads functions into the shell |
| unalias <alias_name> | Temporarily removes the alias |

## Environment Variables
KEY=value
<br>KEY=value1:value2
<br>`printenv` will print out current environment variables

Note: environment variables are local to the shell until saved and made global

<b>PATH</b>
<br>Environment variable that tells the shell which directories to search for executable files. A user's PATH consists of a series of colon-separated paths (absolute). Can add to the path by using:

export PATH=$PATH:/new/path

## Process Management

| Command | Action |
|---|---|
| ps -a | prints out all active processes |
| ps -x | prints out all processes owned by you |
| ps -f | shows full-format listing |
| ps aux | shows all processes on the system |
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
| jobs | prints a list of the currently running jobs and their status |
| Ctrl-z | Sleep a process |
| fg `<num>` | move that job `num` to the foreground |
| bg `<num>` | move that job `num` to the background |
| kill `<num>` | kill that job `num` |
