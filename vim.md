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

## Configure

Create the configuration file `touch ~/.vimrc` first, then add the following

```text
" Required by the plugin manager
execute pathogen#infect()
" Turn syntax highlighting on
syntax on
" Turn on filetype indentation detection
filetype plugin indent on
```

