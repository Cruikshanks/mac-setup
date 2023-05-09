# Oh my zsh

[Oh my zsh](https://github.com/robbyrussell/oh-my-zsh) is a framework for managing your zsh configuration.

Extremely oversimplifying things here but essentially

- the **shell** is a program which processes commands and returns output
- the **terminal** is a program that runs a shell, and passes your inputs to it, and displays its output

Previously the default **shell** in OSX was [bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) but with Catalina it was changed to [zsh](https://en.wikipedia.org/wiki/Z_shell).

Again, simplifying things, **zsh** contains improvements over **bash** including automatic `cd` and spelling correction with approximate completion.

It also includes plugin and theme support and that's where **Oh my zsh** comes in. It acts as a framework for managing your **zsh** configuration, its plugins, and its themes.

The key thing for me is, when previously using bash I would manage my config manually through `~/.bash_profile`. Using zsh the config is managed through `~/.zshrc`. I still make manual adjustments to it, but a lot of what I would previously have added is now handled by plugins.

## Install

```shell
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

### Environment variables

Rather than include environment variables I need loaded directly to this file, instead I add them to `~/.env_vars` and then source that file with the following.

```bash
# Source custom env vars. By putting them in a separate file I can save my
# .zshrc to GitHub whilst protecting anything secret
source ~/.env_vars
```

I put this at the very top of the `.zshrc` file.

This isn't a dotenv file so you will need to include the `export` statement e.g. `export CHANGELOG_GITHUB_TOKEN="biglongscarynumberhashthingy"`.

### Functions

I only have one custom function so far.

```bash
# Handy function that allows me to load a .js file into the node CLI
# -i = Opens the REPL even if stdin does not appear to be a terminal
# -e = Evaluate the following argument as JavaScript
# Thanks so much to https://stackoverflow.com/a/50731756/6117745
noderepl() {
  FILE_CONTENTS="$(< $1 )"
  node -i -e "$FILE_CONTENTS"
}
```

### Aliases

Add the following aliases below the example ones

```bash
# SSH ALIASES
# Alias for setting the FRAE environment ssh keys
alias fra='. ~/.ssh/fra.sh'
# Alias for setting the WCR environment ssh keys
alias wcr='. ~/.ssh/wcr.sh'
# Alias for setting the WEX environment ssh keys
alias wex='. ~/.ssh/wex.sh'
# Alias for setting the TCM environment ssh keys
alias tcm='. ~/.ssh/tcm.sh'
# Alias for setting the PAF environment ssh keys
alias paf='. ~/.ssh/paf.sh'
# Alias for setting the WAL environment ssh keys
alias wal='. ~/.ssh/wal.sh'

# GIT ALIAS HELPERS
alias gcae='git commit --allow-empty'
# This first alias overrides the one provided in the git plugin which checks out master as the default
alias gcm='git checkout main'
# Recently switched to a project that is yet to switch to using main
alias gcmm='git checkout master'
# Use for projects that are using develop
alias gcd='git checkout develop'
alias 'g?'='alias | grep -i "git" | grep -v "alias | grep -i" | sort | less'
alias 'ga?'='alias | grep -i "git add" | sort | less'
alias 'gb?'='alias | grep -i "git branch" | sort | less'
alias 'gc?'='alias | grep -i "git commit" | sort | less'
alias 'gch?'='alias | grep -i "git checkout" | sort | less'
alias 'gp?'='alias | grep -i "git push" | sort | less'
alias 'gs?'='alias | grep -i "git status" | sort | less'
# Undo last commit - soft
alias gu='git reset --soft HEAD~1'
# Undo last commit - hard
alias guh='git reset --hard HEAD~1'
# Change commit author - handy after an npm version
alias gcca='git commit --amend --reset-author --no-edit'

# Navigate to my icloud folder
alias icloud='cd ~/Library/Mobile\ Documents/com\~apple\~CloudDocs'

# Display the tree structure including files for current folder
# https://stackoverflow.com/a/59694976/6117745
alias lst='find . | sed -e "s/[^-][^\/]*\// |/g" -e "s/|\([^ ]\)/|-\1/"'

# Temporary alias whilst I go through and rename `master` to `main` in our repos
alias m2m='git checkout master && git pull && git branch -m master main && git push -u origin main'
```

### Plugins

Add the following plugins

```bash
plugins=(git gpg-agent rbenv zsh-nvm)
```

Rather than go into them here, why they have been added and a little about what they do will is covered in the relevant pages of this guide.
