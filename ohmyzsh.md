# Oh my zsh

[Oh my zsh](https://github.com/robbyrussell/oh-my-zsh) is a framework for managing your zsh configuration.

Extremely oversimplifying things here but essentially

- the **shell** is a program which processes commands and returns output
- the **terminal** is a program that runs a shell, and passes your inputs to it, and displays its output

Previously the default **shell** in OSX was [bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) but with Catalina its been changed to [zsh](https://en.wikipedia.org/wiki/Z_shell).

Again, simplifying things, **zsh** contains improvements over **bash** including automatic `cd` and spelling correction with approximate completion.

It also includes plugin and theme support and that's where **Oh my zsh** comes in. It acts as a framework for managing your **zsh** configuration, its plugins, and its themes.

The key thing for me is, when previously using bash I would manage my config manually through `~/.bash_profile`. Using zsh the config is managed through `~/.zshrc`. I still make manual adjustments to it, but a lot of what I would previously have added is now handled by plugins.

## Install

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## Configure

All configuration happens in `~/.zshrc`. The first time you open it head to the bottom of the file where aliases are defined and uncomment `alias zshconfig="vim ~/.zshrc"`. You can then open it in Vim for editing any time by just calling `zshconfig` in a terminal.

### Theme

Most themes rely on [Powerline fonts](https://github.com/powerline/fonts) being installed so do that first.

```bash
# clone
git clone https://github.com/powerline/fonts.git --depth=1
# install
cd fonts
./install.sh
# clean-up a bit
cd ..
rm -rf fonts
```

The theme I'm currently running with is [Spaceship ZSH](https://github.com/denysdovhan/spaceship-prompt). To install

```bash
git clone https://github.com/denysdovhan/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt"
# Symlink spaceship.zsh-theme to your oh-my-zsh custom themes directory
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
```

Then in your `.zshrc` file set `ZSH_THEME="spaceship"`.

### Default user

This is an extra thing that was required when first trying the agnoster theme

```bash
# Needed as part of using agnoster theme. They said using below
# but didn't work so googling suggested do this instead
# DEFAULT_USER=acruikshanks prompt_context(){}
DEFAULT_USER=$(whoami)
```

It doesn't hurt to have it there, particularly as I am still playing with themes.

### Aliases

Add the following aliases below the example ones

```bash
# Alias for setting the FRAE environment ssh keys
alias fra='. ~/.ssh/fra.sh'
# Alias for setting the WCR environment ssh keys
alias wcr='. ~/.ssh/wcr.sh'
# Alias for setting the WEX environment ssh keys
alias wex='. ~/.ssh/wex.sh'

# GIT ALIAS HELPERS
alias 'g?'='alias | grep -i "git" | grep -v "alias | grep -i" | sort | less'
alias 'ga?'='alias | grep -i "git add" | sort | less'
alias 'gb?'='alias | grep -i "git branch" | sort | less'
alias 'gc?'='alias | grep -i "git commit" | sort | less'
alias 'gch?'='alias | grep -i "git checkout" | sort | less'
alias 'gp?'='alias | grep -i "git push" | sort | less'
alias 'gs?'='alias | grep -i "git status" | sort | less'

# BUNDLER ALIAS HELPER
alias 'b?'='alias | grep -i "bundle" | grep -v "bundled" | sort | less'
```

### Plugins

Add the following plugins

```bash
plugins=(
  git
  gpg-agent
  bundler
  jenv
  nvm
  rbenv
)
```

Rather than go into them here, why they have been added and a little about what they do will be covered in the relevant pages of this guide.
