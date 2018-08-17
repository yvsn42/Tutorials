## Key
- `<C-x>` means "`CTRL` + x"
- `<C-X>` means "`CTRL` + Shift + x"
- `<M-x>` means "`Meta` + x"
    - In Windows, the `Meta` key is the `ALT` Key
    - In OSX, you need to make the `Option/ALT` key to be the `Meta` Key in your
      terminal
        - Goto Terminal->`Preferences->`Profiles->`Keyboard
        - Select "Use Option as Meta Key"

## `cd` Tricks
- Use this command to change directories
    - Both absolute and relative paths are valid
- If cd has no arguments (Enter just `cd` on the command line) takes you back
  to your home directory
- Useful shorthands:
    - `~`: Home directory (The path stored in the $HOME variable)
    - `.`: Current directory 
    - `..`: The parent directory of the current directory
    - `-`: The directory you were previously in
        - Running `cd -` twice, will just bring you back to your current 
          directory
        - Think of this like the back button on your browser that you takes you
          the last web page you were on, but only works once. If you want to keep
          track of the directories you visit, and switch back to them, _see_
          `pushd` and `popd`

## Terminal Commandline Shortcuts
- `<C-e>`: Move to end of command line
- `<C-a>`: Move to beginning of command line
- `<C-x>`: Toggle between the beggining and end of line
- `<M-f>`: Move forward a word
- `<M-b>`: Move backward a word

- `<C-w>`: Delete word before the cursor
- `<M-d>`: Delete word after the cursor
- `<C-k>`: Delete from cursor to end of line
- `<C-u>`: Delete from start of line to cursor
- `<C-y>`: Paste text that was cut using delete shortcuts
- `<C-j>`: Same as enter

- `<C-t>`: Swap the last two characters before the cursor
- `<C-h>`: Same as Backspace

- `<TAB>`: Auto-completion
- Up/Down: Cycle through previously entered commands
    - `<C-p>`/`<C-n>`: Same as Up/Down arrow keys
- !!: Run the last command
- !`<pattern>`: Run the last command that starts with `<pattern>`
- When you run `history` you get a list of previously entered commands
    - !`<number>` : To run the command with the number shown next to it by `history`
- `<C-r>`
    - `<C-g>` : Abort search (Revert back to original line)

- `<M-x>`: Restore all changes made to the line
- `<C-c>`: Terminate running [foreground] process (SIGINT Interrupt)
- `<C-z>`: Stop running [foreground] process (SIGTSTP Interrupt)

(The above two interrupts are similar in that both stop the running process, but
do it in different ways. [Here] is a brief explanation of the difference)

[Here]:(https://askubuntu.com/questions/510811/what-is-the-difference-between-ctrl-z-and-ctrl-c-in-the-terminal)

- `<C-l>`: Clear screen
- `<C-s>`: Stop process output to the screen
    - `<C-q>`: Resume process output to the screen

- `^<pattern1>^<pattern2>` - Search for last command containing _pattern1_ and replace
  it with _pattern2_, and run the new commmand

## Bash expansions
- Example:
    - Change filename's extension:
    - Instead of: `mv /path/to/file.txt /path/to/file.xml`
    - You can : `mv /path/to/file.{txt,xml}`

## Vim mode on BASH terminal commandline
- By default BASH uses emacs' key bindings on the commandline
- If you are really a fan of vim's key bindings, and want to bring the same key
  bindings to the commandline, add the following lines to $HOME/.inputrc
  <!--TODO
  1. The lines required to use vim key bindings
  2. Sugestions for modifying prompt to show which mode (ins/cmd) you're in
  3. Create binding to toggle between emacs and vi mode -->


