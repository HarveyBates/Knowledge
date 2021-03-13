# Vim Commands
## Description
Useful commmands for vim.

## Commands
### Navigation
```bash
e # Move to end of word
w # Jump word forward
b # Jump word backward
% # Jump to corresponding bracket
} # Jump up to next space
{ # Jump down to next space
gg # Top of file
G # Bottom of file
M # Middle of screen
nG # Move to line number n
'' # Return to last position
```

### Modifying
```bash
dd # Delete line
dw # Delete word
da* # Delete around defined char (*)
di* # Delete inside defined char (*)
dG # Delete from cursor to end of file
d} # Delete from cursor to next line break
d{ # Delete from cursor to previous line break

P # Paste before cursor
p # Paste after cursor

yw # Copy word
yy # Copy line

A # Insert at end of line
I # Insert at start of line
```

### Search
```bash
?*name* # Search for item (case-sensitive)
:noh # Stop highlighting
```

### Tags
```bash
:tags # Show tag stack
:tag *name* # Go to defined tag
Ctrl-] # Jump to tag definition
:tn # Jump to next tag
:tp # Jump to previous tag
g] # See all tags for selected definition
```

### Multi-line editing 
```bash
Ctrl-v # Enter visual block mode
j or k # Move up or down to select rows
i # Enter insert mode and type cmd 
esc # Escape and rows should load
# or
Ctrl-n # Open visual multi
n # Select next item 
i # Edit or insert new text
esc # Escape visual multi-mode
```

### File explorer
```bash
Ctrl-o # Open file explorer
```



