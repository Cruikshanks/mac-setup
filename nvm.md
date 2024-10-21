# NVM

**nvm** or [Node Version Manager](https://github.com/nvm-sh/nvm) is a tool that allows you to manage multiple active node.js versions.

I used to use [Homebrew](https://brew.sh/) but was informed by a colleague this is [no longer supported](https://github.com/nvm-sh/nvm#important-notes). It might also explain some issues I had running [npx](https://docs.npmjs.com/cli/v9/commands/npx).

In the same notices they recommend using the zsh plugin [zsh-nvm](https://github.com/lukechilds/zsh-nvm) to manage **nvm**. So, this is what is covered below.

## Install

Clone `zsh-nvm` into your custom plugins repo

```bash
git clone https://github.com/lukechilds/zsh-nvm ~/.oh-my-zsh/custom/plugins/zsh-nvm
```

## Configure

Add the following to the `~/.env_vars` file

```bash
# Config options for plugin https://github.com/lukechilds/zsh-nvm
# Support auto loading of correct node version based on .nvmrc files
export NVM_AUTO_USE=true
# Add additional nvm completion
export NVM_COMPLETION=true
```

The final bit is adding the plugin. But that is already covered by [ohmyzsh](/ohmyzsh.md).
