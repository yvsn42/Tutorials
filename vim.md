#  VIM Tutorial

## Tips

### Map the CapsLock to CTRL

### Remap the Esc key
Vim is a modal editor, and most of the editing functionality discussed below is
available in Normal mode. You will be using `<Esc>` a lot, so it might be useful
to remap the Esc key.
`set inoremap jk <Esc>`
Running that command allows you exit command with just j+k. Doing this, and
remapping the CapsLock key allow to keep your fingers on the home row most of the
time.
You may be wondering how you'll be able to type "jk" without exiting insert mode.
Well you can do that by typing "j", then waiting for a few seconds before
entering "k". Vim waits about 1 second between keys in multi-key mappings.
(See :help timeout for more information)

### Use a mouse in vim
This is not recommended by many Vim users, given that the point of Vim is to
be able to edit text entirely through the keyboard. However, I did find this
mode useful for doing work when I was still in the process of learning vim.
It would be better to learn how to use vim without a mouse, but know that this
option is available in newer versions of vim.

set mouse=a
- Can scroll
- Double click to enter visual mode
- Switch between windows by clicking on them
- Double [left] click to goto tag link
    - Use CTRL + Right Click to go back
- You can even select text by holding down the mouse button.
- Paste with the middle mouse button

> You can't use the mouse to select text to copy/paste to your system keyboard with `set mouse`

## set
`set` is used to assign values to variables used by vim. This is equivalent to
configuring certain options/preferences in the usual text editor
- Most vim variables are boolean values you set to true or false
    - For example: `:set number` enables line numbers in vim
    - To disable, prepend the variable with 'no'.
    - `set nonumber` disables line numbering
- Other vim variables may take a value which you can specify using '='
    - `set mouse=a`
    - Use `+=` to add values/options to ones that are already set in the variable

- To see what value a vim variable already has by appending `?` to the variable
    - `set mouse?`

:ls - List the path of the file (w.r.t. home directory)
:cd - Change vim's working directory
:echo


## Modes
- Normal (Default)
- Insert (i)
- Visual (v)
- Replace (R)
- Command (:)

## Terminal Commands
- Run Unix commands on vim using `!`
For example:
- `:!ls` to list files in the current directory
- `:!grep` to search for patterns across multiples files


## Paste
- p : Paste
- Note:
    - Usually when you copy code outside outside of vim, vim indent each new line
      making the copied code looks like it's cascading to the right.
      Fix:
      - :set paste
	  - Enter insert mode
      - Then copy/paste you code into vim
      - exit insert mode
	  - :set nopaste	

    - Yes, that sequence of commands seems a lot, so I'd recommend mapping the
    `:set paste` command to a keyboard shortcut using
        - `:set pastetoggle=<M-v>`
            - Here I've set the shortcut to Alt+v, which you can toggle inside
              insert mode


## Editing Command
`<number> <operator> [<motion> or <object select> <text object>]`

### Examples:
- 10j : Move down 10 lines
- y20y: Copy the next 20 lines
- diw : Delete inner word 
- daw : Delete around word (Delete the word including surrounding whitespace)
- ci" : Change everything inside the double quotes
- \>i{ : Indent everything inside {} block to the left
- yfd : Copy everything from the cursor to the first occurence of lowercase d
- dG : Delete everything from the cursor to the end of the file

### Operators
- y  : Yank (copy)
- d  : Delete
- c  : Change (Delete and enter into insert mode)
- >  : Indent right
- <  : Indent left
- gu : Change to lowercase
- gU : Chnage to uppercase
- g~ : Swap case


## Motions
- h : Left
- j : Down
- k : Up
- l : Right
- H : Highest [line] on screen
- M : Middle [line] on screen
- L : Lowest [line] on screen
- f<character> : Move to the next occurence of _character_ 
- gg : Move to beginning of file
- G  : Move to the end of file

word (seperated by characters in option `keyword`)
- w : Move forward a word
- b : Move backward a word
- e : Move forward to the end of the word
- ge : Move backward to the end of the word

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

### Object select
- a : around
    - Run command on text object (including the surrounding  whitespace/parentheses)
- i : inner.
    - Run command inside of text object.

###  Text Objects
- w : word
- t : [HTML] tag
- p : paragraph
- s : Sentence (Anything in between two '.', '?',

Also anything inside the following surrounding elements
- " "
- ' '
- ` `
(Note that the following can extend across multiple lines)
- { }
- ( )
- < >

## Other commands
- o : Insert newline after the current line
- O : Insert newline before the current line
- J : Remove newline (Joing the current line with the next line)
- C-u : Half page-up
- C-d : Half page-down
- C-b : Page-up
- C-f : Page-down

## Registers
Vim has a register for every non-modifier key (Letter, Number, or symbol)
on a typical keyboard
### Pasting

### Macros
- You can record any sequence of commands in a register using `q` and run the
  macro using `@`


## I want to ...
- Run a macro on every occurence of the pattern
    - `g/<pattern>/normal! @<register>`

## :expand("%") - Filepath

- '%' - Filepath
    - '%:h' - Filepath excluding the filename
    - '%:r' - Filepath excluding the file extension

## :help

- help can also be used for keyboard shortcuts
- :helpgrep <pattern>

- :help holy-grail

- :smile

## References
- [Vim Text Objects: The Definitve Guide](https://blog.carbonfive.com/2011/10/17/vim-text-objects-the-definitive-guide/)
