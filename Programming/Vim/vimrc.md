# Vim Settings
## Descirption
Settings used in my vimrc file. 

## Update vimrc
Run this in vim (not terminal)
```vim
:so ~/.vimrc 
# or
:source ~/.vimrc
```

## Plugin manager
Choose one of these (Vundle for rpi)
### Vim-plug
https://github.com/junegunn/vim-plug
```vim
:PlugInstall # Install plugin after sourcing vimrc
```
### Vundle
https://github.com/VundleVim/Vundle.vim
```vim
:PluginInstall # After sourcing vimrc
```

## ctags
### Installation
```bash
brew install ctags
```
### Generate
In folder containing scripts run one of the following:
```bash
ctags -R . # For tags for all programs
ctags -R --exclude=node_modules . # Exclude a folder
ctags -R --exclude=.git --exclude=node_modules . # Exclude multiple folders
```
### Usage
```vim
Ctrl-] " Jump to tag definition
:tag *name* " Jump to specific tag
g] " See all tags for a single definition
```

## Vimrc
```vim
call plug#begin('~/.vim/plugged')

Plug 'https://github.com/octol/vim-cpp-enhanced-highlight'
Plug 'https://github.com/preservim/nerdtree'
Plug 'https://github.com/mg979/vim-visual-multi'
Plug 'https://github.com/itchyny/lightline.vim'
Plug 'https://github.com/MaxMEllon/vim-jsx-pretty'
Plug 'https://github.com/ycm-core/YouCompleteMe'
Plug 'xuhdev/vim-latex-live-preview', {'for': 'tex'}
Plug 'instant-markdown/vim-instant-markdown', {'for': 'markdown'}

call plug#end()

# Nerd tree setup (file browser fro vim)
map <C-o> :NERDTreeToggle<CR>
autocmd BufEnter * if tabpagenr('$') == 1 && winnr('$') == 1 && exists('b:NERDTree') && b:NERDTree.isTabTree() |
    \ quit | endif

syntax on
set tabstop=4
set showmatch
set backspace=indent,eol,start
set shiftwidth=4
set expandtab
set autoindent
set noexpandtab
set ignorecase
set smartcase
set ai
set number
set hlsearch
set ruler
highlight Comment ctermfg=lightgrey
highlight LineNr ctermfg=grey
set laststatus=2

# For livepreview of latex documents
autocmd Filetype tex setl updatetime=1
let g:livepreview_previewer = 'open -a Preview'

# For tags (ctags)
command! MakeTags !ctags -R .
set tags=./tags,tags;$HOME
set autochdir

# For livepreview of md documents
filetype plugin on
set shell=bash\ -i
```
