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
cd ~/.vim/bundle
git clone git://github.com/airblade/vim-gitgutter.git
```

## Configure

Create the configuration file `touch ~/.vimrc` first, then add the following

```text
" Required by the plugin manager
execute pathogen#infect()
" Turn syntax highlighting on
syntax on
" Turn on line numbers
set number
" Turn on filetype indentation detection
filetype plugin indent on
```

