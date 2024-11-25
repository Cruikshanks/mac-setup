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

The next bit is adding the plugin. But that is already covered by [ohmyzsh](/ohmyzsh.md).

## Error: ENFILE: file table overflow

When working with Node projects on the Mac, especially the 'managed' machines, when running commands like `npm ci` I sometimes hit this error: `Error: ENFILE: file table overflow, scandir ...`.

The details after that will change depending on which repo was trying to run the `npm ci` command. But there are plenty of posts out there regards this so it seems a common issue.

Put simply, MacOS has a limit on the number of files it will allow to be open at one time. Most feel the default is set to low, especially for those who have to deal with Node.js and its `node_modules`.

The solution that worked for me is this.

```bash
echo kern.maxfiles=524288 | sudo tee -a /etc/sysctl.conf
echo kern.maxfilesperproc=524288 | sudo tee -a /etc/sysctl.conf
sudo sysctl -w kern.maxfiles=524288
sudo sysctl -w kern.maxfilesperproc=524288
ulimit -n 524288
```

> [Error: ENFILE: file table overflow, scandir while run reaction on Mac](https://stackoverflow.com/a/45004802/6117745)

The stackoverflow post uses the value `65536`, but it looked like my current setting was already `65535`. So, I took the advice of other commenters and upped the value. TBH, I haven't deep dived on this (who knows what I really did to my Mac with this!) but a number of those posts lead back to [Open files limit does not work as before in OSX Yosemite [duplicate]](https://superuser.com/a/828010), which in turn points to some more details posts.

If you are curious, happy digging!
