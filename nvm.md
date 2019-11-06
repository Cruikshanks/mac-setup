# NVM

**nvm** or [Node Version Manager](https://github.com/creationix/nvm) is a tool that allows you to manage multiple active node.js versions.

## Install

Clone this repo as a custom oh-my-zsh plugin

```bash
git clone https://github.com/lukechilds/zsh-nvm ~/.oh-my-zsh/custom/plugins/zsh-nvm
```

Just add the following to your `~/.zshrc` file

```bash
plugins=(... zsh-nvm)
```

Then add the following to `~/.bash_profile`

```text
# NVM support when installed via home brew
if [ -f "$(brew --prefix)/opt/nvm/nvm.sh" ]; then
  export NVM_DIR="$HOME/.nvm"
  . "$(brew --prefix)/opt/nvm/nvm.sh"
fi
```

## Use

After installing **nvm** get the latest version of [Node.js](https://nodejs.org/) by simply running `nvm install node --lts`. To install a specific version use `nvm install v5.1.0`.

## Why not homebrew?

In my previous setups I would have installed **nvm** via [homebrew](https://brew.sh/) and then add something like the following to my `~/.bash_profile`

```shell
export NVM_DIR="$HOME/.nvm"
  [ -s "/usr/local/opt/nvm/nvm.sh" ] && . "/usr/local/opt/nvm/nvm.sh"  # This loads nvm
  [ -s "/usr/local/opt/nvm/etc/bash_completion.d/nvm" ] && . "/usr/local/opt/nvm/etc/bash_completion.d/nvm"  # This loads nvm bash_completion
```

With the update to Catalina and the move to `zsh` and [Oh my zsh](ohmyzsh.md) the norm now seems to be to add a plugin which will handle the initialisation for you. But when I tried adding the [nvm plugin](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins/nvm) I just got a `command not found` when calling `nvm` on the command line.

Adding the `export ...` code into my `~/.zshrc` got it working, but that didn't feel right. So instead I found a number of people reference [zsh-nvm](https://github.com/lukechilds/zsh-nvm) for managing **nvm** with zsh so I've opted for that instead. It not only ensures nvm is initialised in your shell, but even the install and update of **nvm**, which is why I no longer use homewbrew to install it.
