# NVM

**nvm** or [Node Version Manager](https://github.com/creationix/nvm) is a tool that allows you to manage multiple active node.js versions.

## Install

```bash
brew install nvm
```

## Configure

Add the following to your `~/.zshrc` file before **Oh My Zsh** is sourced

```bash
# NVM plugin https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/nvm
# The following must be declared before .oh-my-zsh is sourced
# Needed to tell the oh-my-zsh nvm plugin where nvm is installed because we did
# so using homebrew
export NVM_HOMEBREW=$(brew --prefix nvm)
# Plugin will automatically load a node version when if it finds a .nvmrc file
zstyle ':omz:plugins:nvm' autoload true
```

The final bit is adding the plugin. But that is already covered by [ohmyzsh](/ohmyzsh.md).
