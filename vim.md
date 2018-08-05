#  VIM Tutorial

set mouse=a
- Can scroll
- Double click to enter visual mode
- Switch between windows by clicking on them
- Double [left] click to goto tag link
    - Use CTRL + Right Click to go back
- You can even select text by holding down the mouse button.
- Paste with the middle mouse button

:ls - List the path of the file (w.r.t. home directory)
:cd - Change vim's working directory
:echo

## Motions
- h : Left
- j : Down
- k : Up
- l : Right
- H : Highest [line] on screen
- M : Middle [line] on screen
- L : Lowest [line] on screen

word (seperated by characters in option `keyword`)
- w : Move forward a word
- b : Move backward a word
- e : Move forward to the end of the word
- ge : Move backwar to the end of the word

WORD (Only seperated by whitespace)
- W :
- B :
- E :
- gE :
- % : Move to matching pair (Parentheses)
- { : 

- 0 : Move to beginning of line
- $ : Move to end of line
- ^ : Move to first non-blank character in line


## Text Objects
- iw : Inner Word
- it : Inner Tag
- ip : Inner Paragraph
- i" :
- i{ :


## :expand("%") - Filepath

- '%' - Filepath
    - '%:h' - Filepath excluding the filename
    - '%:r' - Filepath excluding the file extension

## :help

- help can also be used for keyboard shortcuts
- :helpgrep <pattern>

- :help holy-grail

- :smile
