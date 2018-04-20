# Vim

In terminal editor that's very powerful but takes a little to get to gripes with.

## Install

Comes with OS X. Possibly will be an old version but so far not hit any issues.

### Plugin manager

**Vim** supports plugins, and its easier to add them via a plugin manager. I currently use [Pathogen](https://github.com/tpope/vim-pathogen). To install

```bash
mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```

## Plugins

### vim-gitgutter

[vim-gitgutter](https://github.com/airblade/vim-gitgutter) shows a git diff in the 'gutter' (sign column).

```bash
git clone https://github.com/airblade/vim-gitgutter.git ~/.vim/bundle/vim-gitgutter
```

### Command-T

[Command-T](https://github.com/wincent/command-t) provides fast file navigation for Vim.

```bash
git clone https://github.com/wincent/command-t.git ~/.vim/bundle/command-t
```

For this plugin to work you are required to compile it first before use. The key issue is that the make file and compilation must be done with the same ruby version as Vim uses. If you are using rbenv (which I do) you might end up doing it with the wrong version of ruby.

[These were the commands](https://stackoverflow.com/a/46394846/6117745) I found (tweaked) that made it work for me.

```bash
cd ~/.vim/bundle/command-t/ruby/command-t/ext/command-t
rbenv local system
ruby extconf.rb
make clean
make
```

#### Use

Enter `\t` to open the Command-T window and then simply start typing. It will match what you type against the files available, and hitting enter will open it.

### NERD Tree

[NERD Tree](https://github.com/scrooloose/nerdtree) allows you to explore your filesystem and to open files and directories. It presents the filesystem to you in the form of a tree which you manipulate with the keyboard and/or mouse. It also allows you to perform simple filesystem operations.

```bash
git clone https://github.com/scrooloose/nerdtree.git ~/.vim/bundle/nerdtree
```

### nerdtree-git-plugin

[nerdtree-git-plugin](https://github.com/Xuyuanp/nerdtree-git-plugin) is a plugin of NERDTree showing git status flags.

```bash
git clone https://github.com/Xuyuanp/nerdtree-git-plugin.git ~/.vim/bundle/nerdtree-git-plugin
```

#### Use

By default `:NERDTreeToggle` will open the file explorer for the current directory (and close it again). You can then move up and down, navigating via folders or if a file open.

However that's quite a gnarly command to enter so create a new shortcut for `fn + f2` to call it instead (see [Configure](#configure)) for details.

For reference hitting the following keys on a file selected in **NERD Tree** will do the following

- `Enter` will open the file in the current pane
- `s` will open the file in a new vertical pane
- `i` will open the file in a new horizontal pane

You can use `ctrl+ww` to cycle through the panes, including when you have just a file and **NERD Tree** open.

Finally there is [documentation](https://github.com/scrooloose/nerdtree/blob/master/doc/NERD_tree.txt) for **NERD Treet** but I found [this article](http://kennedysgarage.com/articles/nerdtree/) more useful.

### Solarized Colorscheme for Vim

[vim-colors-solarized](https://github.com/altercation/vim-colors-solarized) will use the solarized color theme in the Vim editor.

```bash
git clone https://github.com/altercation/vim-colors-solarized.git ~/.vim/bundle/vim-colors-solarized
```

Settings in the `.vimrc` will take care of the rest once this is done.

## Configure

Create the configuration file `touch ~/.vimrc` first, then add the following

```text
" Required by the plugin manager
execute pathogen#infect()

" Turn syntax highlighting on
syntax on

" Set 'soft wrap' on i.e. don't break up words when wrapping
set wrap linebreak nolist

" Set the default colorscheme to solarized dark
" https://github.com/altercation/vim-colors-solarized
set background=dark
colorscheme solarized

" Do not create any temporary files when editing
set nobackup
set nowritebackup
set noswapfile

" Configure Vim to always use spaces for tabs, and to use 2 not 4
" expandtab: Affects what happens when you press the <TAB> key.
" If 'expandtab' is set, pressing the <TAB> key will always insert
" 'softtabstop' amount of space characters
" shiftwidth: affects what happens when you press >>, << or ==
" softtabstop: affects what happens when you press the <TAB> or <BS> keys.
" Its default value is the same as the value of 'tabstop', but when using
" indentation without hard tabs or mixed indentation, you want to set it to
" the same value as 'shiftwidth'
" http://vim.wikia.com/wiki/Indenting_source_code
set expandtab
set shiftwidth=2
set softtabstop=2

" Close vim if the only window left open is a NERD Tree
autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif

" Jump to last cursor position unless it's invalid or in an event handler
autocmd BufReadPost *
  \ if line("'\"") > 0 && line("'\"") <= line("$") |
  \   exe "normal g`\"" |
  \ endif

" Shortcuts
"
" Shortcut to toggle NERD Tree
map <F2> :NERDTreeToggle<CR>

" Shortcut to toggle background (provided by solarized theme)
" https://github.com/altercation/vim-colors-solarized#toggle-background-function
call togglebg#map("<F5>")

```
