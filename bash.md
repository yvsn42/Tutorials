# Key
- `<C-x>` means "`CTRL` + x"
- `<C-X>` means "`CTRL` + Shift + x"
- `<M-x>` means "`Meta` + x"
    - In Windows, the `Meta` key is the `ALT` Key
    - In OSX, you need to make the `Option/ALT` key to be the `Meta` Key in your
      terminal
        - Goto Terminal->Preferences->Profiles->Keyboard
        - Select "Use Option as Meta Key"

# Bash Commandline Shortcuts
- <C-e>: Move to end of command line
- <C-a>: Move to beginning of command line
- <C-x>: Toggle between the beggining and end of line
- <M-f>: Move forward a word
- <M-b>: Move backward a word

- <C-w>: Delete word before the cursor
- <C-k>: Delete from cursor to end of line
- <C-u>: Delete from start of line to cursor
- <C-y>: Paste text that was cut using delete shortcuts

- <TAB>: Auto-completion
- Up/Down: Cycle through previously entered commands
- !!: Run the last command
- !<pattern>: Run the last command that starts with <pattern>

- <C-c>: Terminate running [foreground] process (SIGINT Interrupt)
- <C-z>: Stop running [foreground] process (SIGTSTP Interrupt)

(The above two interrupts are similar in that both stop the running process, but
do it in different ways. [Here] is a brief explanation of the difference)

[Here]:(https://askubuntu.com/questions/510811/what-is-the-difference-between-ctrl-z-and-ctrl-c-in-the-terminal)

- <C-l>: Clear screen
- <C-s>: Stop process output to the screen
    - <C-q>: Resume process output to the screen
