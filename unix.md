---
title: Intro to the Unix CLI
author: Nikhil Yerramilli
patat:
    theme:
        syntaxHighlighting:
            decVal: [bold, onDullRed]
    wrap: true
    margins:
        left: 10
        right: 10
---

# Unix Command Line

```bash
<user>@<machine>:<current directory> $ <command> <arguments>
```

# Unix File System
- Files are organized in a tree-like structure
    - Directories (folders)
    - Files

- Everything in Unix is a file

- Absolute path: /home/yvsn42/foo/bar/a.out
- Relative path: ./a.out

# Basic commands
- `ls` - **l**i**s**t directory contents
    * `-a` - List everything in the directory including hidden files
    * `-l` - List directory contents in a more detail
    * `-R` - List directory contents recursively (list sub-directories as well)
- `echo` - Output to screen
- `cd` - **c**hange **d**irectory
    * Shorthands for `cd`
    * `~` or `$HOME`: The directory you are in when you open a terminal
    * `.`: The directory that you are currently in
    * `..`: The parent directory
    * `-`: The directory you were previously in
- `pwd` - **p**rint working **d**irectory
- `rm` - **r**e**m**ove file
    *  `-i`: 
    *  `-r`:
    *  `f` :
- `mkdir` - **m**a**k**e new **dir**ectory
- `rmdir` - **r**e**m**ove [empty] **dir**ectory
    - `rm -rf` can be used to delete a non-empty directory (Use at your own risk)
- `cp` - **c**o**p**y file
- `mv` - **m**o**v**e file
- `cat` - Print file contents (cat comes from con**cat**enate, don't ask me why)

# Filename globbing
- Interpreted by the shell
- Able to parse multiple filenames on the command line
- Wildcards:
  - `*`: 0 or more characters
  - `?`: 1 character
  - \[...\]: Matches characters in the given set
    - \[abc\]: 1 character that matches a, b, or c
    - \[a-z\]: 1 character that matches a character from a-z
    - \[!abc\]: 1 character that is not a, b, or c

- Examples: `ls file?` or `ls file[1234]`
- Disable globbing with `\`

## Brace Expansion

# Other basics
- History: Up/Down arrow keys
    - `!!` : Run the last command
    - `!<prefix>` : Run the last command that starts with `prefix`
    - `!*`: Repeat all the arguments of the last command
    - `!^`: Repeat the first argument of the last command 
    - `!$` or `$_`: Repeat the last argument of the last command
- Tab completion
- Kill long running programs with `Ctrl-C`

# Terminal shortcuts
  * `<Ctrl-e>`: Move to end of command line
  * `<Ctrl-a>`: Move to beginning of command line
  * `<Ctrl-x>`: Toggle between the begining and end of line

. . .

  - `<Alt-f>`: Move forward a word
  - `<Alt-b>`: Move backward a word

. . . 

  - `<Ctrl-l>`: Clear screen
  - `<Ctrl-w>`: Delete word before the cursor
  - `<Alt-d>`: Delete word after the cursor

. . .

  - `<Ctrl-k>`: Delete from cursor to end of line
  - `<Ctrl-u>`: Delete from start of line to cursor

# Input/Output Redirection
- Everything is a file, even the default input and output channels
  - 0: **stdin** Standard input (keyboard input)
  - 1: **stdout** Standard output (terminal output)
  - 2: **stderr** Standard error (terminal output)
. . .
- You can redirect the default input and output channels to/from files
  - `> [file]`: print output to file
    - `echo "Hello World!" > file
  - `< [file]`: get input from file
    - `echo $HOME > file`
    - `ls < file`
  - `>> [file]`: append output to file
  - `2> [file]`: print error output to file

# Pipes
```sh
[command 1] | [command 2]
```
- The pipe `|` is used to redirect the output of the 1st command as the input of
the 2nd command

- The above line is similar to running both these commands:
```sh
[command 1] > pipe_file
[command 2] < pipe_file
```

- You can have multiple pipes at once
  - Eg. `cut -d: -f1 books | sort | grep "John"`

# `find`
```sh
find [starting point] [expression]
```
- Searches recursively from the starting point (directory) and runs expression on
each filename
- Expressions (which return true or false):
  - `-name [filename]`
  - `-type [f,d]`
  - `exec [command] {} \;`
  - `perm [octal]`

- Examples:
  - `find .`
  - `find . -print`
  - `find . -name *file1 -print`
  - `find . -type d`
  - `find . -type f`
  - `find . -exec cat {} \;`

# `diff`
```sh
diff [file1] [file2]
```
- Compares files line by line
- No output indicates that the files are identical
- Three kinds of changes listed by diff:
1. Additions
```
firstStart a secondStart, secondStop
> lines from the second file to add to the first file.
```
 2. Deletions
```
 firstStart, firstStop d lineCount
< lines from the first file to delete.
```
3. Changes
```
firstStart, firstStop c secondStart, secondStop
< lines in the first file to be replaced
----
> lines in the second file to be used for the replacement
---
```

# `alias`
- Make alias: `alias [aliasname] [command]`
- Show alias: `alias [aliasname]`
- Show all aliases: `alias`
- Remove alias: `unalias [aliasname]`

# `grep`
-  To search for a particular pattern in given file(s), run:
```sh
grep [pattern] [file(s)]
```
- `-i` = ignore case.
- `-l` = just list of files displayed.
- `-n` = line numbers.
- `-v` = display all lines that don't match the pattern.
- `-x` = line must be an exact match.

# `head` and `tail`
```sh
head -n [file(s)] # Display the first n lines of file(s). Default is 10
tail -n [file(s)] # Display the last n lines of file(s). Default is 10
```
# Utilities

- `cal`: Display the calendar on the command line
- `date`: Display the current date
- `wget`: **w**eb**get**, download the file specified from the given link
- `wc`: Word count
- `less`: Make output easier to read
  - `cat file | less`
  - Scroll with arrow keys, `q` to quit, `h` for help
- `tar`: Compress/Uncompress files in tar format
  - `-c` = create
  - `-f` = filename
  - `-t` = generates a table of contents.
  - `-v` = verbose mode
  - `-x` = extract mode

# Help
- `man`: Open manual page for command
- `whatis`: Describe the command in one line
- `which`: Show the location of the command executable

# Other topics to cover
- File permissions
- Regular expressions
- bashrc
- Quoting
- Shell variables (run the command `printenv`)
- Shell scripts
